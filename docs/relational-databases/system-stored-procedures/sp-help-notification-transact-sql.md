---
title: sp_help_notification (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
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
- sp_help_notification
- sp_help_notification_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_notification
ms.assetid: 0273457f-9d2a-4a6f-9a16-6a6bf281cba0
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c779b314553c1895071ab04b5131d998c029cc94
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpnotification-transact-sql"></a>sp_help_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un elenco di avvisi per un determinato operatore o un elenco di operatori per un determinato avviso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_notification  
     [ @object_type = ] 'object_type' ,  
     [ @name = ] 'name' ,  
     [ @enum_type = ] 'enum_type' ,   
     [ @notification_method = ] notification_method   
     [ , [ @target_name = ] 'target_name' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@object_type =**] **'***object_type***'**  
 Tipo di informazioni che si desidera ottenere. *object_type*viene **char(9)**, non prevede alcun valore predefinito. *object_type* sono ALERTS, con cui vengono elencati gli avvisi assegnati al nome dell'operatore specificato*,* o operatori, in cui sono elencati gli operatori responsabili del nome dell'avviso fornito*.*  
  
 [  **@name =**] **'***nome***'**  
 Nome di un operatore (se *object_type* è OPERATORS) o nome di un avviso (se *object_type* è ALERTS). *nome* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@enum_type =**] **'***enum_type***'**  
 Il *object_type*informazioni restituite. *enum_type* è ACTUAL nella maggior parte dei casi. *enum_type*viene **char (10)**e non prevede alcun valore predefinito può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|ACTUAL|Elenca solo i *oggetti object_type* associato *nome*.|  
|ALL|Elenca tutte le*oggetti object_type* inclusi quelli che non sono associati *nome*.|  
|TARGET|Elenca solo i *oggetti object_type* corrispondenza fornito *target_name*, indipendentemente dall'associazione con*nome*.|  
  
 [  **@notification_method =**] *notification_method*  
 Un valore numerico che determina le colonne del metodo di notifica da restituire. *notification_method* viene **tinyint**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Posta elettronica: restituisce solo il **use_email** colonna.|  
|**2**|Cercapersone: restituisce solo il **use_pager** colonna.|  
|**4**|NetSend: restituisce solo il **use_netsend** colonna.|  
|**7**|Tutto: restituisce tutte le colonne.|  
  
 [  **@target_name =**] **'***target_name***'**  
 Il nome di un avviso da cercare (se *object_type* è ALERTS) o il nome di un operatore per la ricerca (se *object_type* è OPERATORS). *target_name* è necessario solo se *enum_type* destinazione. *target_name* viene **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-valves"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Se *object_type* è **avvisi**, il set di risultati vengono elencati tutti gli avvisi per un determinato operatore.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Numero di identificazione dell'avviso.|  
|**alert_name**|**sysname**|Nome dell'avviso.|  
|**use_email**|**int**|Specifica se il metodo di notifica utilizzato è la posta elettronica:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**use_pager**|**int**|Specifica se il metodo di notifica utilizzato è il cercapersone:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**use_netsend**|**int**|Specifica se il metodo di notifica utilizzato è NetSend:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**has_email**|**int**|Numero di notifiche inviate tramite posta elettronica per l'avviso specificato.|  
|**has_pager**|**int**|Numero di notifiche inviate tramite cercapersone per l'avviso specificato.|  
|**has_netsend**|**int**|Numero di **net send** notifiche inviate per questo avviso.|  
  
 Se **object_type** è **operatori**, il set di risultati include tutti gli operatori per un determinato avviso.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**operator_id**|**int**|Numero di identificazione dell'operatore.|  
|**operator_name**|**sysname**|Nome dell'operatore.|  
|**use_email**|**int**|Specifica se il metodo di notifica utilizzato è la posta elettronica:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**use_pager**|**int**|Specifica se il metodo di notifica utilizzato è il cercapersone:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**use_netsend**|**int**|Specifica se il metodo di notifica utilizzato è NetSend:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**has_email**|**int**|Specifica se all'operatore è associato un indirizzo di posta elettronica:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**has_pager**|**int**|Specifica se all'operatore è associato un indirizzo cercapersone:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**has_netsend**|**int**|Specifica se per l'operatore è stata specificata la notifica tramite Net Send.<br /><br /> **1** = Sì<br /><br /> **0** = No|  
  
## <a name="remarks"></a>Osservazioni  
 È necessario eseguire questa stored procedure dal **msdb** database.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa stored procedure, è necessario che gli utenti siano membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-alerts-for-a-specific-operator"></a>A. Visualizzazione di un elenco di avvisi per un operatore specifico  
 Nell'esempio seguente vengono restituiti tutti gli avvisi per i quali `François Ajenstat` riceve una notifica.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_notification   
    @object_type = N'ALERTS',  
    @name = N'François Ajenstat',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
### <a name="b-listing-operators-for-a-specific-alert"></a>B. Visualizzazione di un elenco di operatori per un avviso specifico  
 Nell'esempio seguente vengono restituiti tutti gli operatori che ricevono una notifica per l'avviso `Test Alert`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_notification  
    @object_type = N'OPERATORS',  
    @name = N'Test Alert',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
