---
title: sp_change_users_login (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/13/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_change_users_login
- sp_change_users_login_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_users_login
ms.assetid: 1554b39f-274b-4ef8-898e-9e246b474333
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 207272f7644ab39055b7c6bb330faf6053353601
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spchangeuserslogin-transact-sql"></a>sp_change_users_login (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene eseguito il mapping di un utente di database esistente a un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [ALTER USER](../../t-sql/statements/alter-user-transact-sql.md) invece.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_change_users_login [ @Action = ] 'action'   
    [ , [ @UserNamePattern = ] 'user' ]   
    [ , [ @LoginName = ] 'login' ]   
    [ , [ @Password = ] 'password' ]  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @Action=] '*azione*'  
 Descrive l'azione che deve essere eseguita dalla procedura. *azione* è **varchar (10)**. *azione* può avere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Auto_Fix**|Collega una voce utente presente nella vista del catalogo di sistema sys.database_principals del database corrente a un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con lo stesso nome. Se non esiste un account di accesso con lo stesso nome, ne verrà creato uno. Esaminare il risultato di **Auto_Fix** istruzione per verificare che il collegamento corretto è stato stabilito. Evitare di utilizzare **Auto_Fix** in situazioni di protezione.<br /><br /> Quando si utilizza **Auto_Fix**, è necessario specificare *utente* e *password* se l'account di accesso non esiste già, in caso contrario è necessario specificare *utente*ma *password* verrà ignorato. *account di accesso* deve essere NULL. *utente* deve essere un utente valido nel database corrente. Non è possibile eseguire il mapping dell'account di accesso a un altro utente.|  
|**Report**|Elenca gli utenti e gli ID di sicurezza (SID) corrispondenti disponibili nel database corrente e non collegati ad alcun account di accesso. *utente*, *accesso*, e *password* deve essere NULL o non specificato.<br /><br /> Per sostituire l'opzione di report con una query utilizzando le tabelle di sistema, confrontare le voci in **Sys. server_prinicpals** con le voci in **Sys. database_principals**.|  
|**Update_One**|Collega l'oggetto specificato *utente* nel database corrente a un oggetto esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *accesso*. *utente* e *accesso* deve essere specificato. *password* deve essere NULL o non specificato.|  
  
 [ @UserNamePattern=] '*utente*'  
 Nome di un utente nel database corrente. *utente* è **sysname**, con un valore predefinito è NULL.  
  
 [ @LoginName=] '*accesso*'  
 Nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *account di accesso* è **sysname**, con un valore predefinito è NULL.  
  
 [ @Password=] '*password*'  
 Password assegnata a un nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso creato specificando **Auto_Fix**. Se un account di accesso corrispondente esiste già, l'utente e account di accesso viene eseguito il mapping e *password* viene ignorato. Se un account di accesso corrispondente non esiste, sp_change_users_login crea un nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso e assegna *password* come password per il nuovo account di accesso. *password* è **sysname**, e non deve essere NULL.  
  
> **IMPORTANTE** Utilizzare sempre un [Password complessa.](../../relational-databases/security/strong-passwords.md)
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|UserName|**sysname**|Nome dell'utente del database.|  
|UserSID|**varbinary (85)**|ID di sicurezza (SID) dell'utente.|  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare sp_change_users_login per collegare un utente di database nel database corrente a un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se l'account di accesso di un utente è stato modificato, utilizzare sp_change_users_login per collegare l'utente al nuovo account di accesso senza perdere le autorizzazioni corrispondenti. Il nuovo *accesso* non può essere l'amministratore di sistema e *utente*non può essere dbo, guest, un utente INFORMATION_SCHEMA.  
  
 La stored procedure sp_change_users_login non può essere utilizzata per eseguire il mapping degli utenti del database a entità, certificati o chiavi asimmetriche a livello di Windows.  
  
 Non è possibile utilizzare sp_change_users_login con un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creato da un'entità di Windows o con un utente creato mediante CREATE USER WITHOUT LOGIN.  
  
 La stored procedure sp_change_users_login non può essere eseguita in una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al ruolo predefinito del database db_owner. Solo i membri del ruolo predefinito del server sysadmin possono specificare il **Auto_Fix** opzione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-showing-a-report-of-the-current-user-to-login-mappings"></a>A. Visualizzazione di un report dei mapping tra utente corrente e account di accesso  
 Nell'esempio seguente viene creato un report che include gli utenti del database corrente e i relativi ID di sicurezza (SID).  
  
```  
EXEC sp_change_users_login 'Report';  
```  
  
### <a name="b-mapping-a-database-user-to-a-new-sql-server-login"></a>B. Mapping tra un utente del database e un nuovo account di accesso di SQL Server  
 Nell'esempio seguente un utente del database viene associato a un nuovo account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'utente del database `MB-Sales`, sul quale inizialmente viene eseguito il mapping a un account di accesso diverso, viene eseguito il mapping all'account di accesso `MaryB`.  
  
```  
--Create the new login.  
CREATE LOGIN MaryB WITH PASSWORD = '982734snfdHHkjj3';  
GO  
--Map database user MB-Sales to login MaryB.  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Update_One', 'MB-Sales', 'MaryB';  
GO  
```  
  
### <a name="c-automatically-mapping-a-user-to-a-login-creating-a-new-login-if-it-is-required"></a>C. Mapping automatico tra un utente e un account di accesso e creazione di un nuovo account di accesso se necessario  
 Nell'esempio seguente viene illustrato come utilizzare l'opzione `Auto_Fix` per eseguire il mapping tra un utente esistente e un account di accesso con lo stesso nome oppure per creare l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] denominato `Mary` associato alla password `B3r12-3x$098f6` se l'account di accesso `Mary` non esiste.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Auto_Fix', 'Mary', NULL, 'B3r12-3x$098f6';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_helplogins &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
