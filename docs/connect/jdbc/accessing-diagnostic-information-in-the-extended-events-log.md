---
title: L'accesso a informazioni di diagnostica nel Log degli eventi estesi | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79e9468-2257-4536-91f1-73b008c376c3
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e6dfbd857905f0c0f444c44a9c9eb9813cc32ab2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Accesso alle informazioni di diagnostica nel registro eventi estesi
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Nel [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], la funzionalità di traccia ([operazione Driver traccia](../../connect/jdbc/tracing-driver-operation.md)) è stata aggiornata per semplificare per correlare gli eventi client con le informazioni di diagnostica, ad esempio gli errori di connessione da circolare di connettività del server informazioni sulle prestazioni del buffer e l'applicazione nel log degli eventi estesi. Per informazioni sulla lettura del log di eventi estesi, vedere [visualizzare i dati di sessione eventi](http://msdn.microsoft.com/library/hh710068(SQL.110).aspx).  
  
## <a name="details"></a>Dettagli  
 Per le operazioni di connessione, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] invierà un client ID connessione. Se la connessione non riesce, è possibile accedere al buffer circolare ([la risoluzione dei problemi di connettività in SQL Server 2008 con il Buffer circolare di connettività](http://go.microsoft.com/fwlink/?LinkId=207752)) e individuare il **ClientConnectionID** campo e ottenere informazioni diagnostiche sull'errore di connessione. Gli ID di connessione client vengono registrati nel buffer circolare solo se si verifica un errore. In caso di errore di connessione prima dell'invio del pacchetto di preaccesso, l'ID di connessione client non verrà generato. L'ID di connessione client è un GUID a 16 byte. È anche possibile trovare la connessione client ID nell'output di destinazione di eventi estesi, se il **client_connection_id** azione viene aggiunta agli eventi in una sessione eventi estesi. È possibile abilitare la traccia e rieseguire il comando di connessione e osservare il **ClientConnectionID** campo nella traccia, se è necessaria ulteriore supporto diagnostico del driver client.  
  
 È possibile ottenere il client ID di connessione a livello di programmazione utilizzando [ISQLServerConnection, interfaccia](../../connect/jdbc/reference/isqlserverconnection-interface.md). L'ID connessione sarà inoltre disponibile in tutte le eccezioni correlate alla connessione.  
  
 Quando si verifica un errore di connessione, con l'ID connessione client nelle informazioni relative alla traccia BID del server e nel buffer circolare è possibile semplificare la correlazione delle connessioni client alle connessioni nel server. Per ulteriori informazioni sulle tracce BID nel server, vedere [traccia di accesso ai dati](http://go.microsoft.com/fwlink/?LinkId=125805). Si noti che nell'articolo di traccia di accesso ai dati contiene inoltre informazioni sull'esecuzione di una traccia di accesso ai dati, non è valida per il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]; vedere [operazione Driver traccia](../../connect/jdbc/tracing-driver-operation.md) per informazioni sull'esecuzione di una traccia di accesso ai dati utilizzando la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Il driver JDBC invia anche un ID attività specifico del thread. L'ID attività viene acquisito nelle sessioni di eventi estesi se avviate con l'opzione TRACK_CAUSAILITY abilitata. Per problemi di prestazioni con una connessione attiva, è possibile ottenere l'ID attività dalla traccia del client (campo ActivityID) e quindi individuare l'ID attività nell'output degli eventi estesi. L'ID attività negli eventi estesi è un GUID a 16 byte, non lo stesso del GUID per l'ID connessione client, aggiunto con un numero di sequenza a quattro byte. Il numero di sequenza rappresenta l'ordine di una richiesta all'interno di un thread. ActivityId viene inviato per le istruzioni batch SQL e per le richieste RPC. Per abilitare l'invio di ActivityId al server, è innanzitutto necessario specificare la seguente coppia chiave-valore nel file Logging.Properties:  
  
```  
com.microsoft.sqlserver.jdbc.traceactivity = on  
```  
  
 Qualsiasi valore diverso da `on` (maiuscole/minuscole) disabiliterà l'invio di ActivityId.  
  
 Per ulteriori informazioni, vedere [traccia operazione Driver](../../connect/jdbc/tracing-driver-operation.md). Questo flag di traccia viene utilizzato con i logger degli oggetti JDBC corrispondenti per stabilire se tracciare e inviare ActivityId nel driver JDBC. Oltre ad aggiornare il file Logging.Properties, è necessario abilitare il logger com.microsoft.sqlserver.jdbc al livello FINER o superiore. Se si desidera inviare ActivityId al server per le richieste effettuate da una classe specifica, è necessario abilitare il logger della classe corrispondente al livello FINER o FINEST. Se ad esempio la classe è SQLServerStatement, abilitare il logger com.microsoft.sqlserver.jdbc.SQLServerStatement.  
  
 Di seguito è riportato un esempio che utilizza [!INCLUDE[tsql](../../includes/tsql_md.md)] per avviare una sessione eventi estesi che verrà archiviata in un buffer circolare e che registrerà l'ID attività inviato da un client nelle operazioni batch e RPC:  
  
```  
create event session MySession on server  
add event connectivity_ring_buffer_recorded,  
add event sql_statement_starting (action (client_connection_id)),  
add event sql_statement_completed (action (client_connection_id)),  
add event rpc_starting (action (client_connection_id)),  
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [La diagnosi di problemi con il Driver JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  

