---
title: sysmail_add_profile_sp (Transact-SQL) | Microsoft Docs
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
- sysmail_add_profile_sp_TSQL
- sysmail_add_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profile_sp
ms.assetid: a828e55c-633a-41cf-9769-a0698b446e6c
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 16091d14ba4971ae8e07633dd111dd5f5a2facde
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260224"
---
# <a name="sysmailaddprofilesp-transact-sql"></a>sysmail_add_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un nuovo profilo di Posta elettronica database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_add_profile_sp [ @profile_name = ] 'profile_name'  
    [ , [ @description = ] 'description' ]  
    [ , [ @profile_id = ] new_profile_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@profile_name** =] **'***profile_name***'**  
 Nome del nuovo profilo. *profile_name* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@description** =] **'***descrizione***'**  
 Descrizione facoltativa del nuovo profilo. *Descrizione* viene **nvarchar(256)**, non prevede alcun valore predefinito.  
  
 [ **@profile_id** = ] *new_profile_id***OUTPUT**  
 Restituisce l'ID del nuovo profilo. *new_profile_id* viene **int**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Un profilo di Posta elettronica database include qualsiasi numero di account di Posta elettronica database. Le stored procedure di Posta elettronica database possono far riferimento a un profilo attraverso il nome del profilo o l'ID del profilo generato da questa procedura. Per ulteriori informazioni sull'aggiunta di un account a un profilo, vedere [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md).  
  
 Il nome del profilo e la descrizione può essere modificati con la stored procedure **sysmail_update_profile_sp**, mentre l'id del profilo rimane costante per tutta la durata del profilo.  
  
 Il nome del profilo deve essere univoco per Microsoft [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. In caso contrario, la stored procedure restituisce un errore.  
  
 La stored procedure **sysmail_add_profile_sp** nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 **A. Creazione di un nuovo profilo**  
  
 Nell'esempio seguente viene creato un nuovo profilo di Posta elettronica database denominato `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.' ;  
```  
  
 **B. Creazione di un nuovo profilo e salvataggio dell'id del profilo in una variabile**  
  
 Nell'esempio seguente viene creato un nuovo profilo di Posta elettronica database denominato `AdventureWorks Administrator`. Nell'esempio il numero di ID del profilo viene archiviato nella variabile `@profileId` e viene restituito un set di risultati contenente il numero di ID del nuovo profilo.  
  
```  
DECLARE @profileId INT ;  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.',  
       @profile_id = @profileId OUTPUT ;  
  
SELECT @profileId ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Creare un Account di posta elettronica Database](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Oggetti di configurazione di posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
