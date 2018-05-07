---
title: L'accesso a informazioni di diagnostica nel Log degli eventi estesi | Documenti Microsoft
description: La traccia di Driver OLE DB per SQL Server e l'accesso alle informazioni di diagnostica nel log degli eventi estesi
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 255daa268cb3b8aeaee0e371052ae8af01241f72
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Accesso alle informazioni di diagnostica nel registro eventi estesi
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  A partire da [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], il Driver OLE DB per la traccia di accesso di SQL Server e i dati ([traccia di accesso ai dati](http://go.microsoft.com/fwlink/?LinkId=125805)) sono stati aggiornati per rendere più semplice ottenere informazioni di diagnostica sugli errori di connessione dal buffer circolare di connettività e informazioni sulle prestazioni dell'applicazione dal log degli eventi estesi.  
  
 Per informazioni sulla lettura del log di eventi estesi, vedere [visualizzare i dati di sessione eventi](../../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md). 

  
> [!NOTE]  
>  Questa funzionalità è destinata esclusivamente alla risoluzione dei problemi e a fini diagnostici e potrebbe non essere appropriata per il controllo o per scopi di sicurezza.  
  
## <a name="remarks"></a>Osservazioni  
 Per le operazioni di connessione, il Driver OLE DB per SQL Server invierà un client ID connessione. Se la connessione non riesce, è possibile accedere al buffer circolare ([la risoluzione dei problemi di connettività in SQL Server 2008 con il Buffer circolare di connettività](http://go.microsoft.com/fwlink/?LinkId=207752)) e individuare il **ClientConnectionID** campo e ottenere informazioni diagnostiche sull'errore di connessione. Gli ID di connessione client vengono registrati nel buffer circolare solo se si verifica un errore. In caso di errore di connessione prima dell'invio del pacchetto di preaccesso, l'ID di connessione client non verrà generato. L'ID di connessione client è un GUID a 16 byte. È anche possibile trovare il client ID di connessione negli eventi estesi di output di destinazione, se il **client_connection_id** azione viene aggiunta agli eventi in una sessione eventi estesi. È possibile abilitare la traccia di accesso ai dati e rieseguire il comando di connessione e osservare il **ClientConnectionID** campo nella traccia di accesso ai dati per un'operazione non riuscita, se necessaria ulteriore assistenza diagnostica.  
   
  
 Il Driver OLE DB per SQL Server invia anche un ID attività specifico del thread. L'ID attività viene acquisito nelle sessioni di eventi estesi se avviate con l'opzione TRACK_CAUSAILITY abilitata. Per problemi di prestazioni con una connessione attiva, è possibile ottenere l'ID attività dalla traccia di accesso ai dati del client (**ActivityID** campo) e quindi individuare l'ID attività nell'output degli eventi estesi. L'ID attività negli eventi estesi è un GUID a 16 byte (diverso dal GUID per l'ID di connessione client) accodato con un numero di sequenza a quattro byte. Il numero di sequenza rappresenta l'ordine di una richiesta all'interno di un thread e indica l'ordine relativo di istruzioni batch e RPC per il thread. Il **ActivityID** viene inviato facoltativamente per istruzioni batch SQL e le richieste RPC quando è abilitata la traccia di accesso ai dati e il bit 18 word di configurazione di traccia di accesso ai dati è attivato.  
  
 Di seguito è riportato un esempio di utilizzo di [!INCLUDE[tsql](../../../includes/tsql-md.md)] per avviare una sessione di eventi estesi che verrà archiviata in un buffer circolare e verrà registrato l'ID attività inviato da un client in operazioni RPC e batch.  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
  
```  
  
## <a name="control-file"></a>File di controllo  
 Il contenuto del Driver OLE DB per il file di controllo di SQL Server (ctrl.guid) è:  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x630ff  0   MSDADIAG.ETW
{EE7FB59C-D3E8-9684-AEAC-B214EFD91B31}  0x630ff  0   MSOLEDBSQL.1  
```  
  
## <a name="mof-file"></a>File MOF  
 Il contenuto del Driver OLE DB per il file mof di SQL Server è:  
  
```  
#pragma classflags("forceupdate")  
#pragma namespace ("\\\\.\\Root\\WMI")  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSDADIAG.ETW  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F3-3CC6-0B9C-6651-9649CCE5C752}"),  
 DisplayName("msdadiag"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace : Bid2Etw_MSDADIAG_ETW  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextA : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextW : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSOLEDBSQL.1  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1"),  
 Guid("{EE7FB59C-D3E8-9684-AEAC-B214EFD91B31}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1"),  
 Guid("{EE7FB59D-D3E8-9684-AEAC-B214EFD91B31}"),  
 DisplayName("MSOLEDBSQL.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace : Bid2Etw_MSOLEDBSQL_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace_TextA : Bid2Etw_MSOLEDBSQL_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace_TextW : Bid2Etw_MSOLEDBSQL_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione degli errori](../../oledb/ole-db-errors/errors.md)  
  
  
