---
title: sys.dm_external_script_execution_stats | Microsoft Docs
ms.custom: 
ms.date: 09/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_execution_stats
- sys.dm_external_script_execution_stats_TSQL
- dm_external_script_execution_stats
- dm_external_script_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_execution_stats dynamic management view
ms.assetid: 2e99f026-ceb2-42a2-a549-c71d31ed0cf4
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8306c682ddf8e376e13629cc6fe13472e08f59b0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexternalscriptexecutionstats"></a>sys.dm_external_script_execution_stats
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


  Restituisce una riga per ogni tipo di richiesta di script esterni. Le richieste di script esterni vengono raggruppate per il linguaggio di script esterno supportato. Viene generata una riga per ogni funzione di script esterni registrata. Le funzioni di script esterni arbitrarie non vengono registrate a meno che non siano inviate da un processo padre, ad esempio `rxExec`.

 
  
> [!NOTE]  
>  Questa DMV è disponibile solo se è stata installata e quindi abilitata la funzionalità che supporta l'esecuzione di script esterni. Per informazioni su come eseguire questa operazione per gli script R, vedere [Configurare SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|language|**nvarchar**|Nome del linguaggio di script esterni registrato. Ogni script esterno deve specificare il linguaggio della richiesta di script per usare l'utilità di avvio associata. |  
|counter_name|**nvarchar**|Nome di una funzione di script esterni registrata. Non ammette i valori Null.|  
|counter_value|**integer**|Numero totale di istanze chiamate dalla funzione di script esterni registrata nel server. Questo valore è cumulativo, parte dall'ora di installazione della funzionalità nell'istanza e non può essere reimpostato.|  

  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE nel server.  
  
> [!NOTE]  
>  Gli utenti che eseguono script esterni devono avere l'autorizzazione aggiuntiva EXECUTE ANY EXTERNAL SCRIPT, tuttavia, questa DMV può essere usata dagli amministratori senza tale autorizzazione. 
  
## <a name="remarks"></a>Osservazioni  
  Questa DMV viene fornita per la telemetria interna, per monitorare l'utilizzo complessivo della nuova funzionalità di esecuzione di script esterni disponibile in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Il servizio di telemetria viene avviato insieme al LaunchPad e viene incrementato di un contatore basato su disco ogni volta che viene chiamata una funzione di script esterni registrata.

In generale, i contatori delle prestazioni sono validi solo se il processo che li ha generati è attivo. Quindi, una query su una DMV non può visualizzare i dati dettagliati per i servizi che non sono in esecuzione. Ad esempio, se un'utilità di avvio esegue script esterni e li completa molto rapidamente, una DMV convenzionale potrebbe non visualizzare alcun dato

Di conseguenza, i contatori rilevati da questa DMV restano in esecuzione e lo stato di sys.dm_external_script_requests viene mantenuto usando le scritture su disco, anche se l'istanza è arrestata.

   
  
### <a name="r-counter-values"></a>Valori del contatore R
 Attualmente l'unico linguaggio di script esterni supportato in [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)] è R. Le richieste di script esterni per il linguaggio R vengono gestite da [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. 

Per R, questa DMV tiene traccia del numero di chiamate di R che vengono apportate in un'istanza. Ad esempio, se `rxLinMod` viene chiamato ed eseguito in parallelo, il contatore viene incrementato di 1.
 
Per il linguaggio R, i valori del contatore visualizzati nel campo *counter_name* rappresentano i nomi delle funzioni ScaleR registrate. I valori del campo *counter_value* rappresentano il numero complessivo di istanze per la funzione ScaleR specifica. 

Il conteggio inizia quando la funzionalità viene installata e abilitata nell'istanza ed è cumulativo fino a quando il file che gestisce lo stato viene eliminato o sovrascritto da un amministratore. Di conseguenza, in genere non è possibile reimpostare i valori in *counter_value*. Per monitorare l'utilizzo in base alla sessione, ai tempi del calendario o ad altri intervalli, si consiglia di acquisire i conteggi in una tabella.

### <a name="registration-of-external-script-functions"></a>Registrazione delle funzioni di script esterni

Il linguaggio R supporta gli script arbitrari e la community R fornisce migliaia di pacchetti, ognuno con funzioni e metodi specifici. Tuttavia, questa DMV monitora solo le funzioni ScaleR installate con SQL Server R Services.

La registrazione di queste funzioni viene eseguita quando è installata la funzionalità e le funzioni registrate non possono essere aggiunte o eliminate.

## <a name="examples"></a>Esempi  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>Visualizzazione del numero di script R eseguiti nel server  
 L'esempio seguente visualizza il numero complessivo di esecuzioni di script esterni per il linguaggio R.  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'R';
```  

  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md) 
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

