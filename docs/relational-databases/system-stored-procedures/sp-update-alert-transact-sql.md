---
title: sp_update_alert (Transact-SQL) | Microsoft Docs
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
- sp_update_alert_TSQL
- sp_update_alert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_alert
ms.assetid: 4bbaeaab-8aca-4c9e-abc1-82ce73090bd3
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a7715e354208953dc62e4a161a44f195babf92f3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262884"
---
# <a name="spupdatealert-transact-sql"></a>sp_update_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiorna le impostazioni di un avviso esistente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_update_alert   
     [ @name =] 'name'   
     [ , [ @new_name =] 'new_name']   
     [ , [ @enabled =] enabled]   
     [ , [ @message_id =] message_id]   
     [ , [ @severity =] severity]   
     [ , [ @delay_between_responses =] delay_between_responses]   
     [ , [ @notification_message =] 'notification_message']   
     [ , [ @include_event_description_in =] include_event_description_in]   
     [ , [ @database_name =] 'database']   
     [ , [ @event_description_keyword =] 'event_description_keyword']   
     [ , [ @job_id =] job_id | [@job_name =] 'job_name']   
     [ , [ @occurrence_count = ] occurrence_count]   
     [ , [ @count_reset_date =] count_reset_date]   
     [ , [ @count_reset_time =] count_reset_time]   
     [ , [ @last_occurrence_date =] last_occurrence_date]   
     [ , [ @last_occurrence_time =] last_occurrence_time]   
     [ , [ @last_response_date =] last_response_date]   
     [ , [ @last_response_time =] last_response _time]  
     [ , [ @raise_snmp_trap =] raise_snmp_trap]  
     [ , [ @performance_condition =] 'performance_condition' ]   
     [ , [ @category_name =] 'category']  
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name =**] **'***nome***'**  
 Nome dell'avviso da aggiornare. *nome* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@new_name =**] **'***new_name***'**  
 Nuovo nome per l'avviso. Il nome deve essere univoco. *nuovo_nome* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@enabled =**] *abilitato*  
 Specifica se l'avviso è abilitato (**1**) o non è abilitata (**0**). *abilitata* viene **tinyint**, con un valore predefinito è NULL. Per consentire la generazione di un avviso, è necessario che l'avviso sia abilitato.  
  
 [ **@message_id =**] *message_id*  
 Nuovo messaggio o numero di errore per la definizione dell'avviso. In genere, *message_id* corrisponde al numero di errore nella **sysmessages** tabella. *message_id* viene **int**, con un valore predefinito è NULL. Un messaggio con ID può essere utilizzato solo se l'impostazione del livello di gravità dell'avviso è **0**.  
  
 [  **@severity =**] *gravità*  
 Nuovo livello di gravità (da **1** tramite **25**) per la definizione di avviso. Qualsiasi [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'avviso verranno attivato da messaggi inviati al registro applicazioni di Windows con livello di gravità specificato. *livello di gravità* viene **int**, con un valore predefinito è NULL. Un livello di gravità può essere utilizzato solo se l'impostazione di ID di messaggio per l'avviso è **0**.  
  
 [ **@delay_between_responses =**] *delay_between_responses*  
 Nuovo intervallo di attesa, in secondi, che intercorre tra le risposte all'avviso. *delay_between_responses* viene **int**, con un valore predefinito è NULL.  
  
 [  **@notification_message =**] **'***notification_message***'**  
 Testo modificato di un messaggio aggiuntivo inviato all'operatore come parte del messaggio di posta elettronica, **net send**, o una notifica tramite cercapersone. *notification_message* viene **nvarchar(512)**, con un valore predefinito è NULL.  
  
 [ **@include_event_description_in =**] *include_event_description_in*  
 Specifica se includere o meno la descrizione dell'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del registro applicazioni di Windows nel messaggio di notifica. *include_event_description_in* viene **tinyint**, con un valore predefinito è NULL, e può essere uno o più dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0**|Nessuno|  
|**1**|Posta elettronica|  
|**2**|Cercapersone|  
|**4**|**net send**|  
|**7**|Tutto|  
  
 [  **@database_name =**] **'***database***'**  
 Nome del database nel quale deve verificarsi l'errore affinché l'avviso venga generato. *database* è **sysname.** I nomi racchiusi tra parentesi quadre ([ ]) non sono ammessi. Il valore predefinito è NULL.  
  
 [ **@event_description_keyword =**] **'***event_description_keyword***'**  
 Sequenza di caratteri che è necessario individuare nella descrizione dell'errore inclusa nel log dei messaggi di errore. È possibile utilizzare i caratteri dei criteri di ricerca dell'espressione LIKE [!INCLUDE[tsql](../../includes/tsql-md.md)]. *event_description_keyword* viene **nvarchar(100)**, con un valore predefinito è NULL. Questo parametro è utile per filtrare i nomi degli oggetti (ad esempio, **% customer_table %**).  
  
 [ **@job_id =**] *job_id*  
 Numero di identificazione del processo. *job_id* viene **uniqueidentifier**, con un valore predefinito è NULL. Se *job_id* è specificato, *job_name* deve essere omessa.  
  
 [ **@job_name =**] **'***job_name***'**  
 Nome del processo che viene eseguito in risposta all'avviso. *job_name* viene **sysname**, con un valore predefinito è NULL. Se *job_name* è specificato, *job_id* deve essere omessa.  
  
 [  **@occurrence_count =** ] *numero_occorrenze*  
 Reimposta il numero di occorrenze dell'avviso. *numero_occorrenze* viene **int**, con un valore predefinito è NULL e può essere impostata solo su **0**.  
  
 [ **@count_reset_date =**] *count_reset_date*  
 Reimposta la data dell'ultimo azzeramento del numero di occorrenze. *count_reset_date* viene **int**, con un valore predefinito è NULL.  
  
 [ **@count_reset_time =**] *count_reset_time*  
 Reimposta l'ora dell'ultimo azzeramento del numero di occorrenze. *count_reset_time* viene **int**, con un valore predefinito è NULL.  
  
 [  **@last_occurrence_date =**] *last_occurrence_date*  
 Reimposta la data dell'ultima occorrenza dell'avviso. *last_occurrence_date* viene **int**, con un valore predefinito è NULL e può essere impostata solo su **0**.  
  
 [  **@last_occurrence_time =**] *last_occurrence_time*  
 Reimposta l'ora dell'ultima occorrenza dell'avviso. *last_occurrence_time* viene **int**, con un valore predefinito è NULL e può essere impostata solo su **0**.  
  
 [  **@last_response_date =**] *last_response_date*  
 Reimposta la data dell'ultima risposta all'avviso inviata dal servizio SQLServerAgent. *last_response_date* viene **int**, con un valore predefinito è NULL e può essere impostata solo su **0**.  
  
 [  **@last_response_time =**] *last_response_time*  
 Reimposta l'ora dell'ultima risposta all'avviso inviata dal servizio SQLServerAgent. *last_response_time* viene **int**, con un valore predefinito è NULL e può essere impostata solo su **0**.  
  
 [ **@raise_snmp_trap =**] *raise_snmp_trap*  
 Riservato.  
  
 [  **@performance_condition =**] **'***performance_condition***'**  
 Un valore espresso nel formato **'***itemcomparatorvalue***'**. *performance_condition* viene **nvarchar(512)**, con un valore predefinito è NULL ed è costituito da questi elementi.  
  
|Componente del formato|Description|  
|--------------------|-----------------|  
|*Elemento*|Oggetto prestazioni, contatore delle prestazioni o istanza denominata del contatore|  
|*Criterio di confronto*|Uno degli operatori seguenti: **>**, **<**, **=**|  
|*Valore*|Valore numerico del contatore|  
  
 [  **@category_name =**] **'***categoria***'**  
 Nome della categoria di avvisi. *categoria* viene **sysname** con un valore predefinito è NULL.  
  
 [ **@wmi_namespace**=] **'***wmi_namespace***'**  
 Spazio dei nomi WMI in cui eseguire query per gli eventi. *wmi_namespace* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@wmi_query**= ] **'***wmi_query***'**  
 Query che consente di specificare l'evento WMI per l'avviso. *Wmi_query* viene **nvarchar(512)**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Solo **sysmessages** scritto il [!INCLUDE[msCoName](../../includes/msconame-md.md)] registro applicazioni di Windows può essere generato un avviso.  
  
 **sp_update_alert** cambia solo le impostazioni di avviso per il parametro che vengono forniti i valori. Se si omette un parametro, viene mantenuta l'impostazione corrente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa stored procedure, gli utenti devono essere un membro del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'impostazione di abilitazione di `Test Alert` viene sostituita con `0`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_alert  
    @name = N'Test Alert',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
