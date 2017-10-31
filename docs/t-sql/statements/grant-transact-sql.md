---
title: GRANT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GRANT_TSQL
- GRANT
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], GRANT statement
- schema-level securables [SQL Server]
- GRANT statement
- cross-database permissions
- GRANT statement, about GRANT statement
- server-level securables [SQL Server]
- database-level securables [SQL Server]
- permissions [SQL Server], granting
ms.assetid: a760c16a-4d2d-43f2-be81-ae9315f38185
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bb9bf548f042a4a6f41322fb789a2cd7e5b6bec9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="grant-transact-sql"></a>GRANT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Concede a un'entità autorizzazioni per un'entità a protezione diretta.  Il concetto generale consiste nel concedere \<un'autorizzazione > ON \<un oggetto > TO \<alcuni utenti, account di accesso o gruppo >. Per una discussione generale sulle autorizzazioni, vedere [autorizzazioni &#40; motore di Database &#41;](../../relational-databases/security/permissions-database-engine.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for GRANT  
GRANT { ALL [ PRIVILEGES ] }  
      | permission [ ( column [ ,...n ] ) ] [ ,...n ]  
      [ ON [ class :: ] securable ] TO principal [ ,...n ]   
      [ WITH GRANT OPTION ] [ AS principal ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
GRANT   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class_type> ::=  
{  
      LOGIN  
    | DATABASE  
    | OBJECT  
    | ROLE  
    | SCHEMA  
    | USER  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 ALL  
 Questa opzione è deprecata ed è stata mantenuta solo a scopo di compatibilità con le versioni precedenti. Non concede tutte le possibili autorizzazioni. La concessione di autorizzazioni tramite l'argomento ALL equivale alla concessione delle autorizzazioni seguenti.  
  
-   Se l'entità a protezione diretta è un database, ALL corrisponde a BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE e CREATE VIEW.  
  
-   Se l'entità a protezione diretta è una funzione scalare, ALL corrisponde a EXECUTE e REFERENCES.  
  
-   Se l'entità a protezione diretta è una funzione con valori di tabella, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
-   Se l'entità a protezione diretta è una stored procedure, ALL corrisponde a EXECUTE.  
  
-   Se l'entità a protezione diretta è una tabella, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
-   Se l'entità a protezione diretta è una vista, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
PRIVILEGES  
 Opzione inclusa per compatibilità con lo standard ISO. Non modifica il funzionamento di ALL.  
  
*autorizzazione*  
 Nome di un'autorizzazione. I mapping validi tra le autorizzazioni e le entità a protezione diretta sono descritti negli argomenti correlati elencati di seguito.  
  
*colonna*  
 Specifica il nome di una colonna in una tabella per la quale vengono concesse autorizzazioni. È necessario utilizzare le parentesi ().  
  
*classe*  
 Specifica la classe dell'entità a protezione diretta per la quale viene concessa l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
*entità a protezione diretta*  
 Specifica l'entità a protezione diretta a cui viene concessa l'autorizzazione.  
  
PER *principale*  
 Nome di un'entità. Le entità a cui è possibile concedere le autorizzazioni per un'entità a protezione diretta variano in base all'entità a protezione diretta specifica. Per ulteriori informazioni sulle combinazioni valide, vedere gli argomenti secondari elencati di seguito.  
  
GRANT OPTION  
 Indica che l'utente autorizzato potrà inoltre concedere l'autorizzazione specificata ad altre entità.  
  
AS *principale*  
 Utilizzare la clausola principale per indicare che l'entità è registrata come l'utente che concede l'autorizzazione deve essere un'identità diverso da quello che esegue l'istruzione. Ad esempio, presuppongono che l'utente Mary sia principal_id 12 utente Raul è 15 principale. Mary esegue `GRANT SELECT ON OBJECT::X TO Steven WITH GRANT OPTION AS Raul;` ora la tabella sys. database_permissions indicherà che il grantor_prinicpal_id 15 (Raul) è stato anche se l'istruzione è stata effettivamente eseguita dall'utente 13 (Mary).

Utilizzando la clausola AS in genere non è consigliabile, a meno che non è necessario definire in modo esplicito la catena di autorizzazione. Per ulteriori informazioni, vedere il **riepilogo dell'algoritmo di controllo di autorizzazione** sezione [autorizzazioni (motore di Database)](../../relational-databases/security/permissions-database-engine.md).

L'utilizzo di come questa istruzione non implica la possibilità di rappresentare un altro utente. 
  
## <a name="remarks"></a>Osservazioni  
 La sintassi completa dell'istruzione GRANT è complessa. Il diagramma della sintassi precedente è stato semplificato per evidenziarne la struttura. La sintassi completa per la concessioni di autorizzazioni per entità a protezione diretta specifiche viene descritta negli argomenti riportati di seguito.  
  
 È possibile utilizzare l'istruzione REVOKE per rimuovere le autorizzazioni concesse e l'istruzione DENY per negare un'autorizzazione specifica a un'entità anche in caso di esecuzione di un'istruzione GRANT.  
  
 La concessione di un'autorizzazione rimuove l'istruzione DENY o REVOKE di tale autorizzazione per l'entità a protezione diretta specificata. Se la stessa autorizzazione viene negata a un livello superiore e in tale livello è inclusa l'entità a protezione diretta, l'istruzione DENY ha la precedenza. Tuttavia, la revoca dell'autorizzazione concessa a un ambito superiore non ha la precedenza.  
  
 Le autorizzazioni a livello di database vengono concesse nell'ambito del database specificato. Se un utente deve ottenere autorizzazioni per gli oggetti di un database diverso da quello corrente, è necessario creare un account utente nel secondo database o consentire all'account utente di accedere a tale database oltre che al database corrente.  
  
> [!CAUTION]  
>  Un'istruzione DENY a livello di tabella non ha la precedenza rispetto a un'istruzione GRANT a livello di colonna. Questa incongruenza nella gerarchia di autorizzazioni è stata mantenuta per garantire la compatibilità con le versioni precedenti Verrà rimosso in una versione futura.  
  
 La stored procedure di sistema sp_helprotect visualizza le autorizzazioni per un'entità a protezione diretta a livello di database.  
  
## <a name="with-grant-option"></a>WITH GRANT OPTION  
 Il **GRANT** ... **CON GRANT OPTION** specifica che l'entità di sicurezza, riceve l'autorizzazione ha la possibilità di concedere l'autorizzazione specificata ad altri account di sicurezza. Quando l'entità che riceve l'autorizzazione è un ruolo o un gruppo di Windows, il **AS** clausola deve essere utilizzata quando l'autorizzazione per l'oggetto deve essere concessa ulteriormente a utenti che non sono membri del gruppo o del ruolo. Perché solo un utente, anziché un gruppo o ruolo può eseguire un **GRANT** deve utilizzare l'istruzione, un membro del gruppo o ruolo specifico di **AS** clausola per richiamare in modo esplicito l'appartenenza al ruolo o gruppo quando si concedono l'autorizzazione. L'esempio seguente mostra come **WITH GRANT OPTION** quando viene concesso a un ruolo o gruppo di Windows.  
  
```  
-- Execute the following as a database owner  
GRANT EXECUTE ON TestProc TO TesterRole WITH GRANT OPTION;  
EXEC sp_addrolemember TesterRole, User1;  
-- Execute the following as User1  
-- The following fails because User1 does not have the permission as the User1  
GRANT EXECUTE ON TestMe TO User2;  
-- The following succeeds because User1 invokes the TesterRole membership  
GRANT EXECUTE ON TestMe TO User2 AS TesterRole;  
```  
  
## <a name="chart-of-sql-server-permissions"></a>Grafico delle autorizzazioni di SQL Server  
 Per un grafico di grandi dimensioni di tutte le autorizzazioni [!INCLUDE[ssDE](../../includes/ssde-md.md)] in formato pdf, vedere [http://go.microsoft.com/fwlink/?LinkId=229142](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
## <a name="permissions"></a>Permissions  
 L'utente che concede le autorizzazioni (o l'entità specificata con l'opzione AS) deve disporre della relativa autorizzazione con GRANT OPTION oppure di un'autorizzazione di livello superiore che include l'autorizzazione che viene concessa. Se si utilizza l'opzione AS, sono previsti requisiti aggiuntivi. Per ulteriori informazioni, vedere l'argomento relativo alle entità a protezione diretta.  
  
 I proprietari degli oggetti possono concedere autorizzazioni per gli oggetti di cui sono proprietari. Le entità con l'autorizzazione CONTROL per un'entità a sicurezza diretta possono concedere l'autorizzazione per quella entità.  
  
 Gli utenti che dispongono dell'autorizzazione CONTROL SERVER, ad esempio i membri del ruolo predefinito del server sysadmin, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel server. Gli utenti che dispongono dell'autorizzazione CONTROL in un database, ad esempio i membri del ruolo predefinito del database db_owner, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel database. Gli utenti che dispongono dell'autorizzazione CONTROL in uno schema, possono concedere qualsiasi autorizzazione per qualsiasi oggetto all'interno dello schema.  
  
## <a name="examples"></a>Esempi  
 Nella tabella seguente vengono elencate le entità a protezione diretta e gli argomenti in cui viene descritta la relativa sintassi specifica.  
  
|||  
|-|-|  
|Ruolo applicazione|[GRANT-autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Assembly|[CONCEDERE autorizzazioni per Assembly &#40; Transact-SQL &#41;](../../t-sql/statements/grant-assembly-permissions-transact-sql.md)|  
|Chiave asimmetrica|[GRANT-autorizzazioni per chiavi asimmetriche &#40; Transact-SQL &#41;](../../t-sql/statements/grant-asymmetric-key-permissions-transact-sql.md)|  
|Gruppo di disponibilità|[Il gruppo di disponibilità di concedere autorizzazioni &#40; Transact-SQL &#41;](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)|  
|Certificato|[Certificato di concedere autorizzazioni &#40; Transact-SQL &#41;](../../t-sql/statements/grant-certificate-permissions-transact-sql.md)|  
|Contratto|[Servizio di concessione delle autorizzazioni di Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Database|[Autorizzazioni per Database GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)|
|Credenziali con ambito database|[Credenziali (Transact-SQL) con ambito Database GRANT](../../t-sql/statements/grant-database-scoped-credential-transact-sql.md)|  
|Endpoint|[CONCEDERE autorizzazioni per Endpoint &#40; Transact-SQL &#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)|  
|Catalogo full-text|[Autorizzazioni GRANT Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)|  
|Elenco di parole non significative full-text|[Autorizzazioni GRANT Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)|  
|Funzione|[CONCEDERE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Account di accesso|[Autorizzazioni per entità Server GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)|  
|Tipo di messaggio|[Servizio di concessione delle autorizzazioni di Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Oggetto|[CONCEDERE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Coda|[CONCEDERE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Associazione al servizio remoto|[Servizio di concessione delle autorizzazioni di Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Ruolo|[GRANT-autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Route|[Servizio di concessione delle autorizzazioni di Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|schema|[CONCEDERE autorizzazioni per Schema &#40; Transact-SQL &#41;](../../t-sql/statements/grant-schema-permissions-transact-sql.md)|  
|Elenco delle proprietà di ricerca|[Autorizzazioni GRANT Search Property List &#40; Transact-SQL &#41;](../../t-sql/statements/grant-search-property-list-permissions-transact-sql.md)|  
|Server|[GRANT - autorizzazioni per server &#40;Transact-SQL&#41;](../../t-sql/statements/grant-server-permissions-transact-sql.md)|  
|Servizio|[Servizio di concessione delle autorizzazioni di Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Stored procedure|[CONCEDERE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Chiave simmetrica|[GRANT-autorizzazioni per chiavi simmetriche &#40; Transact-SQL &#41;](../../t-sql/statements/grant-symmetric-key-permissions-transact-sql.md)|  
|Sinonimo|[CONCEDERE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Oggetti di sistema|[GRANT - autorizzazioni per oggetti di sistema &#40;Transact-SQL&#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)|  
|Tabella|[CONCEDERE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Tipo|[Autorizzazioni per tipi GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-type-permissions-transact-sql.md)|  
|Utente|[GRANT-autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Visualizza|[CONCEDERE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Raccolta di XML Schema|[GRANT-autorizzazioni per raccolte XML Schema &#40; Transact-SQL &#41;](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

