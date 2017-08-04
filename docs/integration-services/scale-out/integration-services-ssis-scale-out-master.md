---
title: "SQL Server Integration Services (SSIS) scalabilità Master | Documenti Microsoft"
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1672c015186998065b5d6dc95897147aa11d14ec
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-scale-out-master"></a>Master di scalabilità orizzontale di Integration Services (SSIS)
Il master di scalabilità orizzontale gestisce il sistema di scalabilità orizzontale tramite il catalogo SSISDB e il servizio Master di scalabilità orizzontale. 

Il catalogo SSISDB archivia tutte le informazioni relative ai ruoli di lavoro di scalabilità orizzontale, ai pacchetti e alle esecuzioni. Fornisce l'interfaccia per abilitare un ruolo di lavoro di scalabilità orizzontale ed eseguire pacchetti nel servizio di scalabilità orizzontale. Per altre informazioni, vedere [Procedura dettagliata: Installare il servizio di scalabilità orizzontale di Integration Services](walkthrough-set-up-integration-services-scale-out.md), [Eseguire pacchetti nel servizio di scalabilità orizzontale di Integration Services (SSIS)](run-packages-in-integration-services-ssis-scale-out.md).

Master di scalabilità orizzontale è un servizio Windows responsabile della comunicazione con ruoli di lavoro di scalabilità orizzontale. Scambia lo stato delle esecuzioni del pacchetto con i ruoli di lavoro di scalabilità orizzontale tramite HTTPS e agisce sui dati in SSISDB. 

## <a name="scale-out-related-sql-views-and-stored-procedures-in-ssisdb"></a>Orizzontale relative viste SQL e stored procedure nel database SSISDB

#### <a name="views"></a>Viste:
[[catalog].[master_properties]](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md), [[catalog].[worker_agents]](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md).

#### <a name="stored-procedures"></a>Stored procedure:

- Per la gestione del ruolo di lavoro di scalabilità orizzontale:  
 [[catalog].[disable_worker_agent]](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md), [[catalog].[enable_worker_agent]](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md).
- Per l'esecuzione di pacchetti nel servizio di scalabilità orizzontale:   
[[catalog].[create_execution]](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md), [[catalog].[add_execution_worker]](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md), [[catalog].[start_execution]](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).   

## <a name="configure-sql-server-integration-services-scale-out-master-service"></a>Configurare il servizio Master di scalabilità orizzontale di SQL Server Integration Services
Il servizio Master di scalabilità orizzontale può essere configurato usando l' \<unità\>: \Programmi\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config file. Il servizio deve essere riavviato dopo l'aggiornamento del file di configurazione.


Configurazione  |Descrizione  |Valore predefinito  
---------|---------|---------
PortNumber|Numero di porta di rete usato per comunicare con un ruolo di lavoro di scalabilità orizzontale.|8391         
SSLCertThumbprint|Identificazione personale del certificato SSL usato per proteggere la comunicazione con un ruolo di lavoro di scalabilità orizzontale.|Identificazione personale del certificato SSL specificato durante l'installazione del master di scalabilità orizzontale.         
SqlServerName|Il nome del [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] che contiene il catalogo SSISDB. Ad esempio, ServerName\\\\NomeIstanza.|Il nome del Server SQL che viene installato con la scala Out Master.         
CleanupCompletedJobsIntervalInMs|Intervallo per l'eliminazione dei processi di esecuzione completati, espresso in millisecondi.|43200000         
DealWithExpiredTasksIntervalInMs|Intervallo per la gestione dei processi di esecuzione scaduti, espresso in millisecondi.|300000
MasterHeartbeatIntervalInMs|Intervallo per l'heartbeat del master di scalabilità orizzontale, espresso in millisecondi. Specifica l'intervallo necessario al master di scalabilità orizzontale per l'aggiornamento del proprio stato in linea nel catalogo SSISDB.|30000
SqlConnectionTimeoutInSecs|Il timeout di connessione SQL in secondi per la connessione al database SSISDB.|15        

## <a name="view-scale-out-master-service-log"></a>Visualizzare il log del servizio Master di scalabilità orizzontale
Il file di log di servizio scala Out Master si trova nel \<driver\>: \Users\\*[account]*\AppData\Local\SSIS\ScaleOut\Master percorso della cartella. 

Il *[account]* fa riferimento all'account del servizio scala Out Master. Per impostazione predefinita, l'account è SSISScaleOutMaster140.

