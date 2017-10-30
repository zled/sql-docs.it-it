---
title: "SQL Server Integration Services (SSIS) scalabilità lavoro | Documenti Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 77cf90268938bada458aa159a5f18f885491b407
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-scale-out-worker"></a>Ruolo di lavoro di scalabilità orizzontale di Integration Services (SSIS)

Scala il lavoro viene eseguito un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] servizio scala il lavoro per l'esecuzione pull attività dalla scala Out Master ed esegue i pacchetti in locale con ISServerExec.exe.

## <a name="configure-sql-server-integration-services-scale-out-worker-service"></a>Configurare il servizio Ruolo di lavoro di scalabilità orizzontale di SQL Server Integration Services
Il servizio Ruolo di lavoro di scalabilità orizzontale può essere configurato usando l' \<unità\>: \Programmi\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config file. Il servizio deve essere riavviato dopo l'aggiornamento del file di configurazione.

Configurazione  |Description  |Valore predefinito  
---------|---------|---------
DisplayName|Nome visualizzato del ruolo di lavoro di scalabilità orizzontale. **NON è in uso in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017.**|Nome computer         
Description|Descrizione del ruolo di lavoro di scalabilità orizzontale. **NON è in uso in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017.**|Vuoto         
MasterEndpoint|Endpoint per la connessione al master di scalabilità orizzontale.|Endpoint impostato durante l'installazione del ruolo di lavoro di scalabilità orizzontale         
MasterHttpsCertThumbprint|Identificazione personale del certificato SSL del client usato per autenticare il master di scalabilità orizzontale|Identificazione personale del certificato client specificato durante l'installazione del ruolo di lavoro di scalabilità orizzontale.          
WorkerHttpsCertThumbprint|Identificazione personale del certificato del master di scalabilità orizzontale usato per autenticare il ruolo di lavoro di scalabilità orizzontale.|Identificazione personale di un certificato creato e installato automaticamente durante l'installazione del ruolo di lavoro di scalabilità orizzontale          
StoreLocation|Percorso dell'archivio del certificato del ruolo di lavoro.|LocalMachine       
StoreName|Nome dell'archivio del certificato del ruolo di lavoro.|My         
AgentHeartbeatInterval|Intervallo di heartbeat del ruolo di lavoro di scalabilità orizzontale.|00:01:00         
TaskHeartbeatInterval|Intervallo del ruolo di lavoro di scalabilità orizzontale indicante lo stato dell'attività.|00:00:10         
HeartbeatErrorTollerance|Dopo il periodo di tempo definito dall'ultimo heartbeat dell'attività, quest'ultima viene terminata se si riceve un errore di heartbeat.|00:10:00      
TaskRequestMaxCPU|Limite massimo di CPU per il ruolo di lavoro di scalabilità orizzontale per richiedere attività. **NON è in uso in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017.**|70.0         
TaskRequestMinMemory|Limite massimo di memoria espressa in MB per il ruolo di lavoro di scalabilità orizzontale per richiedere attività. **NON è in uso in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017.**|100.0         
MaxTaskCount|Numero massimo di attività che il ruolo di lavoro di scalabilità orizzontale può gestire.|10         
LeaseInternval|Intervallo di lease di un'attività gestito dal ruolo di lavoro di scalabilità orizzontale.|00:01:00         
TasksRootFolder|Cartella dei log delle attività. Se il valore è vuoto, viene usato il percorso della cartella dell' \<unità\>:\Users\\*[account]*\AppData\Local\SSIS\Cluster\Tasks. [account] è l'account che esegue il servizio Ruolo di lavoro di scalabilità orizzontale. Per impostazione predefinita, l'account è SSISScaleOutWorker140.|Vuoto         
TaskLogLevel|Livello di log dell'attività del ruolo di lavoro di scalabilità orizzontale. (Verbose 0x01, Information 0x02, Warning 0x04, Error 0x08, Progress 0x10, CriticalError 0x20, Audit 0x40)|126 (Information,Warning,Error,Progress,CriticalError,Audit)     
TaskLogSegment|Intervallo di tempo di un file di log dell'attività.|00:00:00         
TaskLogEnabled|Specifica se il log dell'attività è abilitato.|true         
ExecutionLogCacheFolder|Cartella usata per memorizzare nella cache il log di esecuzione del pacchetto. Se il valore è vuoto, viene usato il percorso della cartella dell' \<unità\>:\Users\\*[account]*\AppData\Local\SSIS\Cluster\Agent\ELogCache. [account] è l'account che esegue il servizio Ruolo di lavoro di scalabilità orizzontale. Per impostazione predefinita, l'account è SSISScaleOutWorker140.|Vuoto         
ExecutionLogMaxBufferLogCount|Numero massimo di log di esecuzione memorizzati nella cache, un buffer del log di esecuzione in memoria.|10000        
ExecutionLogMaxInMemoryBufferCount|Numero massimo di buffer del log di esecuzione in memoria per i log di esecuzione.|10         
ExecutionLogRetryCount|Numero di tentativi se si verifica un errore del log di esecuzione.|3
ExecutionLogRetryTimeout|Il timeout dei tentativi in caso di registrazione per l'esecuzione. Se viene raggiunto ExecutionLogRetryTimeout, ExecutionLogRetryCount viene ignorato.|7.00:00:00 (7 giorni)        
AgentId|Id dell'agente di lavoro del ruolo di lavoro di scalabilità orizzontale|Generato automaticamente        

## <a name="view-scale-out-worker-log"></a>Visualizzare il log del ruolo di lavoro di scalabilità orizzontale
Il file di registro del servizio di scala il lavoro è nel \<driver\>: \Users\\*[account]*\AppData\Local\SSIS\ScaleOut\Agent percorso della cartella.

Il percorso del log di ogni attività viene configurato nel file WorkerSettings.config da TasksRootFolder. Se non è specificato, il log è nel \<driver\>: \Users\\*[account]*\AppData\Local\SSIS\ScaleOut\Tasks percorso della cartella. 

Il *[account]* è l'account che esegue servizio scala Out Worker. Per impostazione predefinita, l'account è SSISScaleOutWorker140.

