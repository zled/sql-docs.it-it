---
title: REVOKE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVOKE_TSQL
- REVOKE
dev_langs:
- TSQL
helpviewer_keywords:
- schema-level securables [SQL Server]
- REVOKE statement, Transact-SQL syntax
- removing permissions
- server-level securables [SQL Server]
- deleting permissions
- revoking permissions [SQL Server]
- REVOKE statement
- denying permissions [SQL Server], removing
- database-level securables [SQL Server]
- granting permissions [SQL Server], removing
- permissions [SQL Server], revoking
- dropping permissions
ms.assetid: 9d31d3e7-0883-45cd-bf0e-f0361bbb0956
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa08be63c0d792ed1e0422860b55a0c8f2abdc8b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-transact-sql"></a>REVOKE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove un'autorizzazione precedentemente assegnata o negata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for REVOKE  
REVOKE [ GRANT OPTION FOR ]  
      {   
        [ ALL [ PRIVILEGES ] ]  
        |  
                permission [ ( column [ ,...n ] ) ] [ ,...n ]  
      }  
      [ ON [ class :: ] securable ]   
      { TO | FROM } principal [ ,...n ]   
      [ CASCADE] [ AS principal ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
REVOKE   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    [ FROM | TO ] principal [ ,...n ]  
    [ CASCADE ]  
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
 GRANT OPTION FOR  
 Indica che verrà revocata la capacità di concedere l'autorizzazione specificata. Argomento obbligatorio in caso di utilizzo dell'argomento CASCADE.  
  
> [!IMPORTANT]  
>  Se l'autorizzazione specificata è stata concessa all'entità senza l'opzione GRANT, l'autorizzazione stessa verrà revocata.  
  
 ALL  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Questa opzione non revoca tutte le possibili autorizzazioni. La revoca di autorizzazioni tramite l'argomento ALL equivale alla revoca delle autorizzazioni seguenti.  
  
-   Se l'entità a protezione diretta è un database, ALL corrisponde a BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE e CREATE VIEW.  
  
-   Se l'entità a protezione diretta è una funzione scalare, ALL corrisponde a EXECUTE e REFERENCES.  
  
-   Se l'entità a protezione diretta è una funzione con valori di tabella, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
-   Se l'entità a protezione diretta è una stored procedure, ALL corrisponde a EXECUTE.  
  
-   Se l'entità a protezione diretta è una tabella, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
-   Se l'entità a protezione diretta è una vista, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
> [!NOTE]  
>  La sintassi REVOKE ALL è deprecata. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Revocare invece autorizzazioni specifiche.  
  
 PRIVILEGES  
 Opzione inclusa per compatibilità con lo standard ISO. Non modifica il funzionamento di ALL.  
  
 *autorizzazione*  
 Nome di un'autorizzazione. I mapping validi tra le autorizzazioni per entità a protezione diretta sono descritti negli argomenti elencati [sintassi specifica delle entità a protezione diretta](#securable) più avanti in questo argomento.  
  
 *colonna*  
 Specifica il nome di una colonna in una tabella alla quale vengono revocate le autorizzazioni. È necessario utilizzare le parentesi.  
  
 *classe*  
 Specifica la classe dell'entità a protezione diretta alla quale viene revocata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 *entità a protezione diretta*  
 Specifica l'entità a protezione diretta a cui viene revocata l'autorizzazione.  
  
 PER | DA *principale*  
 Nome di un'entità. Le entità a cui è possibile revocare le autorizzazioni per un'entità a protezione diretta variano in base all'entità a protezione diretta specifica. Per ulteriori informazioni sulle combinazioni valide, vedere gli argomenti elencati [sintassi specifica delle entità a protezione diretta](#securable) più avanti in questo argomento.  
  
 CASCADE  
 Indica che l'autorizzazione revocata viene revocata anche ad altre entità alle quali è stata concessa da questa entità. Se si utilizza l'argomento CASCADE, è inoltre necessario includere l'argomento GRANT OPTION FOR.  
  
> [!CAUTION]  
>  La revoca propagata di un'autorizzazione concessa con WITH GRANT OPTION comporterà la revoca sia delle autorizzazioni GRANT che delle autorizzazioni DENY per tale autorizzazione.  
  
 AS *principale*  
 Utilizzare la clausola principale per indicare che revoca di un'autorizzazione che è stata concessa da un'entità diversi da. Ad esempio, presuppongono che l'utente Mary sia principal_id 12 utente Raul è 15 principale. Mary sia Raul concedere a che un utente denominato Steven la stessa autorizzazione. Nella tabella sys. database_permissions indicherà le autorizzazioni due volte, ma ognuno hanno un valore grantor_prinicpal_id diversi. Mary Impossibile revocare l'autorizzazione utilizzando il `AS RAUL` clausola per rimuovere la concessione di Raul dell'autorizzazione.
 
L'utilizzo di come questa istruzione non implica la possibilità di rappresentare un altro utente.  
  
## <a name="remarks"></a>Osservazioni  
 La sintassi completa dell'istruzione REVOKE è complessa. Il diagramma della sintassi precedente è stato semplificato per evidenziarne la struttura. La sintassi completa per la revoca delle autorizzazioni per entità a protezione diretta specifiche viene descritta negli argomenti elencati [sintassi specifica delle entità a protezione diretta](#securable) più avanti in questo argomento.  
  
 È possibile utilizzare l'istruzione REVOKE per rimuovere le autorizzazioni concesse e l'istruzione DENY per negare un'autorizzazione specifica a un'entità anche in caso di esecuzione di un'istruzione GRANT.  
  
 La concessione di un'autorizzazione rimuove l'istruzione DENY o REVOKE di tale autorizzazione per l'entità a protezione diretta specificata. Se la stessa autorizzazione viene negata a un livello superiore e in tale livello è inclusa l'entità a protezione diretta, l'istruzione DENY ha la precedenza. Tuttavia, la revoca dell'autorizzazione concessa a un ambito superiore non ha la precedenza.  
  
> [!CAUTION]  
>  Un'istruzione DENY a livello di tabella non ha la precedenza rispetto a un'istruzione GRANT a livello di colonna. Questa incoerenza nella gerarchia delle autorizzazioni è stata mantenuta per compatibilità con le versioni precedenti. Verrà rimosso in una versione futura.  
  
 La stored procedure di sistema sp_helprotect restituisce le autorizzazioni per un'entità a protezione diretta a livello di database.  
  
 L'istruzione REVOKE avrà esito negativo se l'argomento CASCADE viene omesso in caso di revoca a un'entità di un'autorizzazione concessa tramite GRANT OPTION.  
  
## <a name="permissions"></a>Permissions  
 Le entità con l'autorizzazione CONTROL per un'entità a protezione diretta possono revocare l'autorizzazione per quella entità. I proprietari degli oggetti possono revocare autorizzazioni per gli oggetti di cui sono proprietari.  
  
 Gli utenti che dispongono dell'autorizzazione CONTROL SERVER, ad esempio i membri del ruolo predefinito del server sysadmin, possono revocare qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel server. Gli utenti che dispongono dell'autorizzazione CONTROL in un database, ad esempio i membri del ruolo predefinito del database db_owner, possono revocare qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel database. Gli utenti che dispongono dell'autorizzazione CONTROL in uno schema possono revocare qualsiasi autorizzazione per qualsiasi oggetto all'interno dello schema.  
  
##  <a name="securable"></a>Sintassi specifica delle entità a protezione diretta  
 Nella tabella seguente vengono elencate le entità a protezione diretta e gli argomenti in cui viene descritta la relativa sintassi specifica.  
  
|Entità a protezione diretta|Argomento|  
|---------------|-----------|  
|Ruolo applicazione|[REVOKE-autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Assembly|[REVOKE-autorizzazioni per Assembly &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-assembly-permissions-transact-sql.md)|  
|Chiave asimmetrica|[Autorizzazioni per chiavi asimmetriche REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-asymmetric-key-permissions-transact-sql.md)|  
|Gruppo di disponibilità|[Le autorizzazioni del gruppo di disponibilità REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)|  
|Certificato|[REVOCARE le autorizzazioni del certificato &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-certificate-permissions-transact-sql.md)|  
|Contratto|[REVOCARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Database|[REVOKE-autorizzazioni per Database &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-permissions-transact-sql.md)|  
|Endpoint|[REVOKE-autorizzazioni per Endpoint &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)|  
|Credenziali con ambito database|[Credenziali (Transact-SQL) con ambito Database REVOKE](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)|  
|Catalogo full-text|[REVOCA di autorizzazioni Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|Elenco di parole non significative full-text|[REVOCA di autorizzazioni Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|Funzione|[REVOCARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Account di accesso|[Autorizzazioni per entità Server REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-server-principal-permissions-transact-sql.md)|  
|Tipo di messaggio|[REVOCARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Oggetto|[REVOCARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Coda|[REVOCARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Associazione al servizio remoto|[REVOCARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Ruolo|[REVOKE-autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Route|[REVOCARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|schema|[REVOKE-autorizzazioni per Schema &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-schema-permissions-transact-sql.md)|  
|Elenco delle proprietà di ricerca|[REVOCARE autorizzazioni Search Property List &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-search-property-list-permissions-transact-sql.md)|  
|Server|[REVOKE-autorizzazioni per Server &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-server-permissions-transact-sql.md)|  
|Servizio|[REVOCARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Stored procedure|[REVOCARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Chiave simmetrica|[Autorizzazioni per chiavi simmetriche REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)|  
|Sinonimo|[REVOCARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Oggetti di sistema|[REVOCARE autorizzazioni per gli oggetti di sistema &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)|  
|Tabella|[REVOCARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Tipo|[Autorizzazioni per tipi REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-type-permissions-transact-sql.md)|  
|Utente|[REVOKE-autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Visualizza|[REVOCARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Raccolta di XML Schema|[REVOCARE autorizzazioni per raccolte XML Schema &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia delle autorizzazioni &#40;Motore di database&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

