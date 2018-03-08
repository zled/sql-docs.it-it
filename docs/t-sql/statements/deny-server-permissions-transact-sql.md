---
title: DENY-autorizzazioni per Server (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], servers
- denying permissions [SQL Server], servers
- servers [SQL Server], permissions
- DENY statement, servers
ms.assetid: 68d6b2a9-c36f-465a-9cd2-01d43a667e99
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5cabf58a9136324602af30f9b8fa6b85e3ee346
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="deny-server-permissions-transact-sql"></a>DENY - autorizzazioni per server (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Nega le autorizzazioni per un server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DENY permission [ ,...n ]   
    TO <grantee_principal> [ ,...n ]  
    [ CASCADE ]  
    [ AS <grantor_principal> ]   
  
<grantee_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
  
<grantor_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Specifica un'autorizzazione che può essere negata per un server. Per un elenco delle autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 CASCADE  
 Indica che l'autorizzazione negata viene negata anche ad altre entità alle quali è stata concessa da questa entità.  
  
 PER \<server_principal >  
 Specifica l'entità a cui viene negata l'autorizzazione.  
  
 AS \<grantor_principal >  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di negare l'autorizzazione.  
  
 *SQL_Server_login*  
 Specifica un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_mapped_to_Windows_login*  
 Specifica un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul quale viene eseguito il mapping a un utente di Windows.  
  
 *SQL_Server_login_mapped_to_Windows_group*  
 Specifica un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul quale viene eseguito il mapping a un gruppo di Windows.  
  
 *SQL_Server_login_mapped_to_certificate*  
 Specifica un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di cui è stato eseguito il mapping a un certificato.  
  
 *SQL_Server_login_mapped_to_asymmetric_key*  
 Specifica un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di cui è stato eseguito il mapping a una chiave asimmetrica.  
  
 *server_role*  
 Specifica un ruolo del server.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile negare autorizzazioni nell'ambito del server solo se il database corrente è il database master.  
  
 Informazioni sulle autorizzazioni del server possono essere visualizzate nel [server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) vista del catalogo e le informazioni sulle entità server possono essere visualizzati nel [Sys. server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vista del catalogo. Informazioni sull'appartenenza ai ruoli del server possono essere visualizzate nel [server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md) vista del catalogo.  
  
 Un server rappresenta il livello più alto nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile negare per un server.  
  
|Autorizzazione del server|Autorizzazione del server in cui è inclusa|  
|-----------------------|----------------------------------|  
|ADMINISTER BULK OPERATIONS|CONTROL SERVER|  
|ALTER ANY AVAILABILITY GROUP<br /><br /> **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|ALTER ANY CONNECTION|CONTROL SERVER|  
|ALTER ANY CREDENTIAL|CONTROL SERVER|  
|ALTER ANY DATABASE|CONTROL SERVER|  
|ALTER ANY ENDPOINT|CONTROL SERVER|  
|ALTER ANY EVENT NOTIFICATION|CONTROL SERVER|  
|ALTER ANY EVENT SESSION|CONTROL SERVER|  
|ALTER ANY LINKED SERVER|CONTROL SERVER|  
|ALTER ANY LOGIN|CONTROL SERVER|  
|ALTER ANY SERVER AUDIT|CONTROL SERVER|  
|ALTER ANY SERVER ROLE<br /><br /> **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|ALTER RESOURCES|CONTROL SERVER|  
|ALTER SERVER STATE|CONTROL SERVER|  
|ALTER SETTINGS|CONTROL SERVER|  
|ALTER TRACE|CONTROL SERVER|  
|AUTHENTICATE SERVER|CONTROL SERVER|  
|CONNECT ANY DATABASE<br /><br /> **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|CONNECT SQL|CONTROL SERVER|  
|CONTROL SERVER|CONTROL SERVER|  
|CREATE ANY DATABASE|ALTER ANY DATABASE|  
|CREATE AVAILABILITY GROUP<br /><br /> **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|ALTER ANY AVAILABILITY GROUP|  
|CREATE DDL EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|CREATE ENDPOINT|ALTER ANY ENDPOINT|  
|CREATE SERVER ROLE<br /><br /> **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|ALTER ANY SERVER ROLE|  
|CREATE TRACE EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|EXTERNAL ACCESS ASSEMBLY|CONTROL SERVER|  
|IMPERSONATE ANY LOGIN<br /><br /> **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|SELECT ALL USER SECURABLES<br /><br /> **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|SHUTDOWN|CONTROL SERVER|  
|UNSAFE ASSEMBLY|CONTROL SERVER|  
|VIEW ANY DATABASE|VIEW ANY DEFINITION|  
|VIEW ANY DEFINITION|CONTROL SERVER|  
|VIEW SERVER STATE|ALTER SERVER STATE|  
  
## <a name="remarks"></a>Osservazioni  
 In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] sono state aggiunte le tre autorizzazioni server riportate di seguito.  
  
 **La connessione a qualsiasi DATABASE** autorizzazione  
 GRANT **CONNECT ANY DATABASE** a un account di accesso che deve connettersi a tutti i database attualmente esistenti e ai nuovi database che potrebbero essere creati in futuro. Non concede alcuna autorizzazione nei database oltre la connessione. Combinare con **SELECT ALL USER SECURABLES** o **VIEW SERVER STATE** per consentire un processo di controllo visualizzare tutti i dati o tutti gli stati di database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **RAPPRESENTARE qualsiasi account di accesso** autorizzazione  
 Quando viene concessa, consente a un processo di livello intermedio di rappresentare l'account dei client a cui ci si connette, quando si connette ai database. Quando viene negata, è possibile che a un account di accesso con privilegi elevati venga impedito di rappresentare altri account di accesso. Ad esempio, un account di accesso con **CONTROL SERVER** autorizzazione può essere impedita di rappresentare altri account di accesso.  
  
 **Selezionare ALL USER SECURABLES** autorizzazione  
 Quando viene concessa, un account di accesso, ad esempio un revisore, può visualizzare i dati in tutti i database a cui l'utente può connettersi. Quando negata, impedisce l'accesso agli oggetti a meno che non si trovano nel **sys** dello schema.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL SERVER o la proprietà dell'entità a sicurezza diretta. Se si utilizza la clausola AS, l'entità specificata deve essere proprietaria dell'entità a sicurezza diretta per cui vengono negate le autorizzazioni.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-denying-connect-sql-permission-to-a-sql-server-login-and-principals-to-which-the-login-has-regranted-it"></a>A. Negazione dell'autorizzazione CONNECT SQL a un account di accesso di SQL Server e alle entità a cui l'account di accesso ha concesso tale autorizzazione  
 Nell'esempio seguente viene negata l'autorizzazione `CONNECT SQL` all'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Annika` e a tutte le entità a cui tale account di accesso ha concesso l'autorizzazione.  
  
```  
USE master;  
DENY CONNECT SQL TO Annika CASCADE;  
GO  
```  
  
### <a name="b-denying-create-endpoint-permission-to-a-sql-server-login-using-the-as-option"></a>B. Negazione dell'autorizzazione CREATE ENDPOINT a un account di accesso di SQL Server con l'opzione AS  
 Nell'esempio seguente viene negata l'autorizzazione `CREATE ENDPOINT` all'utente `ArifS`. Nell'esempio viene utilizzata l'opzione `AS` per specificare `MandarP` come entità da cui l'entità che esegue l'istruzione deriva il diritto di effettuare l'operazione.  
  
```  
USE master;  
DENY CREATE ENDPOINT TO ArifS AS MandarP;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [DENY-autorizzazioni per Server (Transact-SQL)](../../t-sql/statements/deny-server-permissions-transact-sql.md)   
 [REVOKE-autorizzazioni per Server &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-server-permissions-transact-sql.md)   
 [Gerarchia delle autorizzazioni &#40;Motore di database&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  
