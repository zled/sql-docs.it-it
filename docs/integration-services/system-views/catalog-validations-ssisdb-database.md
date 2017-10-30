---
title: Catalog. validations (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: dbafe110-b480-48f3-b45f-31d71ca68f62
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2d799fd23c2adef75e3dcf4543e9e0ee6271c9b5
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogvalidations-ssisdb-database"></a>catalog.validations (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i dettagli di tutte le convalide del progetto e del pacchetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|validation_id|**bigint**|Identificatore (ID) univoco della convalida.|  
|environment_scope|**Char (1)**|Vengono indicati i riferimenti all'ambiente considerati dalla convalida. Quando il valore è `A`, tutti i riferimenti all'ambiente associati al progetto sono inclusi nella convalida. Quando il valore è `S`, è incluso solo un singolo riferimento all'ambiente. Quando il valore è `D`, non è incluso alcun riferimento all'ambiente e ogni parametro deve disporre di un valore predefinito letterale per passare la convalida.|  
|validate_type|**Char (1)**|Tipo di convalida da eseguire. I tipi di convalida possibili sono la convalida della dipendenza (`D`) o la convalida completa (`F`). La convalida del pacchetto è sempre quella completa.|  
|nome_cartella|**nvarchar (128)**|Nome della cartella in cui è contenuto il progetto corrispondente.|  
|PROJECT_NAME|**nvarchar (128)**|Nome del progetto.|  
|project_lsn|**bigint**|Versione del progetto rispetto a cui è stata eseguita la convalida.|  
|use32bitruntime|**bit**|Viene indicato se il runtime a 32 bit viene utilizzato per eseguire il pacchetto in un sistema operativo a 64 bit. Quando il valore è `1`, l'esecuzione viene eseguita con il runtime a 32 bit. Quando il valore è `0`, l'esecuzione viene eseguita con il runtime a 64 bit.|  
|reference_id|**bigint**|ID univoco del riferimento all'ambiente del progetto utilizzato dal progetto per fare riferimento a un ambiente.|  
|operation_type|**smallint**|Tipo di operazione. Nelle operazioni visualizzate in questa vista sono incluse la convalida del progetto (`300`) e la convalida del pacchetto (`301`).|  
|object_name|**nvarhcar(260)**|Nome dell'oggetto .|  
|object_type|**smallint**|Tipo di oggetto. Può trattarsi di un progetto (`20`) o di un pacchetto (`30`).|  
|object_id|**bigint**|ID dell'oggetto interessato dall'operazione.|  
|start_time|**DateTimeOffset(7)**|Ora di inizio dell'operazione.|  
|end_time|**datetimeoffsset(7)**|Ora di fine dell'operazione.|  
|status|**int**|Stato dell'operazione. I valori possibili sono Creata (`1`), In esecuzione (`2`), Operazione annullata (`3`) Operazione non riuscita (`4`), In sospeso (`5`), Terminata in modo inatteso (`6`), Operazione riuscita (`7`), Arresto in corso (`8`) Operazione completata (`9`).|  
|caller_sid|**varbinary (85)**|ID di sicurezza (SID) dell'utente se per l'accesso è stata utilizzata l'autenticazione di Windows.|  
|caller_name|**nvarchar (128)**|Nome dell'account tramite cui è stata eseguita l'operazione.|  
|process_id|**int**|ID processo del programma esterno, se applicabile.|  
|stopped_by_sid|**varbinary (85)**|SID dell'utente che ha arrestato l'operazione.|  
|stopped_by_name|**nvarchar (128)**|Nome dell'utente che ha arrestato l'operazione.|  
|server_name|**nvarchar (128)**|Informazioni relative al server Windows e all'istanza per un'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|machine_name|**nvarchar (128)**|Nome del computer in cui è in esecuzione l'istanza del server.|  
|dump_id|**uniqueidentifier**|ID del dump di esecuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni convalida nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'operazione corrispondente  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
> [!NOTE]  
>  Quando si dispone delle autorizzazioni per eseguire un'operazione nel server, si dispone anche delle autorizzazioni per visualizzare le informazioni sull'operazione. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  

