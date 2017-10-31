---
title: ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_AUDIT_SPECIFICATION_TSQL
- ALTER DATABASE AUDIT SPECIFICATION
- ALTER_DATABASE_AUDIT_TSQL
- ALTER DATABASE AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER DATABASE AUDIT SPECIFICATION statement
ms.assetid: 85f4e7e6-a330-4de0-9048-64f386ccc314
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06d58a9ecce3175e021e7db484aeadbe41f3b372
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-audit-specification-transact-sql"></a>ALTER DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica un oggetto specifica controllo database utilizzando la funzionalità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. Per altre informazioni, vedere [SQL Server Audit &#40;Motore di database&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER DATABASE AUDIT SPECIFICATION audit_specification_name  
{  
    [ FOR SERVER AUDIT audit_name ]  
    [ { { ADD | DROP } (   
           { <audit_action_specification> | audit_action_group_name }   
                )   
      } [, ...n] ]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
<audit_action_specification>::=  
{  
      <action_specification>[ ,...n ] ON [ class :: ] securable   
     BY principal [ ,...n ]   
}  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *audit_specification_name*  
 Nome della specifica del controllo.  
  
 *audit_name*  
 Nome del controllo al quale viene applicata questa specifica.  
  
 *audit_action_specification*  
 Nome di una o più azioni controllabili a livello di database. Per un elenco di gruppi di azioni di controllo, vedere [gruppi di azioni di controllo di SQL Server e le azioni](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
 *audit_action_group_name*  
 Nome di uno o più gruppi di azioni controllabili a livello di database. Per un elenco di gruppi di azioni di controllo, vedere [gruppi di azioni di controllo di SQL Server e le azioni](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
 *classe*  
 Nome della classe nell'entità a sicurezza diretta, se applicabile.  
  
 *entità a protezione diretta*  
 Tabella, vista oppure altro oggetto a sicurezza diretta nel database cui applicare l'azione di controllo oppure il gruppo di azioni di controllo. Per altre informazioni, vedere [Entità a protezione diretta](../../relational-databases/security/securables.md).  
  
 *colonna*  
 Nome della colonna nell'entità a sicurezza diretta, se applicabile.  
  
 *entità*  
 Nome di entità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cui applicare l'azione di controllo oppure il gruppo di azioni di controllo. Per ulteriori informazioni, vedere [entità &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/principals-database-engine.md).  
  
 CON **(** STATO  **=**  {ON | OFF} **)**  
 Abilita o disabilita la raccolta di record mediante il controllo per questa specifica del controllo. Le modifiche relative allo stato della specifica di controllo devono essere apportate all'esterno di una transazione utente e non possono contenere altre modifiche nella stessa istruzione in presenza di una transizione da ON a OFF.  
  
## <a name="remarks"></a>Osservazioni  
 Le specifiche del controllo del database sono oggetti non a sicurezza diretta che risiedono in un database specifico. È necessario impostare lo stato di una specifica del controllo sull'opzione OFF per apportare modifiche a un database specifica del controllo. Se ALTER DATABASE AUDIT SPECIFICATION viene eseguita quando un controllo è abilitato con qualsiasi altra opzione diversa da STATE=OFF, verrà visualizzato un messaggio di errore. Per altre informazioni, vedere [tempdb Database](../../relational-databases/databases/tempdb-database.md).  
  
## <a name="permissions"></a>Permissions  
 Gli utenti che dispongono dell'autorizzazione ALTER ANY DATABASE AUDIT possono modificare specifiche del controllo del database e associarle a qualsiasi controllo.  
  
 Dopo la creazione di una specifica del controllo del database, possono essere visualizzato dalle entità con il SERVER di controllo, o le autorizzazioni ALTER ANY DATABASE AUDIT, account sysadmin oppure dalle entità che possono accedere esplicitamente al controllo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene modificata una specifica del controllo del database denominata `HIPPA_Audit_DB_Specification` che controlla le istruzioni `SELECT` mediante l'utente `dbo`, per un oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit denominato `HIPPA_Audit`.  
  
```  
ALTER DATABASE AUDIT SPECIFICATION HIPPA_Audit_DB_Specification  
FOR SERVER AUDIT HIPPA_Audit  
    ADD (SELECT  
         ON OBJECT::dbo.Table1  
         BY dbo)  
    WITH (STATE = ON);  
GO  
```  
  
 Per un esempio completo su come creare un controllo, vedere [SQL Server Audit &#40; motore di Database &#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREARE DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [AUTORIZZAZIONE ALTER &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys. fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys. server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys. server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [Sys. server_audit_specification_details – &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [Sys. database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Creazione di un controllo del server e di una specifica del controllo del server](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

