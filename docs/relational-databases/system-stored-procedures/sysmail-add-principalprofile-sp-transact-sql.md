---
title: sysmail_add_principalprofile_sp (Transact-SQL) | Documenti Microsoft
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
- sysmail_add_principalprofile_sp_TSQL
- sysmail_add_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_principalprofile_sp
ms.assetid: b2a0b313-abb9-4c23-8511-db77ca8172b3
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d5eda99649aa5f27cc199a2a4676c0f79d36c80
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33261490"
---
# <a name="sysmailaddprincipalprofilesp-transact-sql"></a>sysmail_add_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Concede l'autorizzazione per un utente o ruolo del database per l'utilizzo di un profilo di Posta elettronica database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_add_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
    [ , [ @is_default ] = 'is_default' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@principal_id** =] *principal_id*  
 L'ID dell'utente del database o del ruolo nel **msdb** database per l'associazione. *principal_id* viene **int**, con un valore predefinito è NULL. Entrambi *principal_id* o *principal_name* deve essere specificato. Oggetto *principal_id* di **0** rende questo profilo di un profilo pubblico e concedere l'accesso a tutte le entità nel database.  
  
 [ **@principal_name** =] **'***principal_name***'**  
 Il nome dell'utente del database o del ruolo nel **msdb** database per l'associazione. *principal_name* viene **sysname**, con un valore predefinito è NULL. Entrambi *principal_id* o *principal_name* deve essere specificato. Oggetto *principal_name* di **'public'** rende questo profilo di un profilo pubblico e concedere l'accesso a tutte le entità nel database.  
  
 [ **@profile_id** = ] *profile_id*  
 ID del profilo per l'associazione. *profile_id* viene **int**, con un valore predefinito è NULL. Entrambi *profile_id* o *profile_name* deve essere specificato.  
  
 [ **@profile_name** =] **'***profile_name***'**  
 Nome del profilo per l'associazione. *profile_name* viene **sysname**, non prevede alcun valore predefinito. Entrambi *profile_id* o *profile_name* deve essere specificato.  
  
 [ **@is_default** =] *is_default*  
 Indica se il profilo è il profilo predefinito per l'entità. A un'entità può essere associato un solo profilo predefinito. *is_default* viene **bit**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Per rendere pubblico un profilo, specificare un **@principal_id** di **0** o **@principal_name** di **pubblica**. Un profilo pubblico è disponibile a tutti gli utenti di **msdb** database, anche se gli utenti devono inoltre essere un membro di **DatabaseMailUserRole** eseguire **sp_send_dbmail**.  
  
 A un utente del database può essere associato un solo profilo predefinito. Quando **@is_default** è '**1**' e l'utente è già associata a uno o più profili, il profilo specificato diventa il profilo predefinito per l'utente. Il profilo che in precedenza era il profilo predefinito è tuttora associato all'utente, ma non è più il profilo predefinito.  
  
 Quando **@is_default** è '**0**' e non esistono altre associazioni, la stored procedure restituisce un errore.  
  
 La stored procedure **sysmail_add_principalprofile_sp** nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 **A. Creazione di un'associazione, l'impostazione del profilo predefinito**  
  
 L'esempio seguente crea un'associazione tra il profilo denominato `AdventureWorks Administrator Profile` e **msdb** utente del database `ApplicationUser`. Il profilo è il profilo predefinito per l'utente.  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @is_default = 1 ;  
```  
  
 **B. Impostazione di un profilo come profilo pubblico predefinito**  
  
 Nell'esempio seguente viene impostato il profilo `AdventureWorks Public Profile` il profilo pubblico predefinito per gli utenti di **msdb** database.  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'AdventureWorks Public Profile',  
    @is_default = 1 ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Oggetti di configurazione di posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
