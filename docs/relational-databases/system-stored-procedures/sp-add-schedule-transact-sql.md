---
title: sp_add_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_schedule_TSQL
- sp_add_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_schedule
ms.assetid: 9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7
caps.latest.revision: 53
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d53d4d5781d6d1d977549deac3382d948cbdf31b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spaddschedule-transact-sql"></a>sp_add_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea una pianificazione che può essere utilizzata da un numero qualsiasi di processi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_schedule [ @schedule_name = ] 'schedule_name'   
    [ , [ @enabled = ] enabled ]  
    [ , [ @freq_type = ] freq_type ]  
    [ , [ @freq_interval = ] freq_interval ]   
    [ , [ @freq_subday_type = ] freq_subday_type ]   
    [ , [ @freq_subday_interval = ] freq_subday_interval ]   
    [ , [ @freq_relative_interval = ] freq_relative_interval ]   
    [ , [ @freq_recurrence_factor = ] freq_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time = ] active_start_time ]   
    [ , [ @active_end_time = ] active_end_time ]   
    [ , [ @owner_login_name = ] 'owner_login_name' ]  
    [ , [ @schedule_uid = ] schedule_uid OUTPUT ]  
    [ , [ @schedule_id = ] schedule_id OUTPUT ]  
    [ , [ @originating_server = ] server_name ] /* internal */  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@schedule_name =** ] **'***schedule_name***'**  
 Nome della pianificazione. *schedule_name*viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@enabled =** ] *abilitato*  
 Indica lo stato corrente della pianificazione. *abilitata*viene **tinyint**, il valore predefinito è **1** (abilitato). Se **0**, la pianificazione non è abilitata. Quando la pianificazione non è abilitata, non viene eseguito alcun processo su questa pianificazione.  
  
 [ **@freq_type =** ] *freq_type*  
 Valore che indica la frequenza di esecuzione di un processo *freq_type*viene **int**, il valore predefinito è **0**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**4**|Ogni giorno|  
|**8**|Settimanale|  
|**16**|Mensile|  
|**32**|Mensile, relativa a *freq_interval*|  
|**64**|All'avvio del servizio SQLServerAgent|  
|**128**|Quando il computer è inattivo|  
  
 [  **@freq_interval =** ] *freq_interval*  
 Giorni in cui un processo viene eseguito. *freq_interval* viene **int**, il valore predefinito è **1**e dipende dal valore del *freq_type*.  
  
|Value of *freq_type*|Effetto su *freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (una volta)|*freq_interval* è inutilizzato.|  
|**4** (giornaliera)|Ogni *freq_interval* giorni.|  
|**8** (settimanale)|*freq_interval* corrisponde a uno o più dei valori seguenti (in combinazione con un operatore logico OR):<br /><br /> **1** = domenica<br /><br /> **2** = lunedì<br /><br /> **4** = martedì<br /><br /> **8** = mercoledì<br /><br /> **16** = giovedì<br /><br /> **32** = venerdì<br /><br /> **64** = sabato|  
|**16** (mensile)|Nel *freq_interval* giorno del mese.|  
|**32** (frequenza mensile relativa)|*freq_interval* è uno dei seguenti:<br /><br /> **1** = domenica<br /><br /> **2** = lunedì<br /><br /> **3** = martedì<br /><br /> **4** = mercoledì<br /><br /> **5** = giovedì<br /><br /> **6** = venerdì<br /><br /> **7** = sabato<br /><br /> **8** = giorno<br /><br /> **9** = giorno feriale<br /><br /> **10** = giorno festivo|  
|**64** (all'avvio del servizio SQLServerAgent)|*freq_interval* è inutilizzato.|  
|**128**|*freq_interval* è inutilizzato.|  
  
 [ **@freq_subday_type =** ] *freq_subday_type*  
 Specifica le unità per *freq_subday_interval*. *freq_subday_type*viene **int**, il valore predefinito è **0**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione (unità)|  
|-----------|--------------------------|  
|**0x1**|All'ora specificata|  
|**0x2**|Secondi|  
|**0x4**|Minutes|  
|**0x8**|Ore|  
  
 [ **@freq_subday_interval =** ] *freq_subday_interval*  
 Il numero di *freq_subday_type* periodi devono intercorrere tra ogni esecuzione di un processo. *freq_subday_interval*viene **int**, il valore predefinito è **0**. Nota: l'intervallo dovrebbe superare i 10 secondi. *freq_subday_interval* viene ignorato nei casi in cui *freq_subday_type* è uguale a **1**.  
  
 [  **@freq_relative_interval =** ] *freq_relative_interval*  
 Occorrenza di un processo di *freq_interval* ogni mese, se *freq_interval* è 32 (mensile relativa). *freq_relative_interval*viene **int**, il valore predefinito è **0**, e può essere uno dei valori seguenti. *freq_relative_interval* viene ignorato nei casi in cui *freq_type* non è uguale a 32 caratteri.  
  
|Value|Descrizione (unità)|  
|-----------|--------------------------|  
|**1**|Primo|  
|**2**|Secondo|  
|**4**|Terzo|  
|**8**|Quarto|  
|**16**|Ultimo|  
  
 [  **@freq_recurrence_factor =** ] *freq_recurrence_factor*  
 Numero di settimane o mesi tra le esecuzioni pianificate di un processo. *freq_recurrence_factor* viene utilizzata solo se *freq_type* viene **8**, **16**, o **32**. *freq_recurrence_factor*viene **int**, il valore predefinito è **0**.  
  
 [ **@active_start_date =** ] *active_start_date*  
 Data dalla quale è possibile avviare l'esecuzione del processo. *active_start_date*viene **int**, un valore predefinito è NULL, che indica la data odierna. La data è nel formato AAAAMMGG. Se *active_start_date* non è NULL, la data deve essere maggiore o uguale a 19900101.  
  
 Al termine della creazione della pianificazione, esaminare la data di inizio per verificare che corrisponda alla data corretta. Per ulteriori informazioni, vedere la sezione "Pianificazione data di inizio" in [creare e collegare le pianificazioni ai processi](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5).  
  
 Per le pianificazioni settimanali o mensili, tramite Agent viene ignorato se la data di active_start_date è già passata e viene invece utilizzata la data corrente. Quando una pianificazione di SQL Agent viene creata utilizzando sp_add_schedule è possibile specificare il parametro active_start_date che rappresenta la data di avvio dell'esecuzione del processo. Se il tipo di pianificazione è settimanale o mensile e il parametro active_start_date è impostato su una data già trascorsa, il parametro active_start_date viene ignorato e la data corrente verrà utilizzata per active_start_date.  
  
 [ **@active_end_date =** ] *active_end_date*  
 Data dalla quale è possibile arrestare l'esecuzione del processo. *active_end_date*viene **int**, il valore predefinito è **99991231**, che indica il 31 dicembre 9999. La data è nel formato AAAAMMGG.  
  
 [  **@active_start_time =** ] *active_start_time*  
 L'ora compresa tra *active_start_date* e *active_end_date* per avviare l'esecuzione di un processo. *active_start_time*viene **int**, il valore predefinito è **000000**, a indicare 12:00:00 A.M. nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@active_end_time =** ] *active_end_time*  
 L'ora compresa tra *active_start_date* e *active_end_date* per terminare l'esecuzione di un processo. *active_end_time*viene **int**, il valore predefinito è **235959**, a indicare 11:59: le ore 23.59.59 nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [ **@owner_login_name**=] **'***owner_login_name***'**  
 Nome dell'entità server proprietaria della pianificazione. *owner_login_name* viene **sysname**, con un valore predefinito è NULL, a indicare che la pianificazione è di proprietà dell'autore.  
  
 [ **@schedule_uid**= ] *schedule_uid***OUTPUT**  
 Identificatore univoco della pianificazione. *valore schedule_uid* è una variabile di tipo **uniqueidentifier**.  
  
 [ **@schedule_id**= ] *schedule_id***OUTPUT**  
 Identificatore della pianificazione. *schedule_id* è una variabile di tipo **int**.  
  
 [ **@originating_server**= ] *server_name*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è incluso un semplice strumento grafico per la gestione dei processi, che è lo strumento consigliato per la creazione e la gestione dell'infrastruttura dei processi.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-schedule"></a>A. Creazione di una pianificazione  
 Nell'esempio seguente viene creata una pianificazione denominata `RunOnce`. La pianificazione viene eseguita una volta, alle `23:30` del giorno in cui è stata creata.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_schedule  
    @schedule_name = N'RunOnce',  
    @freq_type = 1,  
    @active_start_time = 233000 ;  
  
GO  
```  
  
### <a name="b-creating-a-schedule-attaching-the-schedule-to-multiple-jobs"></a>B. Creazione di una pianificazione e associazione della pianificazione a più processi  
 Nell'esempio seguente viene creata una pianificazione denominata `NightlyJobs`. I processi che utilizzano questa pianificazione vengono eseguiti ogni giorno quando l'ora indicata dal server è `01:00`. Nell'esempio la pianificazione viene collegata al processo `BackupDatabase` e al processo `RunReports`.  
  
> [!NOTE]  
>  In questo esempio si presuppone che il processo `BackupDatabase` e il processo `RunReports` esistano già.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_add_schedule  
    @schedule_name = N'NightlyJobs' ,  
    @freq_type = 4,  
    @freq_interval = 1,  
    @active_start_time = 010000 ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'BackupDatabase',  
   @schedule_name = N'NightlyJobs' ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'RunReports',  
   @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creare e collegare le pianificazioni ai processi](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5)   
 [Pianificare un processo](http://msdn.microsoft.com/library/f626390a-a3df-4970-b7a7-a0529e4a109c)   
 [Creare una pianificazione](http://msdn.microsoft.com/library/8c7ef3b3-c06d-4a27-802d-ed329dc86ef3)   
 [Stored procedure SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_jobschedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
