---
title: catalog.execution_data_statistics | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 6f51407e-0e4e-4b44-af33-db14c9d40ded
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a5463b9da862b8ebeb3f9f769da7a22dde6867b6
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="catalogexecutiondatastatistics"></a>catalog.execution_data_statistics
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Nella vista viene visualizzata una riga ogni volta che un componente flusso di dati invia dati a un componente a valle, per l'esecuzione di un determinato pacchetto. Le informazioni contenute in questa vista possono essere utilizzate per calcolare la velocità effettiva dei dati per un componente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|data_stats_id|**bigint**|Identificatore univoco (ID) dei dati.|  
|execution_id|**bigint**|ID univoco per l'istanza di esecuzione.|  
|package_name|**nvarchar(260)**|Nome del primo pacchetto avviato durante l'esecuzione.|  
|task_name|**nvarchar(4000)**|Nome dell'attività del flusso di dati.|  
|dataflow_path_id_string|**nvarchar(4000)**|Stringa di identificazione del percorso del flusso di dati.|  
|dataflow_path_name|**nvarchar(4000)**|Nome del percorso del flusso di dati.|  
|source_component_name|**nvarchar(4000)**|Nome del componente flusso di dati che invia i dati.|  
|destination_component_name|**nvarchar(4000)**|Nome del componente flusso di dati che riceve i dati.|  
|rows_sent|**bigint**|Numero di righe inviate dal componente di origine.|  
|created_time|**datatimeoffset(7)**|Ora in cui vengono ottenuti i valori.|  
|execution_path|**nvarchar(max)**|Percorso di esecuzione del componente.|  
  
## <a name="remarks"></a>Remarks  
  
-   In presenza di più output dal componente, viene aggiunta una riga per ogni output.  
  
-   Per impostazione predefinita, quando viene avviata un'esecuzione, le informazioni sul numero di righe inviate non vengono registrate.  
  
-   Per visualizzare i dati per l'esecuzione di un determinato pacchetto, impostare il livello di registrazione su **Verbose**. Per altre informazioni, vedere [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'istanza di esecuzione  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
> [!NOTE]  
>  Quando si dispone delle autorizzazioni per eseguire un'operazione nel server, si dispone anche delle autorizzazioni per visualizzare le informazioni sull'operazione. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
