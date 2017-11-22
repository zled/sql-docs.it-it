---
title: Eventi estesi per SQL Server R Services | Microsoft Docs
ms.custom: SQL2016_New_Updated
ms.date: 11/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e90e057-aacb-4adc-8da6-64861f4e87df
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b4d65cd2812fea830bbdd7127b8f47569979e94
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="extended-events-for-sql-server-r-services"></a>Eventi estesi per SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fornisce un set di eventi estesi da usare per la risoluzione dei problemi correlati a [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] o ai processi R inviati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per visualizzare un elenco di eventi relativi a SQL Server, eseguire la query seguente da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
```  
select o.name as event_name, o.description  
  from sys.dm_xe_objects o  
  join sys.dm_xe_packages p  
    on o.package_guid = p.guid  
 where o.object_type = 'event'  
   and p.name = 'SQLSatellite';  
```  
  
 Tuttavia, alcuni eventi estesi per [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] vengono generati solo da processi esterni, ad esempio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], BXLServer, il processo satellite che avvia il runtime di R. Per altre informazioni sull'acquisizione di questi eventi, vedere [Collecting Events from External Processes](#bkmk_externalevents).  
  
 Per informazioni generali sull'uso di eventi estesi, vedere [SQL Server Extended Events Sessions](../../relational-databases/extended-events/sql-server-extended-events-sessions.md).  

  
##  <a name="bkmk_xeventtable"></a> Tabella degli eventi estesi  
  
|Evento|Descrizione|Utilizzare|  
|-----------|-----------------|---------|  
|connection_accept|Si verifica quando viene accettata una nuova connessione. Questo evento viene usato per registrare tutti i tentativi di connessione.||  
|failed_launching|Avvio non riuscito.|Indica un errore.|  
|satellite_abort_connection|Record di interruzione della connessione.||  
|satellite_abort_received|Generato quando viene ricevuto un messaggio di interruzione su una connessione satellite.||  
|satellite_abort_sent|Generato quando viene inviato un messaggio di interruzione su una connessione satellite.||  
|satellite_authentication_completion|Generato quando viene completata l'autenticazione per una connessione su TCP o Namedpipe.||  
|satellite_authorization_completion|Generato quando viene completata l'autorizzazione per una connessione su TCP o Namedpipe.||  
|satellite_cleanup|Generato quando il satellite chiama la pulizia.|Generato solo da processi esterni. Vedere le istruzioni sulla raccolta di eventi da processi esterni.|  
|satellite_data_chunk_sent|Generato quando la connessione satellite completa l'invio di un singolo blocco di dati.|L'evento indica il numero di righe inviate, il numero di colonne, il numero di pacchetti SNI usati e il tempo trascorso in millisecondi per l'invio del blocco. Le informazioni possono aiutare a determinare il tempo necessario per passare tipi di dati diversi e il numero di pacchetti usati.|  
|satellite_data_receive_completion|Generato quando vengono ricevuti tutti i dati richiesti da una query sulla connessione satellite.|Generato solo da processi esterni. Vedere le istruzioni sulla raccolta di eventi da processi esterni.|  
|satellite_data_send_completion|Generato quando vengono ricevuti tutti i dati richiesti per una sessione sulla connessione satellite.||  
|satellite_data_send_start|Generato quando viene avviata la trasmissione dei dati (poco prima dell'invio primo blocco di dati).||  
|satellite_error|Usato per tenere traccia degli errori del satellite di sql.||  
|satellite_invalid_sized_message|La dimensione del messaggio non è valida.||  
|satellite_message_coalesced|Usato per tenere traccia dei messaggi che si uniscono a livello di rete.||  
|satellite_message_ring_buffer_record|Record del buffer circolare del messaggio.||  
|satellite_message_summary|Informazioni di riepilogo sui messaggi.||  
|satellite_message_version_mismatch|Il campo della versione del messaggio non corrisponde.||  
|satellite_messaging|Usato per tenere traccia degli eventi di messaggistica (associazione, annullamento dell'associazione e così via).||  
|satellite_partial_message|Usato per tenere traccia dei messaggi parziali a livello di rete.||  
|satellite_schema_received|Generato quando il messaggio dello schema viene ricevuto e letto da SQL.||  
|satellite_schema_sent|Generato quando il messaggio dello schema viene inviato tramite il satellite.|Generato solo da processi esterni. Vedere le istruzioni sulla raccolta di eventi da processi esterni.|  
|satellite_service_start_posted|Generato quando avviare il servizio messaggio viene registrato nel Launchpad.|questo evento indica a Launchpad di avviare il processo esterno e contiene un ID per la nuova sessione.|  
|satellite_unexpected_message_received|Generato quando viene ricevuto un messaggio imprevisto.|Indica un errore.|  
|stack_trace|Si verifica alla richiesta di un dump di memoria del processo.|Indica un errore.|  
|trace_event|Usato a scopo di monitoraggio|Questi eventi possono contenere SQL Server, Launchpad e i messaggi di traccia dei processi esterni. Questi includono l'output in stdout e stderr da R.|  
|launchpad_launch_start|Generato quando Launchpad avvia un satellite.|Generato solo da Launchpad Vedere le istruzioni sulla raccolta di eventi da launchpad.exe.|  
|launchpad_resume_sent|Generato quando Launchpad ha avviato il satellite e inviato un messaggio di ripristino a SQL Server.|Generato solo da Launchpad Vedere le istruzioni sulla raccolta di eventi da launchpad.exe.|  
|satellite_data_chunk_sent|Generato quando la connessione satellite completa l'invio di un singolo blocco di dati.|Contiene informazioni sul numero di colonne, numero di righe, numero di pacchetti e sul tempo impiegato per l'invio del blocco.|  
|satellite_sessionId_mismatch|L'ID della sessione del messaggio non è previsto.||  
  
###  <a name="bkmk_externalevents"></a> Collecting Events from External Processes  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] avvia alcuni servizi che vengono eseguiti all'esterno del processo di SQL Server. Per acquisire gli eventi relativi a questi processi esterni, è necessario creare un file di configurazione per tracciare gli eventi e inserire il file nella stessa directory del file eseguibile per il processo.  
  
-   **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
     Per acquisire gli eventi correlati a Launchpad, inserire il file *config* nella directory Binn per l'istanza di SQL Server.  In un'installazione predefinita la directory sarà `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`.  
  
-   **BXLServer** è il processo satellite che supporta l'estendibilità di SQL con R e altri linguaggi di script.  
  
     Per acquisire gli eventi correlati a BXLServer, inserire il file *config* nella directory di installazione di R.  In un'installazione predefinita la directory sarà `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  
  
> [!IMPORTANT]
>   Il file di configurazione deve avere lo stesso nome del file eseguibile, con il formato "[nome].xeventi.xml". In altre parole, i file devono essere denominati come segue:  
>   
> - Launchpad.xevents.xml  
> - bxlserver.xevents.xml  
  
 Il file di configurazione presenta il formato seguente:  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="[session name]" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="you">Xevent for launchpad or bxl server.</description>  
    <event package="SQLSatellite" name="[XEvent Name 1]" />  
    <event package="SQLSatellite" name="[XEvent Name 2]" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="[SessionName].xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Note:**  
  
-   Per configurare la traccia, modificare il segnaposto *nome sessione*, il segnaposto per il nome del file (`[SessionName].xel`) e i nomi degli eventi da acquisire (ad esempio, `[XEvent Name 1]` o `[XEvent Name 1]`).  
  
-   Verrà raccolto qualsiasi numero di tag `event package` visualizzati, a condizione che l'attributo del nome sia corretto.  
  
### <a name="example-capturing-launchpad-events"></a>Esempio: Acquisizione degli eventi Launchpad  
 L'esempio seguente illustra la definizione di una traccia di eventi per il servizio Launchpad.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="launchpad_launch_start" />  
    <event package="SQLSatellite" name="launchpad_resume_sent" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="launchpad_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Note:**  
  
-   Inserire il file *config* nella directory Binn per l'istanza di SQL Server.  
  
-   Questo file deve essere denominato *Launchpad.xevents.xml*.  
  
### <a name="example-capturing-bxlserver-events"></a>Esempio: Acquisizione degli eventi BXLServer  
 L'esempio seguente illustra la definizione di una traccia di eventi per l'eseguibile di BXLServer.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
 <event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="satellite_abort_received" />  
    <event package="SQLSatellite" name="satellite_authentication_completion" />  
    <event package="SQLSatellite" name="satellite_cleanup" />  
    <event package="SQLSatellite" name="satellite_data_receive_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_start" />  
    <event package="SQLSatellite" name="satellite_schema_sent" />   
    <event package="SQLSatellite" name="satellite_unexpected_message_received" />    
    <event package="SQLSatellite" name="satellite_data_chunk_sent" />   
    <target package="package0" name="event_file">  
      <parameter name="filename" value="satellite_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Note:**  
  
-   Inserire il file *config* nella stessa directory dell'eseguibile di BXLServer.  
  
-   Questo file deve essere denominato *bxlserver.xevents.xml*.  
  
## <a name="see-also"></a>Vedere anche
[Custom Management Studio Reports for R Services](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md) (Report personalizzati di Management Studio per R Services)  
 [Servizi R per SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Gestione e monitoraggio di soluzioni R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
  
  
