---
title: sysmail_help_principalprofile_sp (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/02/2016
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
- sysmail_help_principalprofile_sp_TSQL
- sysmail_help_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_principalprofile_sp
ms.assetid: 0cfd6464-09c7-4f03-9d25-58001c096a9e
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6a03dba8211a2841be94725565edaed3be61ef78
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysmailhelpprincipalprofilesp-transact-sql"></a>sysmail_help_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un elenco di informazioni sulle associazioni tra i profili di Posta elettronica database e le entità di database.  
  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_help_principalprofile_sp [ {   [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ]  
    [ [ , ] {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@principal_id=** ] *principal_id*  
 È l'ID dell'utente del database o del ruolo nel **msdb** database per l'associazione all'elenco. *principal_id* viene **int**, con un valore predefinito è NULL. Entrambi *principal_id* o *principal_name* può essere specificato.  
  
 [  **@principal_name=** ] **'***principal_name***'**  
 È il nome dell'utente del database o del ruolo nel **msdb** database per l'associazione all'elenco. *principal_name* viene **sysname**, con un valore predefinito è NULL. Entrambi *principal_id* o *principal_name* può essere specificato.  
  
 [ **@profile_id=** ] *profile_id*  
 ID del profilo per l'associazione da includere nell'elenco. *profile_id* viene **int**, con un valore predefinito è NULL. Entrambi *profile_id* o *profile_name* può essere specificato.  
  
 [  **@profile_name=** ] **'***profile_name***'**  
 Nome del profilo per l'associazione da includere nell'elenco. *profile_name* viene **sysname**, con un valore predefinito è NULL. Entrambi *profile_id* o *profile_name* può essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Restituisce un set di risultati contenente le colonne elencate nella tabella seguente.  
  
||||  
|-|-|-|  
|Nome colonna|Tipo di dati|Description|  
|**principal_id**|**int**|ID dell'utente del database.|  
|**principal_name**|**sysname**|Nome dell'utente del database.|  
|**profile_id**|**int**|Numero ID del profilo di Posta elettronica database.|  
|**profile_name**|**sysname**|Nome del profilo di Posta elettronica database.|  
|**is_default**|**bit**|Flag che indica se il profilo è il profilo predefinito per l'utente.|  
  
## <a name="remarks"></a>Osservazioni  
 Se **sysmail_help_principalprofile_sp** viene richiamata senza parametri, il set di risultati restituito vengono elencate tutte le associazioni nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Negli altri casi il set di risultati conterrà le informazioni relative alle associazioni che corrispondono ai parametri specificati. Se ad esempio si specifica il nome di un profilo, la procedura elenca tutte le associazioni per tale profilo.  
  
 **sysmail_help_principalprofile_sp** è il **msdb** database ed è di proprietà il **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-information-for-a-specific-association"></a>A. Visualizzazione delle informazioni relative a un'associazione specifica  
 Nell'esempio seguente viene illustrato come visualizzare le informazioni relative a tutte le associazioni tra il profilo `AdventureWorks Administrator` e l'entità `ApplicationLogin` nel database `msdb`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp  
    @principal_name = 'danw',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Set di risultati di esempio, riformattato in base alla lunghezza di riga:  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
5            danw               9           AdventureWorks Administrator   1  
```  
  
### <a name="b-listing-information-for-all-associations"></a>B. Visualizzazione delle informazioni relative a tutte le associazioni  
 Nell'esempio seguente viene illustrato come visualizzare le informazioni relative a tutte le associazioni nell'istanza.  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp ;  
```  
  
 Set di risultati di esempio, riformattato in base alla lunghezza di riga:  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
6            terrid             3           Product Update Profile         1  
5            danw               9           AdventureWorks Administrator   1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
