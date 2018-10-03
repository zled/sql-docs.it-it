---
title: sp_add_notification (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_notification_TSQL
- sp_add_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_notification
ms.assetid: 0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bb19049185ab79178213b1dc042a1c23f8978374
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704599"
---
# <a name="spaddnotification-transact-sql"></a>sp_add_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta una notifica per un avviso.  
  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_notification [ @alert_name = ] 'alert' ,   
    [ @operator_name = ] 'operator' ,   
    [ @notification_method = ] notification_method  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@alert_name=** ] **'***avviso***'**  
 Avviso da notificare. *avviso* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@operator_name=** ] **'***operatore***'**  
 Operatore a cui inviare una notifica quando viene generato l'avviso. *operatore* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@notification_method=** ] *notification_method*  
 Metodo adottato per l'invio della notifica all'operatore. *notification_method* viene **tinyint**, non prevede alcun valore predefinito. *notification_method* può essere uno o più dei valori seguenti combinati con un' **OR** operatore logico.  
  
|valore|Description|  
|-----------|-----------------|  
|**1**|Posta elettronica|  
|**2**|Cercapersone|  
|**4**|**net send**|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="remarks"></a>Note  
 **sp_add_notification** deve essere eseguita la **msdb** database.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] include un semplice strumento grafico per la gestione del sistema di avvisi. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] è lo strumento consigliato per la configurazione di un'infrastruttura di avvisi.  
  
 Per inviare una notifica in risposta a un avviso, è innanzitutto necessario configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per l'invio di messaggi.  
  
 Gli eventuali errori che si verificano durante l'invio di un messaggio di posta elettronica o di una notifica su cercapersone vengono registrati nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_add_notification**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aggiunta una notifica di posta elettronica per l'avviso specificato (`Test Alert`).  
  
> **Nota:** in questo esempio si presuppone che `Test Alert` esiste già e che `François Ajenstat` è un nome di operatore valido.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_notification  
 @alert_name = N'Test Alert',  
 @operator_name = N'François Ajenstat',  
 @notification_method = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
