---
title: sp_help_alert (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_alert
- sp_help_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_alert
ms.assetid: 850cef4e-6348-4439-8e79-fd1bca712091
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: afaa688907d80a37855890ff8fcf29acd80f9c27
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpalert-transact-sql"></a>sp_help_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sugli avvisi definiti per il server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_alert [ [ @alert_name = ] 'alert_name' ]   
     [ , [ @order_by = ] 'order_by' ]   
     [ , [ @alert_id = ] alert_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @legacy_format = ] legacy_format ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@alert_name =**] **'***alert_name***'**  
 Nome dell'avviso. *alert_name* viene **nvarchar (128)**. Se *alert_name* viene omesso, vengono restituite informazioni su tutti gli avvisi.  
  
 [  **@order_by =**] **'***order_by***'**  
 Criterio da applicare per l'ordinamento dei risultati. *order_by*viene **sysname**, con un valore predefinito è N' '*nome*'.  
  
 [ **@alert_id =**] *alert_id*  
 Numero di identificazione dell'avviso su cui si desidera ottenere informazioni. *alert_id*viene **int**, con un valore predefinito è NULL.  
  
 [  **@category_name =**] **'***categoria***'**  
 Categoria dell'avviso. *categoria* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@legacy_format**=] *legacy_format*  
 Indica se generare un set di risultati legacy. *legacy_format* viene **bit**, il valore predefinito è **0**. Quando *legacy_format* è **1**, **sp_help_alert** restituisce il set di risultati restituito da **sp_help_alert** in Microsoft SQL Server 2000.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Quando **@legacy_format** è **0**, **sp_help_alert** produce il seguente set di risultati.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identificatore univoco di tipo integer assegnato dal sistema.|  
|**name**|**sysname**|Nome dell'avviso (ad esempio Demo: Full **msdb** log).|  
|**event_source**|**Nvarchar (100)**|Origine dell'evento. Sarà sempre **MSSQLServer** per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|Numero dell'errore del messaggio che definisce l'avviso (In genere corrisponde al numero di errore nella **sysmessages** tabella). Se il livello di gravità viene utilizzato per definire l'avviso, **message_id** è **0** o NULL.|  
|**severity**|**int**|Livello di gravità (da **9** tramite **25**, **110**, **120**, **130**, o **140**) che definisce l'avviso.|  
|**enabled**|**tinyint**|Stato indica se l'avviso è attualmente abilitato (**1**) o non (**0**). Gli avvisi non abilitati non vengono inviati.|  
|**delay_between_responses**|**int**|Periodo di attesa in secondi tra risposte successive per l'avviso.|  
|**last_occurrence_date**|**int**|Data dell'ultima generazione dell'avviso.|  
|**last_occurrence_time**|**int**|Ora dell'ultima generazione dell'avviso.|  
|**last_response_date**|**int**|Data ultimo avviso ha risposto di **SQLServerAgent** servizio.|  
|**last_response_time**|**int**|Ora dell'ultima l'avviso ha risposto di **SQLServerAgent** servizio.|  
|**notification_message**|**nvarchar(512)**|Messaggio aggiuntivo facoltativo inviato all'operatore come parte della notifica tramite posta elettronica o cercapersone.|  
|**include_event_description**|**tinyint**|Indica se la descrizione dell'errore di SQL Server inclusa nel registro applicazioni di Microsoft Windows deve essere inserita nel messaggio di notifica.|  
|**database_name**|**sysname**|Database in cui deve verificarsi l'errore affinché l'avviso venga generato. Se il nome del database è NULL, l'avviso viene generato indipendentemente dal database in cui l'errore si verifica.|  
|**event_description_keyword**|**Nvarchar (100)**|Descrizione dell'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclusa nel registro applicazioni di Windows, che deve corrispondere alla sequenza di caratteri specificata.|  
|**occurrence_count**|**int**|Numero di volte che l'avviso è stato generato.|  
|**count_reset_date**|**int**|Data di **numero_occorrenze** ultima reimpostazione.|  
|**count_reset_time**|**int**|Tempo di **numero_occorrenze** ultima reimpostazione.|  
|**job_id**|**uniqueidentifier**|Numero di identificazione del processo da eseguire in risposta a un avviso.|  
|**job_name**|**sysname**|Nome del processo da eseguire in risposta a un avviso.|  
|**has_notification**|**int**|È diverso da zero se uno o più operatori ricevono una notifica dell'avviso. Può essere uno o più d'uno dei valori seguenti uniti dall'operatore OR:<br /><br /> **1**= notifica tramite posta elettronica<br /><br /> **2**= notifica tramite cercapersone<br /><br /> **4**= ha **net send** notifica.|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**performance_condition**|**nvarchar(512)**|Se **tipo** è **2**, questa colonna Mostra la definizione della condizione delle prestazioni; in caso contrario, la colonna è NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 è sempre '[Uncategorized]'.|  
|**wmi_namespace**|**sysname**|Se **tipo** è **3**, questa colonna viene visualizzato lo spazio dei nomi per l'evento WMI.|  
|**wmi_query**|**nvarchar(512)**|Se **tipo** è **3**, questa colonna viene visualizzata la query per l'evento WMI.|  
|**type**|**int**|Tipo dell'evento:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avviso per evento<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avviso relativo alle prestazioni<br /><br /> **3** = avviso per evento WMI|  
  
 Quando **@legacy_format** è **1**, **sp_help_alert** produce il seguente set di risultati.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identificatore univoco di tipo integer assegnato dal sistema.|  
|**name**|**sysname**|Nome dell'avviso (ad esempio Demo: Full **msdb** log).|  
|**event_source**|**Nvarchar (100)**|Origine dell'evento. Sarà sempre **MSSQLServer** per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|Numero dell'errore del messaggio che definisce l'avviso (In genere corrisponde al numero di errore nella **sysmessages** tabella). Se il livello di gravità viene utilizzato per definire l'avviso, **message_id** è **0** o NULL.|  
|**severity**|**int**|Livello di gravità (da **9** tramite **25**, **110**, **120**, **130**, o 1**40**) che definisce l'avviso.|  
|**enabled**|**tinyint**|Stato indica se l'avviso è attualmente abilitato (**1**) o non (**0**). Gli avvisi non abilitati non vengono inviati.|  
|**delay_between_responses**|**int**|Periodo di attesa in secondi tra risposte successive per l'avviso.|  
|**last_occurrence_date**|**int**|Data dell'ultima generazione dell'avviso.|  
|**last_occurrence_time**|**int**|Ora dell'ultima generazione dell'avviso.|  
|**last_response_date**|**int**|Data ultimo avviso ha risposto di **SQLServerAgent** servizio.|  
|**last_response_time**|**int**|Ora dell'ultima l'avviso ha risposto di **SQLServerAgent** servizio.|  
|**notification_message**|**nvarchar(512)**|Messaggio aggiuntivo facoltativo inviato all'operatore come parte della notifica tramite posta elettronica o cercapersone.|  
|**include_event_description**|**tinyint**|Indica se la descrizione dell'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclusa nel registro applicazioni di Windows deve essere inserita nel messaggio di notifica.|  
|**database_name**|**sysname**|Database in cui deve verificarsi l'errore affinché l'avviso venga generato. Se il nome del database è NULL, l'avviso viene generato indipendentemente dal database in cui l'errore si verifica.|  
|**event_description_keyword**|**Nvarchar (100)**|Descrizione dell'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclusa nel registro applicazioni di Windows, che deve corrispondere alla sequenza di caratteri specificata.|  
|**occurrence_count**|**int**|Numero di volte che l'avviso è stato generato.|  
|**count_reset_date**|**int**|Data di **numero_occorrenze** ultima reimpostazione.|  
|**count_reset_time**|**int**|Tempo di **numero_occorrenze** ultima reimpostazione.|  
|**job_id**|**uniqueidentifier**|Numero di identificazione del processo.|  
|**job_name**|**sysname**|Processo su richiesta da eseguire in risposta a un avviso.|  
|**has_notification**|**int**|È diverso da zero se uno o più operatori ricevono una notifica dell'avviso. Può essere uno o più d'uno dei valori seguenti uniti dall'operatore OR:<br /><br /> **1**= notifica tramite posta elettronica<br /><br /> **2**= notifica tramite cercapersone<br /><br /> **4**= ha **net send** notifica.|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)].|  
|**performance_condition**|**nvarchar(512)**|Se **tipo** è **2**, questa colonna Mostra la definizione della condizione delle prestazioni. Se **tipo** è **3**, questa colonna viene visualizzata la query per l'evento WMI. Negli altri casi la colonna è NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Sarà sempre '**[senza categoria]**' per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.|  
|**type**|**int**|Tipo di avviso:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avviso per evento<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avviso relativo alle prestazioni<br /><br /> **3** = avviso per evento WMI|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_alert** deve essere eseguita la **msdb** database.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono appartenere al ruolo predefinito del database **SQLAgentOperatorRole** nel database **msdb** .  
  
 Per informazioni dettagliate su **SQLAgentOperatorRole**, vedere [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sull'avviso `Demo: Sev. 25 Errors`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
