---
title: ALTER AUTHORIZATION (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_AUTHORIZATION_TSQL
- ALTER AUTHORIZATION
dev_langs: TSQL
helpviewer_keywords:
- owners [SQL Server], transferring
- modifying entity ownership
- full-text search [SQL Server], permissions
- owners [SQL Server], entities
- ALTER AUTHORIZATION statement
- entity ownership [SQL Server]
- transferring ownership
- search property lists [SQL Server], permissions
- TAKE OWNERSHIP
ms.assetid: 8c805ae2-91ed-4133-96f6-9835c908f373
caps.latest.revision: "84"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: f992d085f8c9b282be4288488cf872d99b426f48
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-authorization-transact-sql"></a>ALTER AUTHORIZATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Modifica la proprietà di un'entità a protezione diretta.    
    
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Sintassi    
    
```    
-- Syntax for SQL Server  
ALTER AUTHORIZATION    
   ON [ <class_type>:: ] entity_name    
   TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::=    
    {    
        OBJECT | ASSEMBLY | ASYMMETRIC KEY | AVAILABILITY GROUP | CERTIFICATE     
      | CONTRACT | TYPE | DATABASE | ENDPOINT | FULLTEXT CATALOG     
      | FULLTEXT STOPLIST | MESSAGE TYPE | REMOTE SERVICE BINDING    
      | ROLE | ROUTE | SCHEMA | SEARCH PROPERTY LIST | SERVER ROLE     
      | SERVICE | SYMMETRIC KEY | XML SCHEMA COLLECTION    
    }    
```    

```
-- Syntax for SQL Database  
  
ALTER AUTHORIZATION    
   ON [ <class_type>:: ] entity_name    
   TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::=    
    {    
      OBJECT | ASSEMBLY | ASYMMETRIC KEY | CERTIFICATE     
    | TYPE | DATABASE | FULLTEXT CATALOG     
    | FULLTEXT STOPLIST     
    | ROLE | SCHEMA | SEARCH PROPERTY LIST     
    | SYMMETRIC KEY | XML SCHEMA COLLECTION    
    }    
```    

    
```    
-- Syntax for Azure SQL Data Warehouse  
  
ALTER AUTHORIZATION ON    
    [ <class_type> :: ] <entity_name>     
    TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::= {    
      SCHEMA     
    | OBJECT     
}    
    
<entity_name> ::=    
{    
      schema_name    
    | [ schema_name. ] object_name    
}    
```    
    
```    
-- Syntax for Parallel Data Warehouse  
  
ALTER AUTHORIZATION ON    
    [ <class_type> :: ] <entity_name>     
    TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::= {    
      DATABASE     
    | SCHEMA     
    | OBJECT     
}    
    
<entity_name> ::=    
{    
      database_name 
    | schema_name    
    | [ schema_name. ] object_name    
}    
```    
    
## <a name="arguments"></a>Argomenti    
\<class_type > è la classe di entità a protezione diretta dell'entità per cui viene modificato il proprietario. OBJECT è l'impostazione predefinita.    
    
|||    
|-|-|    
|OBJECT|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], Azure SQL Data Warehouse, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|    
|ASSEMBLY|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|ASYMMETRIC KEY|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|AVAILABILITY GROUP |**Si applica a**: SQL Server 2012 tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|CERTIFICATE|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|CONTRACT|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|DATABASE|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Per ulteriori informazioni, vedere [ALTER AUTHORIZATION per database](#AlterDB) sezione riportata di seguito.|    
|ENDPOINT|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|FULLTEXT CATALOG|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|FULLTEXT STOPLIST|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|MESSAGE TYPE|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|REMOTE SERVICE BINDING|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|ROLE|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|ROUTE|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SCHEMA|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], Azure SQL Data Warehouse, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|    
|SEARCH PROPERTY LIST|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|SERVER ROLE|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SERVICE|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SYMMETRIC KEY|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|TYPE|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|XML SCHEMA COLLECTION|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
    
 *nome_entità*    
 Nome dell'entità.    
    
 *principal_name* | PROPRIETARIO DELLO SCHEMA    
 Nome dell'entità di sicurezza a cui verrà trasferita la proprietà dell'entità. Gli oggetti di database devono essere di proprietà di un'entità di database oppure di un utente o ruolo del database. Gli oggetti server, ad esempio i database, devono essere di proprietà di un'entità server (un account di accesso). Specificare **proprietario dello SCHEMA** come il *principal_name* per indicare che l'oggetto deve essere di proprietà dell'entità proprietaria dello schema dell'oggetto.    
    
## <a name="remarks"></a>Osservazioni    
 È possibile utilizzare l'istruzione ALTER AUTHORIZATION per modificare la proprietà di qualsiasi entità associata a un proprietario. La proprietà di entità incluse in un database può essere trasferita a qualsiasi entità a livello di database. La proprietà di entità a livello di server può essere trasferita solo a entità a livello di server.    
    
> [!IMPORTANT]    
>  A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], un utente può essere proprietario di un elemento OBJECT o TYPE contenuto in uno schema di proprietà di un altro utente di database, diversamente da quanto consentito nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [OBJECTPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/objectproperty-transact-sql.md) e [TYPEPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/typeproperty-transact-sql.md).    
    
 È possibile trasferire la proprietà delle seguenti entità incluse nello schema di tipo "object": tabelle, viste, funzioni, procedure, code e sinonimi.    
    
 Non è possibile trasferire la proprietà delle entità seguenti: server collegati, statistiche, vincoli, regole, valori predefiniti, trigger, code di [!INCLUDE[ssSB](../../includes/sssb-md.md)], credenziali, funzioni di partizione, schemi di partizione, chiavi master del database, chiavi master del servizio e notifiche di eventi.    
    
 Non è possibile trasferire la proprietà di membri delle classi a protezione diretta seguenti: server, account di accesso, utenti, ruoli applicazione e colonne.    
    
 L'opzione SCHEMA OWNER è valida solo in caso di trasferimento della proprietà di un'entità inclusa nello schema. L'opzione SCHEMA OWNER trasferirà la proprietà dell'entità al proprietario dello schema in cui si trova. Solo le entità della classe OBJECT, TYPE o XML SCHEMA COLLECTION sono incluse nello schema.    
    
 Se l'entità di destinazione non è un database e l'entità sta per essere trasferita a un nuovo proprietario, verranno eliminate tutte le autorizzazioni per la destinazione.    
    
> [!CAUTION]    
>  Il comportamento degli schemi in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] è diverso rispetto alle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile che il codice in cui gli schemi sono equivalenti agli utenti del database non restituisca risultati corretti. Non utilizzare le viste del catalogo delle versioni precedenti, inclusa sysobjects, nei database in cui sia già stata utilizzata una delle istruzioni DLL seguenti: CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE, ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. In questi database è necessario usare le nuove viste del catalogo, in cui si tiene conto della separazione tra entità e schemi introdotta in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Per altre informazioni sulle viste del catalogo, vedere [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).    
    
 Si noti inoltre quanto segue:    
    
> [!IMPORTANT]    
>  È l'unico modo affidabile per cercare il proprietario di un oggetto query il **Sys. Objects** vista del catalogo. L'unico modo affidabile per cercare il proprietario di un tipo consiste nell'utilizzare la funzione TYPEPROPERTY.    
    
## <a name="special-cases-and-conditions"></a>Casi e condizioni speciali    
 Nella tabella seguente sono elencati casi, eccezioni e condizioni speciali validi per la modifica delle autorizzazioni.    
    
|Classe|Condizione|    
|-----------|---------------|    
|OBJECT|Non è possibile modificare la proprietà di trigger, vincoli, regole, valori predefiniti, statistiche, oggetti di sistema, code, viste indicizzate o tabelle con viste indicizzate.|    
|SCHEMA|In caso di trasferimento della proprietà, verranno eliminate le autorizzazioni per gli oggetti inclusi nello schema che non dispongono di proprietari espliciti. Non è possibile modificare il proprietario di sys, dbo o information_schema.|    
|TYPE|Non è possibile modificare la proprietà di una classe TYPE appartenente a sys o information_schema.|    
|CONTRACT, MESSAGE TYPE o SERVICE|Non è possibile modificare la proprietà delle entità di sistema.|    
|SYMMETRIC KEY|Non è possibile modificare la proprietà delle chiavi temporanee globali.|    
|CERTIFICATE o ASYMMETRIC KEY|Non è possibile trasferire la proprietà di queste entità a un ruolo o gruppo.|    
|ENDPOINT|L'entità deve essere un account di accesso.|    
  
## <a name="AlterDB"></a>ALTER AUTHORIZATION per i database  
**SI APPLICA A**: [!INCLUDE[ssSQL15](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
### <a name="for-sql-server"></a>Per SQL Server:  
**Requisiti per il nuovo proprietario:**   
Il nuovo server principale proprietario deve essere uno dei valori seguenti:  
-   Un accesso con autenticazione SQL Server.  
-   Un accesso con autenticazione Windows che rappresenta un utente di Windows (non un gruppo).  
-   Un utente di Windows che esegue l'autenticazione tramite un accesso con autenticazione Windows che rappresenta un gruppo di Windows.  
  
**Requisiti per l'utente esegue l'istruzione ALTER AUTHORIZATION:**  
Se non si è un membro del **sysadmin** ruolo predefinito del server, è necessario disporre di almeno autorizzazione diventa proprietario nel database e deve disporre dell'autorizzazione IMPERSONATE nel nuovo account di accesso proprietario.   

### <a name="for-azure-sql-database"></a>Per Database SQL di Azure:  
**Requisiti per il nuovo proprietario:**   
Il nuovo server principale proprietario deve essere uno dei valori seguenti:  
-   Un accesso con autenticazione SQL Server.  
-   Un utente federato (non un gruppo) presente in Azure AD.  
-   Utente gestito (non un gruppo) o un'applicazione presente in Azure AD.    

> [!NOTE]  
> Se il nuovo proprietario è un utente di Azure Active Directory, non può esistere come utente del database in cui il nuovo proprietario diventerà proprietario del nuovo database. Innanzitutto, tale utente di Azure AD deve essere rimossi dal database prima l'esecuzione dell'istruzione ALTER AUTHORIZATION, la modifica del proprietario di database per il nuovo utente. Per ulteriori informazioni sulla configurazione di un utente di Azure Active Directory con il Database SQL, vedere [la connessione al Database SQL o Data Warehouse da usando Azure Active Directory l'autenticazione di SQL](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).   
  
**Requisiti per l'utente esegue l'istruzione ALTER AUTHORIZATION:**  
È necessario connettersi al database di destinazione per modificare il proprietario di tale database.  

I seguenti tipi di account è possono modificare il proprietario di un database. 
* L'account di accesso a livello di servizio dell'entità. (L'amministratore SQL Azure provisioning quando il server logico è stato creato.)  
* L'amministratore di Azure Active Directory per il Server SQL Azure.   
* Il proprietario corrente del database.   
 
  
Nella tabella seguente sono riepilogati i requisiti:  
  
Esecutore  |Destinazione  |Risultato    
---------|---------|---------  
Account di accesso di autenticazione di SQL Server     |Account di accesso di autenticazione di SQL Server         |Operazione completata  
Account di accesso di autenticazione di SQL Server     |Utente di Azure Active Directory         |Esito negativo           
Utente di Azure Active Directory     |Account di accesso di autenticazione di SQL Server         |Operazione completata           
Utente di Azure Active Directory     |Utente di Azure Active Directory         |Operazione completata           
  
Per verificare un proprietario di Azure Active Directory del database, eseguire il comando Transact-SQL seguente in un database utente (in questo esempio `testdb`).  
    
```    
SELECT CAST(owner_sid as uniqueidentifier) AS Owner_SID   
FROM sys.databases   
WHERE name = 'testdb';  
```    
    
L'output sarà un identificatore (ad esempio 6D8B81F6-7C79-444C-8858-4AF896C03C67) che corrisponde a Azure AD ObjectID assegnato a`richel@cqclinic.onmicrosoft.com`  
Quando un utente di accesso di autenticazione di SQL Server è il proprietario del database, eseguire l'istruzione seguente nel database master per verificare il proprietario del database:  
    
```    
SELECT d.name, d.owner_sid, sl.name   
FROM sys.databases AS d  
JOIN sys.sql_logins AS sl  
ON d.owner_sid = sl.sid;  
    
```    
  
### <a name="best-practice"></a>Procedura consigliata  
  
Anziché agli utenti di Azure AD come singoli proprietari del database, utilizzare un gruppo di Azure AD come membro di **db_owner** ruolo predefinito del database. La procedura seguente viene illustrato come configurare un account di accesso disabilitato come proprietario del database e rendere un gruppo di Azure Active Directory (`mydbogroup`) un membro del **db_owner** ruolo. 
1.  Account di accesso a SQL Server come amministratore di Azure AD e modificare il proprietario del database da un accesso con autenticazione SQL Server disabilitato. Ad esempio, dal database utente eseguire:  
  ```    
  ALTER AUTHORIZATION ON database::testdb TO DisabledLogin;  
  ```    
2.  Creare un gruppo di Azure AD che deve essere proprietaria del database e aggiungerlo come utente al database utente. Esempio:  
  ```    
  CREATE USER [mydbogroup] FROM EXTERNAL PROVIDER;  
  ```    
3.  Nel database utente, aggiungere l'utente che rappresenta il gruppo di Azure AD, al **db_owner** ruolo predefinito del database. Esempio:  
  ```    
  ALTER ROLE db_owner ADD MEMBER mydbogroup;  
  ```    
  
A questo punto il `mydbogroup` i membri possono gestire centralmente il database come membri del **db_owner** ruolo.  
- Quando i membri di questo gruppo vengono rimossi dal gruppo di Azure AD, vengono perse automaticamente le autorizzazioni dbo per il database.  
- Allo stesso modo se vengono aggiunti nuovi membri `mydbogroup` gruppo di Azure Active Directory, vengono automaticamente ottenere l'accesso dbo per il database.  
  
Per verificare se un utente specifico dispone dell'autorizzazione dbo efficace, richiedere all'utente di eseguire l'istruzione seguente:  
    
```    
SELECT IS_MEMBER ('db_owner');  
```    
  
Valore restituito pari a 1 indica che l'utente è un membro del ruolo.  
   
    
## <a name="permissions"></a>Permissions    
 È richiesta l'autorizzazione TAKE OWNERSHIP per l'entità. Se il nuovo proprietario non è l'utente che sta eseguendo l'istruzione 1) è richiesta l'autorizzazione IMPERSONATE per il nuovo proprietario se si tratta di un utente o un account di accesso, oppure 2) se il nuovo proprietario è un ruolo, è richiesta l'appartenenza al ruolo o l'autorizzazione ALTER per tale ruolo, oppure 3) se il nuovo proprietario è un ruolo applicazione, è richiesta l'autorizzazione ALTER per il ruolo applicazione.    
    
## <a name="examples"></a>Esempi    
    
### <a name="a-transfer-ownership-of-a-table"></a>A. Trasferire la proprietà di una tabella    
 Nell'esempio seguente la proprietà della tabella `Sprockets` viene trasferita all'utente `MichikoOsada`. La tabella è inclusa nello schema `Parts`.    
    
```    
ALTER AUTHORIZATION ON OBJECT::Parts.Sprockets TO MichikoOsada;    
GO    
```    
    
 La query potrebbe essere simile alla seguente:    
    
```    
ALTER AUTHORIZATION ON Parts.Sprockets TO MichikoOsada;    
GO    
```    
    
 Se lo schema di oggetti non è incluso come parte dell'istruzione, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] Cerca l'oggetto di nello schema predefinito di utenti. Esempio:    
    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
```    
    
### <a name="b-transfer-ownership-of-a-view-to-the-schema-owner"></a>B. Trasferire la proprietà di una vista al proprietario dello schema    
 Nell'esempio seguente la proprietà della vista `ProductionView06` viene trasferita al proprietario dello schema che la contiene. La vista è inclusa nello schema `Production`.    
    
```    
ALTER AUTHORIZATION ON OBJECT::Production.ProductionView06 TO SCHEMA OWNER;    
GO    
```    
    
### <a name="c-transfer-ownership-of-a-schema-to-a-user"></a>C. Trasferire la proprietà di uno schema a un utente    
 Nell'esempio seguente la proprietà dello schema `SeattleProduction11` viene trasferita all'utente `SandraAlayo`.    
    
```    
ALTER AUTHORIZATION ON SCHEMA::SeattleProduction11 TO SandraAlayo;    
GO    
```    
    
### <a name="d-transfer-ownership-of-an-endpoint-to-a-sql-server-login"></a>D. Trasferire la proprietà di un endpoint a un account di accesso di SQL Server    
 Nell'esempio seguente la proprietà dell'endpoint `CantabSalesServer1` viene trasferita a `JaePak`. Poiché è un'entità a protezione diretta a livello di server, l'endpoint può essere trasferito solo a un'entità a livello di server.    
    
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].    
    
```    
ALTER AUTHORIZATION ON ENDPOINT::CantabSalesServer1 TO JaePak;    
GO    
```    
    
### <a name="e-changing-the-owner-of-a-table"></a>E. Modifica del proprietario di una tabella    
 Ognuno degli esempi seguenti viene modificato il proprietario del `Sprockets` tabella il `Parts` database all'utente del database `MichikoOsada`.    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON dbo.Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::dbo.Sprockets TO MichikoOsada;    
```    
    
### <a name="f-changing-the-owner-of-a-database"></a>F. Modifica del proprietario di un database    
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].    
    
 Nell'esempio seguente modificare il proprietario del `Parts` database all'account di accesso `MichikoOsada`.    
    
```    
ALTER AUTHORIZATION ON DATABASE::Parts TO MichikoOsada;    
```    
  
### <a name="g-changing-the-owner-of-a-sql-database-to-an-azure-ad-user"></a>G. Modifica del proprietario di un Database SQL a un utente AD Azure  
Nell'esempio seguente, un amministratore di Azure Active Directory per SQL Server in un'organizzazione con active directory denominato `cqclinic.onmicrosoft.com`, può modificare il proprietario corrente di un database `targetDB` e impostare un utente AAD `richel@cqclinic.onmicorsoft.com` il nuovo database proprietario mediante il comando seguente:  
    
```    
ALTER AUTHORIZATION ON database::targetDB TO [rachel@cqclinic.onmicrosoft.com];   
```    
    
 Si noti che per gli utenti di Azure AD è necessario utilizzare le parentesi che racchiudono il nome utente.  
  
    
## <a name="see-also"></a>Vedere anche    
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)     
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)     
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)    
 
