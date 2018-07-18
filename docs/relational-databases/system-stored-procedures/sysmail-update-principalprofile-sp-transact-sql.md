---
title: sysmail_update_principalprofile_sp (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_update_principalprofile_sp
- sysmail_update_principalprofile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_principalprofile_sp
ms.assetid: 9fe96e9a-4758-4e4a-baee-3e1217c4426c
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a86fc4775ee1096d72451ace855bb19a1094c3c5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysmailupdateprincipalprofilesp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiorna le informazioni per un'associazione tra un'entità e un profilo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_update_principalprofile_sp { @principal_id = principal_id | @principal_name = 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    [ @is_default = ] 'is_default'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@principal_id** =] *principal_id*  
 L'ID dell'utente del database o del ruolo nel **msdb** database per l'associazione da modificare. *principal_id* viene **int**, con un valore predefinito è NULL. Entrambi *principal_id* o *principal_name* deve essere specificato.  
  
 [ **@principal_name** =] **'***principal_name***'**  
 Il nome dell'utente del database o del ruolo nel **msdb** database per l'associazione da aggiornare. *principal_name* viene **sysname**, con un valore predefinito è NULL. Entrambi *principal_id* o *principal_name* può essere specificato.  
  
 [ **@profile_id** = ] *profile_id*  
 ID del profilo per l'associazione da modificare. *profile_id* viene **int**, con un valore predefinito è NULL. Entrambi *profile_id* o *profile_name* deve essere specificato.  
  
 [ **@profile_name** =] **'***profile_name***'**  
 Nome del profilo per l'associazione da modificare. *profile_name* viene **sysname**, con un valore predefinito è NULL. Entrambi *profile_id* o *profile_name* deve essere specificato.  
  
 [ **@is_default** =] **'***is_default***'**  
 Specifica se il profilo è il profilo predefinito per l'utente del database. A un utente del database può essere associato un solo profilo predefinito. *is_default* viene **bit**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Questa stored procedure consente di modificare il profilo predefinito per l'utente del database. A un utente del database può essere associato un solo profilo privato predefinito.  
  
 Quando il nome dell'entità per l'associazione è **pubblica** o l'id dell'entità per l'associazione è **0**, questa stored procedure modifica il profilo pubblico. È possibile associare un solo profilo pubblico predefinito.  
  
 Quando **@is_default** è '**1**' e l'entità è associata a più di un profilo, il profilo specificato diventa il profilo predefinito per l'entità. Il profilo che in precedenza era il profilo predefinito è tuttora associato all'entità, ma non è più il profilo predefinito.  
  
 La stored procedure **sysmail_update_principalprofile_sp** nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 **A. L'impostazione di un profilo come profilo pubblico predefinito per un database**  
  
 Nell'esempio seguente imposta il profilo `General Use Profile` per il profilo pubblico predefinito per gli utenti di **msdb** database.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'General Use Profile',  
    @is_default = '1';  
```  
  
 **B. Impostazione di un profilo come profilo privato predefinito per un utente**  
  
 Nell'esempio seguente imposta il profilo `AdventureWorks Administrator` profilo predefinito per l'entità `ApplicationUser` nel **msdb** database. Il profilo deve essere già associato all'entità. Il profilo che in precedenza era il profilo predefinito è tuttora associato all'entità, ma non è più il profilo predefinito.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator',  
    @is_default = '1' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Oggetti di configurazione di posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
