---
title: sp_help_jobhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobhistory_TSQL
- sp_help_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobhistory
ms.assetid: a944d44e-411b-4735-8ce4-73888d4262d7
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e001e9e0ea0dd7dfdbe64a788db465125b04e414
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpjobhistory-transact-sql"></a>sp_help_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui processi per i server del dominio di amministrazione multiserver.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_jobhistory [ [ @job_id = ] job_id ]   
     [ , [ @job_name = ] 'job_name' ]   
     [ , [ @step_id = ] step_id ]   
     [ , [ @sql_message_id = ] sql_message_id ]   
     [ , [ @sql_severity = ] sql_severity ]   
     [ , [ @start_run_date = ] start_run_date ]   
     [ , [ @end_run_date = ] end_run_date ]   
     [ , [ @start_run_time = ] start_run_time ]   
     [ , [ @end_run_time = ] end_run_time ]   
     [ , [ @minimum_run_duration = ] minimum_run_duration ]   
     [ , [ @run_status = ] run_status ]   
     [ , [ @minimum_retries = ] minimum_retries ]   
     [ , [ @oldest_first = ] oldest_first ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @mode = ] 'mode' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id=** ] *job_id*  
 Numero di identificazione del processo. *job_id* viene **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [ **@job_name=** ] **'***job_name***'**  
 Nome del processo. *job_name* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@step_id=** ] *step_id*  
 Numero di identificazione del passaggio. *step_id* viene **int**, con un valore predefinito è NULL.  
  
 [ **@sql_message_id=** ] *sql_message_id*  
 Numero di identificazione del messaggio di errore restituito da Microsoft SQL Server durante l'esecuzione del processo. *sql_message_id* viene **int**, con un valore predefinito è NULL.  
  
 [ **@sql_severity=** ] *sql_severity*  
 Livello di gravità del messaggio di errore restituito da SQL Server durante l'esecuzione del processo. *sql_severity* viene **int**, con un valore predefinito è NULL.  
  
 [ **@start_run_date=** ] *start_run_date*  
 Data di avvio del processo. *start_run_date*viene **int**, con un valore predefinito è NULL. *start_run_date* deve essere immesso nel formato YYYYMMDD, dove YYYY è un anno di quattro caratteri, MM è un nome del mese di due caratteri, e DD è un nome di giorno di due caratteri.  
  
 [ **@end_run_date=** ] *end_run_date*  
 Data di completamento del processo. *espresso* viene **int**, con un valore predefinito è NULL. *espresso*deve essere immesso nel formato aaaammgg, dove AAAA è l'anno a quattro cifre, MM è il un nome del mese di due caratteri e GG è un nome di giorno di due caratteri.  
  
 [  **@start_run_time=** ] *start_run_time*  
 Ora di avvio del processo. *start_run_time* viene **int**, con un valore predefinito è NULL. *start_run_time*deve essere un valore nel formato HHMMSS, dove HH è l'ora, MM è il minuto espressi con due cifre del giorno, e SS è il secondo dei due caratteri del giorno.  
  
 [ **@end_run_time=** ] *end_run_time*  
 Ora di completamento del processo. *end_run_time* viene **int**, con un valore predefinito è NULL. *end_run_time*deve essere un valore nel formato HHMMSS, dove HH è l'ora, MM è il minuto espressi con due cifre del giorno, e SS è il secondo dei due caratteri del giorno.  
  
 [  **@minimum_run_duration=** ] *minimum_run_duration*  
 Durata minima per il completamento del processo. *minimum_run_duration* viene **int**, con un valore predefinito è NULL. *minimum_run_duration*deve essere un valore nel formato HHMMSS, dove HH è l'ora, MM è il minuto espressi con due cifre del giorno, e SS è il secondo dei due caratteri del giorno.  
  
 [  **@run_status=** ] *run_status*  
 Stato di esecuzione del processo. *run_status* viene **int**, con un valore predefinito è NULL, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0**|Non riuscito|  
|**1**|Operazione completata|  
|**2**|Nuovo tentativo (solo passaggio)|  
|**3**|Canceled|  
|**4**|Messaggio di esecuzione in corso|  
|**5**|Unknown|  
  
 [  **@minimum_retries=** ] *minimum_retries*  
 Numero minimo di tentativi per l'esecuzione di un processo. *minimum_retries* viene **int**, con un valore predefinito è NULL.  
  
 [  **@oldest_first=** ] *oldest_first*  
 Indica se i processi meno recenti devono essere visualizzati per primi nell'output. *oldest_first* viene **int**, il valore predefinito è **0**, che presenta i processi più recenti prima di tutto. **1** consente innanzitutto i processi meno recenti.  
  
 [ **@server=** ] **'***server***'**  
 Nome del server in cui è stato eseguito il processo. *server* viene **nvarchar(30)**, con un valore predefinito è NULL.  
  
 [  **@mode=** ] **'***modalità***'**  
 Indica se stampare tutte le colonne nel set di risultati (**completo**) o un riepilogo delle colonne. *modalità* viene **varchar(7)**, il valore predefinito è **riepilogo**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 L'elenco delle colonne dipende dal valore di *modalità*. Il set di colonne più completo è illustrato di seguito e viene restituito quando *modalità* è FULL.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Numero di identificazione della voce di cronologia.|  
|**job_id**|**uniqueidentifier**|Numero di identificazione del processo.|  
|**job_name**|**sysname**|Nome del processo.|  
|**step_id**|**int**|Numero di identificazione del passaggio (sarà **0** per la cronologia dei processi).|  
|**step_name**|**sysname**|Nome del passaggio (è NULL per la cronologia dei processi).|  
|**sql_message_id**|**int**|Per un passaggio [!INCLUDE[tsql](../../includes/tsql-md.md)], numero di errore [!INCLUDE[tsql](../../includes/tsql-md.md)] più recente restituito durante l'esecuzione del comando.|  
|**sql_severity**|**int**|Per un passaggio [!INCLUDE[tsql](../../includes/tsql-md.md)], gravità di errore [!INCLUDE[tsql](../../includes/tsql-md.md)] più elevata restituita durante l'esecuzione del comando.|  
|**message**|**nvarchar(1024)**|Messaggio della cronologia relativo al processo o al passaggio.|  
|**run_status**|**int**|Risultato del processo o del passaggio.|  
|**run_date**|**int**|Data di inizio dell'esecuzione del processo o del passaggio.|  
|**run_time**|**int**|Ora di inizio dell'esecuzione del processo o del passaggio.|  
|**run_duration**|**int**|Periodo trascorso, in formato HHMMSS, nella fase di esecuzione del processo o passaggio.|  
|**operator_emailed**|**nvarchar(20)**|Operatore che ha ricevuto la notifica relativa al processo tramite posta elettronica (è NULL per la cronologia dei passaggi).|  
|**operator_netsent**|**nvarchar(20)**|Operatore che ha ricevuto la notifica relativa al processo tramite un messaggio di rete (è NULL per la cronologia dei passaggi).|  
|**operator_paged**|**nvarchar(20)**|Operatore che ha ricevuto la notifica relativa al processo tramite cercapersone (è NULL per la cronologia dei passaggi).|  
|**retries_attempted**|**int**|Numero di tentativi di esecuzione del passaggio (è sempre 0 per la cronologia dei processi).|  
|**server**|**nvarchar(30)**|Server in cui viene eseguito il processo o il passaggio. È sempre (**locale**).|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_jobhistory** restituisce un report con la cronologia dei processi pianificati specificati. Se non viene specificato alcun parametro, il report include la cronologia di tutti i processi pianificati.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 I membri del **SQLAgentUserRole** ruolo del database può visualizzare solo la cronologia dei processi di cui sono proprietari.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-all-job-information-for-a-job"></a>A. Visualizzazione di un elenco di tutte le informazioni di un processo  
 Nell'esempio seguente viene visualizzato un elenco di informazioni per il processo `NightlyBackups`  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobhistory   
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-that-match-certain-conditions"></a>B. Visualizzazione di un elenco di informazioni per i processi che corrispondono a determinate condizioni  
 Nell'esempio seguente vengono stampate tutte le colonne e tutte le informazioni relative ai processi e ai passaggi non eseguiti correttamente che hanno generato un messaggio di errore `50100` (messaggio di errore definito dall'utente) con livello di gravità `20`.  
  
```  
USE msdb  
GO  
  
EXEC dbo.sp_help_jobhistory  
    @sql_message_id = 50100,  
    @sql_severity = 20,  
    @run_status = 0,  
    @mode = N'FULL' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
