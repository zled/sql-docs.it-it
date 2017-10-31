---
title: "Le autorizzazioni del gruppo di disponibilità REVOKE (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], permissions
- REVOKE statement, availability groups
- revoking permissions, [SQL Server], availability groups
- permissions [SQL Server], availability group
ms.assetid: 02c77378-a36d-4286-9235-d8867a2b92ad
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1573f866cec3105cde4eeab59c230ede46144ac3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-availability-group-permissions-transact-sql"></a>REVOKE, autorizzazioni del gruppo di disponibilità (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Revoca le autorizzazioni per un gruppo di disponibilità Always On. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    ON AVAILABILITY GROUP :: availability_group_name  
    { FROM | TO } < server_principal >  [ ,...n ]  
    [ CASCADE ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
        SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey  
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Specifica un'autorizzazione che può essere revocata su un gruppo di disponibilità. Per un elenco delle autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 NEL gruppo di disponibilità **::***availability_group_name*  
 Specifica il gruppo di disponibilità per cui vengono revocate le autorizzazioni. Il qualificatore di ambito (**::**) è obbligatorio.  
  
 {DA | A} \<server_principal > specifica il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui viene revocata l'autorizzazione di accesso.  
  
 *SQL_Server_login*  
 Specifica il nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Specifica il nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creato da un account di accesso di Windows.  
  
 *SQL_Server_login_from_certificate*  
 Specifica il nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul quale viene eseguito il mapping a un certificato.  
  
 *SQL_Server_login_from_AsymKey*  
 Specifica il nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul quale viene eseguito il mapping a una chiave asimmetrica.  
  
 GRANT OPTION  
 Indica che verrà revocato il diritto di concedere l'autorizzazione specificata ad altre entità. L'autorizzazione stessa non verrà revocata.  
  
> [!IMPORTANT]  
>  Se l'autorizzazione specificata è stata concessa all'entità senza l'opzione GRANT, l'autorizzazione stessa verrà revocata.  
  
 CASCADE  
 Indica che l'autorizzazione che viene revocata anche ad altre entità a cui è stata concessa o negata da questa entità.  
  
> [!IMPORTANT]  
>  La revoca propagata di un'autorizzazione concessa con WITH GRANT OPTION comporterà la revoca sia delle autorizzazioni GRANT che delle autorizzazioni DENY per tale autorizzazione.  
  
 AS *SQL_Server_login*  
 Specifica l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dal quale l'entità che esegue la query ottiene il diritto di revocare l'autorizzazione.  
  
## <a name="remarks"></a>Osservazioni  
 Possibile revocare autorizzazioni nell'ambito del server solo quando il database corrente è **master**.  
  
 Informazioni sui gruppi di disponibilità sono visibili nella [availability_groups &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) vista del catalogo. Informazioni sulle autorizzazioni del server sono visibili nella [server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) è visibile nella vista del catalogo e le informazioni sulle entità server il [Sys. server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vista del catalogo.  
  
 Un gruppo di disponibilità è un'entità a protezione diretta a livello server. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile revocare per un gruppo di disponibilità, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione del gruppo di disponibilità|Autorizzazione del gruppo di disponibilità in cui è inclusa|Autorizzazione del server in cui è inclusa|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per il gruppo di disponibilità o l'autorizzazione ALTER ANY AVAILABILTIY GROUP per il server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-revoking-view-definition-permission-on-an-availability-group"></a>A. Revoca dell'autorizzazione VIEW DEFINITION per un gruppo di disponibilità  
 Nell'esempio seguente viene revocata l'autorizzazione `VIEW DEFINITION` sul gruppo di disponibilità `MyAg` per l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `ZArifin`.  
  
```  
USE master;  
REVOKE VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-revoking-take-ownership-permission-with-the-cascade"></a>B. Revoca dell'autorizzazione TAKE OWNERSHIP con l'opzione CASCADE  
 Nell'esempio seguente viene revocata l'autorizzazione `TAKE OWNERSHIP` sul gruppo di disponibilità `MyAg` per l'utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `PKomosinski` e da tutte le entità di sicurezza a cui `PKomosinski` ha concesso l'autorizzazione TAKE OWNERSHIP per MyAg.  
  
```  
USE master;  
REVOKE TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    CASCADE;  
GO  
```  
  
### <a name="c-revoking-a-previously-granted-with-grant-option-clause"></a>C. Revoca di una clausola WITH GRANT OPTION concessa in precedenza  
 Se è stata concessa un'autorizzazione tramite WITH GRANT OPTION, utilizzare REVOKE GRANT OPTION FOR... Per rimuovere WITH GRANT OPTION. Nell'esempio seguente viene concessa l'autorizzazione e viene rimossa la parte WITH GRANT dell'autorizzazione.  
  
```  
USE master;  
GRANT CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    WITH GRANT OPTION;  
GO  
REVOKE GRANT OPTION FOR CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski  
CASCADE  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Il gruppo di disponibilità di concedere autorizzazioni &#40; Transact-SQL &#41;](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)   
 [Nega le autorizzazioni del gruppo di disponibilità &#40; Transact-SQL &#41;](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [availability_groups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Viste del catalogo dei gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


