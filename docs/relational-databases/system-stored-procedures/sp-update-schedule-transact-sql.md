---
title: sp_update_schedule (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_update_schedule
- sp_update_schedule_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_update_schedule
ms.assetid: 97b3119b-e43e-447a-bbfb-0b5499e2fefe
caps.latest.revision: "42"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: caeb6cf9ecf16a77b25bbb9b6a42ae865b077792
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spupdateschedule-transact-sql"></a>sp_update_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le impostazioni per una pianificazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_update_schedule   
    {   [ @schedule_id = ] schedule_id   
      | [ @name = ] 'schedule_name' }  
    [ , [ @new_name = ] new_name ]  
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
    [ , [ @automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@schedule_id =** ] *schedule_id*  
 Identificatore della pianificazione da modificare. *schedule_id* è **int**, non prevede alcun valore predefinito. Entrambi *schedule_id* o *schedule_name* deve essere specificato.  
  
 [  **@name =** ] **'***schedule_name***'**  
 Nome della pianificazione da modificare. *schedule_name*è **sysname**, non prevede alcun valore predefinito. Entrambi *schedule_id* o *schedule_name* deve essere specificato.  
  
 [  **@new_name** =] *nuovo_nome*  
 Nuovo nome della pianificazione. *nuovo_nome* è **sysname**, con un valore predefinito è NULL. Quando *nuovo_nome* è NULL, il nome della pianificazione rimane invariato.  
  
 [  **@enabled =** ] *abilitato*  
 Indica lo stato corrente della pianificazione. *abilitato*è **tinyint**, il valore predefinito è **1** (abilitato). Se **0**, la pianificazione non è abilitata. Quando la pianificazione non è abilitata, non viene eseguito alcun processo su questa pianificazione.  
  
 [  **@freq_type =** ] *freq_type*  
 Valore che indica la frequenza di esecuzione di un processo *freq_type*è **int**, il valore predefinito è **0**, i possibili valori sono i seguenti.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**4**|Ogni giorno|  
|**8**|Settimanale|  
|**16**|Mensile|  
|**32**|Mensile, relativa a *freq intervallo*|  
|**64**|All'avvio del servizio SQLServerAgent|  
|**128**|Quando il computer è inattivo|  
  
 [  **@freq_interval =** ] *freq_interval*  
 Giorni in cui un processo viene eseguito. *freq_interval* è **int**, il valore predefinito è **0**e dipende dal valore di *freq_type*.  
  
|Valore di *freq_type*|Effetto su *freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (una volta)|*freq_interval* è inutilizzato.|  
|**4** (giornaliera)|Ogni *freq_interval* giorni.|  
|**8** (settimanale)|*freq_interval* uno o più dei valori seguenti (combinato con un **OR** operatore logico):<br /><br /> **1** = domenica<br /><br /> **2** = lunedì<br /><br /> **4** = martedì<br /><br /> **8** = mercoledì<br /><br /> **16** = giovedì<br /><br /> **32** = venerdì<br /><br /> **64** = sabato|  
|**16** (mensile)|Nel *freq_interval* giorno del mese.|  
|**32** (frequenza mensile relativa)|*freq_interval* è uno dei seguenti:<br /><br /> **1** = domenica<br /><br /> **2** = lunedì<br /><br /> **3** = martedì<br /><br /> **4** = mercoledì<br /><br /> **5** = giovedì<br /><br /> **6** = venerdì<br /><br /> **7** = sabato<br /><br /> **8** = giorno<br /><br /> **9** = giorno feriale<br /><br /> **10** = giorno festivo|  
|**64** (all'avvio del servizio SQLServerAgent)|*freq_interval* è inutilizzato.|  
|**128**|*freq_interval* è inutilizzato.|  
  
 [  **@freq_subday_type =** ] *freq_subday_type*  
 Specifica le unità per *freq_subday_interval**.* *freq_subday_type*è **int**, il valore predefinito è **0**, i possibili valori sono i seguenti.  
  
|Valore|Descrizione (unità)|  
|-----------|--------------------------|  
|**0x1**|All'ora specificata|  
|**0x2**|Secondi|  
|**0x4**|Minutes|  
|**0x8**|Ore|  
  
 [  **@freq_subday_interval =** ] *freq_subday_interval*  
 Il numero di *freq_subday_type* periodi devono intercorrere tra ogni esecuzione di un processo. *freq_subday_interval*è **int**, il valore predefinito è **0**.  
  
 [  **@freq_relative_interval =** ] *freq_relative_interval*  
 Occorrenza di un processo di *freq_interval* ogni mese, se *freq_interval* è **32** (frequenza mensile relativa). *freq_relative_interval*è **int**, il valore predefinito è **0**, i possibili valori sono i seguenti.  
  
|Valore|Descrizione (unità)|  
|-----------|--------------------------|  
|**1**|Primo|  
|**2**|Secondo|  
|**4**|Terzo|  
|**8**|Quarto|  
|**16**|Ultimo|  
  
 [  **@freq_recurrence_factor =** ] *freq_recurrence_factor*  
 Numero di settimane o mesi tra le esecuzioni pianificate di un processo. *freq_recurrence_factor* viene utilizzata solo se *freq_type* è **8**, **16**, o **32**. *freq_recurrence_factor*è **int**, il valore predefinito è **0**.  
  
 [  **@active_start_date =** ] *active_start_date*  
 Data dalla quale è possibile avviare l'esecuzione del processo. *active_start_date*è **int**, il valore predefinito è NULL, che indica la data odierna. La data è nel formato AAAAMMGG. Se *active_start_date* non è NULL, la data deve essere maggiore o uguale a 19900101.  
  
 Al termine della creazione della pianificazione, esaminare la data di inizio per verificare che corrisponda alla data corretta. Per ulteriori informazioni, vedere la sezione "Pianificazione data di inizio" in [creare e collegare le pianificazioni ai processi](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5).  
  
 [  **@active_end_date =** ] *active_end_date*  
 Data dalla quale è possibile arrestare l'esecuzione del processo. *active_end_date*è **int**, il valore predefinito è **99991231**, che indica il 31 dicembre 9999. La data è nel formato AAAAMMGG.  
  
 [  **@active_start_time =** ] *active_start_time*  
 L'ora compresa tra *active_start_date* e *active_end_date* per avviare l'esecuzione di un processo. *active_start_time*è **int**, il valore predefinito è 000000, che indica le 12:00:00 AM. nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@active_end_time =** ] *active_end_time*  
 L'ora compresa tra *active_start_date* e *active_end_date* per terminare l'esecuzione di un processo. *active_end_time*è **int**, il valore predefinito è **235959**, che indica l'11: 59:59 P.M. nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@owner_login_name** =] **'***owner_login_name***'**]  
 Nome dell'entità server proprietaria della pianificazione. *owner_login_name* è **sysname**, il valore predefinito è NULL, che indica che la pianificazione è di proprietà dell'autore.  
  
 [  **@automatic_post =**] *automatic_post*  
 Riservato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 Tutti i processi che utilizzano la pianificazione, adottano immediatamente le nuove impostazioni. Cambiando la pianificazione, tuttavia, non vengono arrestati i processi attualmente in esecuzione.  
  
## <a name="permissions"></a>Permissions  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Solo i membri di **sysadmin** possibile modificare una pianificazione di proprietà da un altro utente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene modificato lo stato abilitato della pianificazione `NightlyJobs` impostandolo su `0` e impostando il proprietario su `terrid`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_schedule  
    @name = 'NightlyJobs',  
    @enabled = 0,  
    @owner_login_name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creare e collegare le pianificazioni ai processi](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5)   
 [Pianificare un processo](http://msdn.microsoft.com/library/f626390a-a3df-4970-b7a7-a0529e4a109c)   
 [Creare una pianificazione](http://msdn.microsoft.com/library/8c7ef3b3-c06d-4a27-802d-ed329dc86ef3)   
 [SQL Server Agent Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobschedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_delete_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
