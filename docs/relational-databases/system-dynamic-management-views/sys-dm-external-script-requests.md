---
title: sys.dm_external_script_requests | Microsoft Docs
ms.custom: ''
ms.date: 06/24/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_requests
- sys.dm_external_script_requests_TSQL
- dm_external_script_requests
- dm_external_script_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_requests dynamic management view
ms.assetid: e7e7c50f-b8b2-403c-b8c8-1955da5636c3
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bc6db4816e4ba890e132600874d5db21aa190c02
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmexternalscriptrequests"></a>sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Restituisce una riga per ogni account di lavoro attivo che esegue uno script esterno.
 
  
> [!NOTE] 
>  
>  Questa DMV è disponibile solo se è stata installata e quindi abilitata la funzionalità che supporta l'esecuzione di script esterni. Per informazioni su come eseguire questa operazione per gli script R, vedere [Configurare SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**Identificatore univoco**|ID del processo che ha inviato la richiesta di script esterni. Questo corrisponde all'ID di processo così come viene ricevuto da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|language|**nvarchar**|Parola chiave che rappresenta un linguaggio di scripting supportato. Attualmente è supportato solo `R` .|  
|degree_of_parallelism|**int**|Numero che indica il numero di processi paralleli che sono stati creati. Questo valore potrebbe essere diverso dal numero di processi paralleli che sono stati richiesti.|  
|external_user_name|**nvarchar**|Account di lavoro di Windows con cui è stato eseguito lo script.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE nel server.  
  
> [!NOTE]
>   
>  Gli utenti che eseguono script esterni devono avere l'autorizzazione aggiuntiva EXECUTE ANY EXTERNAL SCRIPT, tuttavia, questa DMV può essere usata dagli amministratori senza tale autorizzazione. 
  
## <a name="remarks"></a>Osservazioni  

Questa vista può essere filtrata usando l'identificatore del linguaggio di scripting.

La vista restituisce anche l'account di lavoro con cui viene eseguito lo script. Per informazioni sugli account di lavoro usati dagli script R, vedere [Modificare il pool di account utente per SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).

Il GUID restituito nel campo **external_script_request_id** rappresenta anche il nome file della directory protetta in cui vengono archiviati i file temporanei. Ogni account di lavoro come MSSQLSERVER01 rappresenta un singolo account di accesso SQL o un utente di Windows e potrebbe essere usato per eseguire più richieste di script. Per impostazione predefinita, la pulizia di questi file temporanei viene eseguita dopo il completamento dello script richiesto. Se è necessario conservare questi file per un determinato periodo di tempo a scopo di debug, è possibile modificare il flag di pulizia, come descritto in questo argomento: [Configurare e gestire Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md).  
 
Questa DMV monitora solo i processi attivi e non può segnalare gli script che sono già stati completati. Se è necessario tenere traccia della durata degli script, è consigliabile aggiungere le informazioni sulla misurazione del tempo nello script e acquisire tali informazioni come parte dell'esecuzione dello script.


## <a name="examples"></a>Esempi  
  
### <a name="viewing-the-currently-active-r-scripts-for-a-particular-process"></a>Visualizzazione degli script R attualmente attivi per un determinato processo 
 L'esempio seguente visualizza il numero di esecuzioni dello script esterno completate nell'istanza corrente.  
  
```  
SELECT external_script_request_id 
  , [language]
  , degree_of_parallelism
  , external_user_name
FROM sys.dm_external_script_requests; 
```  

Risultati  


external_script_request_id  |language  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     L    |      1   |  MSSQLSERVER01       


  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

