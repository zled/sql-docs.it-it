---
title: sp_helpremotelogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpremotelogin_TSQL
- sp_helpremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpremotelogin
ms.assetid: 93f50869-2627-4642-899f-8f626f8833f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1181ab030078b0f7ba61a72448991ed677e22d76
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704805"
---
# <a name="sphelpremotelogin-transact-sql"></a>sp_helpremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sugli account di accesso remoti per un determinato server remoto o per tutti i server remoti definiti nel server locale.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilizzare i server collegati e le stored procedure per i server collegati in alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpremotelogin [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @remoteserver **=** ] **'***remoteserver***'**  
 Server remoto per il quale vengono restituite informazioni sugli account di accesso remoti. *remoteserver* viene **sysname**, con un valore predefinito è NULL. Se *remoteserver* viene omesso, vengono restituite informazioni su tutti i server remoti definiti nel server locale.  
  
 [ @remotename **=** ] **'***remote_name***'**  
 Account di accesso remoto specifico nel server remoto. *remote_name* viene **sysname**, con un valore predefinito è NULL. Se *remote_name* non viene specificato, informazioni su tutti gli utenti remoti definiti per *remoteserver* viene restituito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|server|**sysname**|Nome di un server remoto definito nel server locale.|  
|local_user_name|**sysname**|Account di accesso del server locale a cui è stato eseguito il mapping degli account di accesso remoti del server.|  
|remote_user_name|**sysname**|Account di accesso nel server remoto che esegue il mapping a local_user_name.|  
|opzioni|**sysname**|Trusted = Quando l'account di accesso remoto si connette al server locale dal server remoto, non viene richiesta alcuna password.<br /><br /> Untrusted (o vuoto) = Quando l'account di accesso remoto si connette al server locale dal server remoto, viene sempre richiesta una password.|  
  
## <a name="remarks"></a>Note  
 Per elencare i nomi dei server remoti definiti nel server locale, utilizzare sp_helpserver.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni non vengono controllate.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-reporting-help-on-a-single-server"></a>A. Visualizzazione di informazioni su un solo server  
 Nell'esempio seguente vengono visualizzate informazioni su tutti gli utenti remoti nel server remoto `Accounts`.  
  
```  
EXEC sp_helpremotelogin 'Accounts';  
```  
  
### <a name="b-reporting-help-on-all-remote-users"></a>B. Visualizzazione di informazioni su tutti gli utenti remoti  
 Nell'esempio seguente vengono visualizzate informazioni su tutti gli utenti remoti disponibili in tutti i server remoti noti al server locale.  
  
```  
EXEC sp_helpremotelogin;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
