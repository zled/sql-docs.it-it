---
title: sysmail_delete_profileaccount_sp (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- sysmail_delete_profileaccount_sp
- sysmail_delete_profileaccount_sp_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmail_delete_profileaccount_sp
ms.assetid: b58d06f2-d6c9-4c8e-95bd-027c50f4621a
caps.latest.revision: "45"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67c1f60356209a9f39d0ac902fea41b5f6ec2f2a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysmaildeleteprofileaccountsp-transact-sql"></a>sysmail_delete_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un account da un profilo di Posta elettronica database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_delete_profileaccount_sp  {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    {   [ @account_id = ] account_id | [ @account_name = ] 'account_name' }  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@profile_id**  =] *profile_id*  
 ID del profilo da eliminare. *profile_id* è **int**, con un valore predefinito è NULL. Entrambi i *profile_id* o *profile_name* può essere specificato.  
  
 [  **@profile_name**  =] **'***profile_name***'**  
 Nome del profilo da eliminare. *profile_name* è **sysname**, con un valore predefinito è NULL. Entrambi i *profile_id* o *profile_name* può essere specificato.  
  
 [  **@account_id**  =] *account_id*  
 ID dell'account da eliminare. *account_id* è **int**, con un valore predefinito è NULL. Entrambi i *account_id* o *account_name* può essere specificato.  
  
 [  **@account_name**  =] **'***account_name***'**  
 Nome dell'account da eliminare. *account_name* è **sysname**, con un valore predefinito è NULL. Entrambi i *account_id* o *account_name* può essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Restituisce un errore se l'account specificato non è associato al profilo.  
  
 Quando viene specificato un account senza specificare un profilo, questa stored procedure rimuove l'account specificato da tutti i profili. Se si sta preparando l'arresto di un server SMTP già esistente, ad esempio, verranno rimossi gli account che utilizzano il server SMTP da tutti i profili, e non ogni singolo account da ogni profilo.  
  
 Quando viene specificato un profilo senza specificare un account, questa stored procedure rimuove tutti gli account dal profilo specificato. Se si modificano i server SMTP utilizzati da un profilo, ad esempio, potrebbe risultare utile rimuovere tutti gli account dal profilo e quindi aggiungere nuovi account, se necessario.  
  
 La stored procedure **sysmail_delete_profileaccount_sp** nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'account `Audit Account` viene rimosso dal profilo `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator',  
    @account_name = 'Audit Account' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Creare un Account di posta elettronica Database](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Oggetti di configurazione di posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Posta elettronica database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
