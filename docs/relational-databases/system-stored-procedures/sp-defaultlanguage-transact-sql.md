---
title: sp_defaultlanguage (Transact-SQL) | Documenti Microsoft
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
- sp_defaultlanguage
- sp_defaultlanguage_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_defaultlanguage
ms.assetid: 908d01cc-e704-45d9-9e85-d2df6da3e6f5
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dfd63d6dddf3cc553ffee62dffbacff891d1991c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spdefaultlanguage-transact-sql"></a>sp_defaultlanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica la lingua predefinita di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_defaultlanguage [ @loginame = ] 'login'   
     [ , [ @language = ] 'language' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@loginame =** ] **'***accesso***'**  
 Nome dell'account di accesso. *account di accesso* è **sysname**, non prevede alcun valore predefinito. *account di accesso* può essere un oggetto esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso o un utente di Windows o un gruppo.  
  
 [  **@language =** ] **'***language***'**  
 Lingua predefinita dell'account di accesso. *lingua* è **sysname**, con un valore predefinito è NULL. *lingua* deve essere una lingua valida nel server. Se *language* non viene specificato, *language* è impostato per la lingua predefinita del server lingua predefinita è definita dal **sp_configure** variabile di configurazione **lingua predefinita**. Se si modifica la lingua predefinita del server non viene modificata la lingua predefinita degli account di accesso esistenti.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_defaultlanguage** chiama ALTER LOGIN, che supporta opzioni aggiuntive. Per informazioni sulla modifica delle impostazioni predefinite di altri account di accesso, vedere [ALTER LOGIN &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-login-transact-sql.md).  
  
 Per modificare la lingua della sessione corrente, eseguire l'istruzione SET LANGUAGE. Utilizzo di @@LANGUAGE funzione per visualizzare l'impostazione della lingua corrente.  
  
 Se la lingua predefinita di un account di accesso viene eliminata dal server, l'account di accesso acquisisce la lingua predefinita del server. **sp_defaultlanguage** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
 Informazioni sulle lingue installate nel server sono visibili nella **Sys. syslanguages** vista del catalogo.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY LOGIN.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'istruzione `ALTER LOGIN` viene utilizzata per modificare la lingua predefinita dell'account di accesso `Fathima` e impostarla sull'arabo. Questo è il metodo consigliato.  
  
```  
ALTER LOGIN Fathima WITH DEFAULT_LANGUAGE = Arabic;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [Sys. syslanguages &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
