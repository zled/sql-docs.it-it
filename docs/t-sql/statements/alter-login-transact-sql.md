---
title: L'autorizzazione ALTER LOGIN (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_LOGIN_TSQL
- ALTER LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER LOGIN statement
- change password
- mapping logins [SQL Server]
- logins [SQL Server], modifying
- passwords [SQL Server], modifying
- names [SQL Server], logins
- modifying login accounts
ms.assetid: e247b84e-c99e-4af8-8b50-57586e1cb1c5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: fc5c2a17e3d75cb743c6c0e3a335d911e102de0e
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="alter-login-transact-sql"></a>ALTER LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Modifica le proprietà di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    | <cryptographic_credential_option>  
    }   
[;]  
  
<status_option> ::=  
        ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD = 'password' | hashed_password HASHED  
    [   
      OLD_PASSWORD = 'oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }  
    | CREDENTIAL = credential_name  
    | NO CREDENTIAL  
  
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
  
<cryptographic_credentials_option> ::=   
    ADD CREDENTIAL credential_name  
  | DROP CREDENTIAL credential_name  
```  
  
```  
-- Syntax for Azure SQL Database  
  
ALTER LOGIN login_name   
  {   
      <status_option>   
    | WITH <set_option> [ ,.. .n ]   
  }   
[;]  
  
<status_option> ::=  
    ENABLE | DISABLE  
  
<set_option> ::=   
    PASSWORD ='password'   
    [  
      OLD_PASSWORD ='oldpassword'  
    ]   
    | NAME = login_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    }   
  
<status_option> ::=ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD ='password'   
    [   
      OLD_PASSWORD ='oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }   
      
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
```  
  
## <a name="arguments"></a>Argomenti  
 *login_name*  
 Specifica il nome dell'account di accesso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che si desidera modificare. Gli account di accesso per il dominio devono essere racchiusi tra parentesi nel formato [dominio\utente].  
  
 ENABLE | DISABLE  
 Abilita o disabilita questo account di accesso. La disabilitazione di un account di accesso non influisce sul comportamento degli account di accesso già connessi. (Utilizzare il `KILL` istruzione per terminare un connessioni esistenti.) Gli account di accesso disabilitati conservano le autorizzazioni e possono essere ancora rappresentati.  
  
 PASSWORD **='***password***'**  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica la password per l'account di accesso che viene modificato. Per le password viene fatta distinzione tra maiuscole e minuscole.  
  
 In modo continuo connessioni attive al Database di SQL richiedono la riautorizzazione (eseguita dal motore di Database) almeno ogni 10 ore. Il motore di Database tenta la riautorizzazione utilizzando la password inviata e nessun input utente viene richiesto. Per motivi di prestazioni quando si reimposta una password nel Database SQL, la connessione non verrà nuovamente autenticata, anche se la connessione viene reimpostata a causa del pool di connessioni. Ciò è diverso da quello del Server SQL locale. Se la password è stata modificata dopo la connessione è stata inizialmente autorizzata, è necessario terminare la connessione e stabilire una nuova connessione utilizzando la nuova password. Un utente con l'autorizzazione KILL DATABASE CONNECTION possa terminare in modo esplicito una connessione al Database SQL tramite il comando KILL. Per ulteriori informazioni, vedere [KILL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/kill-transact-sql.md).  
  
 PASSWORD  **=**  *hashed_password*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo alla parola chiave HASHED. Specifica il valore hash della password per l'account di accesso in fase di creazione.  
  
> [!IMPORTANT]  
>  Quando un account di accesso (o un utente di database indipendente) si connette e viene autenticato, tramite la connessione vengono memorizzate nella cache le informazioni relative all'identità sull'account di accesso. In caso di un account di accesso con l'autenticazione di Windows, sono incluse informazioni sull'appartenenza ai gruppi di Windows. L'identità dell'account di accesso rimane autenticata, a condizione che la connessione venga mantenuta. Per forzare le modifiche nell'identità, ad esempio una reimpostazione della password o una modifica dell'appartenenza al gruppo di Windows, l'account di accesso deve disconnettersi dall'autorità di autenticazione (Windows o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) e accedere di nuovo. Un membro del ruolo predefinito del server **sysadmin** o qualsiasi account di accesso con l'autorizzazione **ALTER ANY CONNECTION** può usare il comando **KILL** per terminare una connessione e forzare la riconnessione di un account di accesso. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è possibile usare di nuovo le informazioni di connessione quando si aprono più connessioni alle finestre Esplora oggetti ed Editor di query. Chiudere tutte le connessioni per forzare la riconnessione.  
  
 HASHED  
   
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica che è già stato eseguito l'hashing per la password immessa dopo l'argomento PASSWORD. Se si include questa opzione, viene eseguito l'hashing della password prima che questa venga archiviata nel database. Questa opzione deve essere utilizzata solo per la sincronizzazione degli account di accesso tra due server. Non utilizzare l'opzione HASHED per le normali operazioni di modifica delle password.  
  
 OLD_PASSWORD **='***oldpassword***'**  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Password corrente dell'account di accesso a cui verrà assegnata una nuova password. Per le password viene fatta distinzione tra maiuscole e minuscole.  
  
 MUST_CHANGE  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si include questa opzione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiederà una password aggiornata al primo utilizzo dell'account di accesso modificato.  
  
 DEFAULT_DATABASE  **=**  *database*  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica un database predefinito da assegnare all'account di accesso.  
  
 DEFAULT_LANGUAGE  **=**  *language*  
 
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica una lingua predefinita da assegnare all'account di accesso. La lingua predefinita per gli account di accesso di tutti i Database SQL è l'inglese e non può essere modificata. La lingua predefinita di `sa` account di accesso per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su Linux, è l'inglese, ma può essere modificata.  
  
 NOME = *login_name*  
 Nuovo nome dell'account di accesso che viene rinominato. Se si tratta di un account di accesso di Windows, il SID dell'entità di Windows corrispondente al nuovo nome deve corrispondere al SID associato all'account di accesso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il nuovo nome di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso non può contenere un carattere barra rovesciata (\\).  
  
 CHECK_EXPIRATION = {ON | **OFF** }  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica se i criteri di scadenza delle password devono essere applicati a questo account di accesso. Il valore predefinito è OFF.  
  
 CHECK_POLICY  **=**  { **ON** | OFF}  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica che i criteri password di Windows del computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere applicati a questo account di accesso. Il valore predefinito è ON.  
  
 CREDENZIALE = *credential_name*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nome della credenziale su cui eseguire il mapping all'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La credenziale deve già esistere nel server. Per ulteriori informazioni vedere [credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md). Impossibile eseguire il mapping di una credenziale per l'account di accesso sa.  
  
 NO CREDENTIAL  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Rimuove gli eventuali mapping esistenti tra l'account di accesso e una credenziale del server. Per ulteriori informazioni vedere [credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 UNLOCK  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica che un account di accesso bloccato deve essere sbloccato.  
  
 ADD CREDENTIAL  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Aggiunge una credenziale del provider EKM per l'account di accesso. Per ulteriori informazioni, vedere [Extensible Key Management &#40; EKM &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 DROP CREDENTIAL  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
Rimuove una credenziale del provider Extensible Key Management (EKM) dall'account di accesso. Per ulteriori informazioni vedere [Extensible Key Management &#40; EKM &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Osservazioni  
 Quando CHECK_POLICY è impostato su ON, non è possibile utilizzare l'argomento HASHED.  
  
 Quando si modifica l'opzione CHECK_POLICY impostandola su ON, si verifica il comportamento seguente:  
  
-   La cronologia delle password viene inizializzata con il valore dell'hash della password corrente.  
  
 Quando si modifica l'opzione CHECK_POLICY impostandola su OFF, si ottengono le conseguenze seguenti:  
  
-   Anche l'opzione CHECK_EXPIRATION viene impostata su OFF.  
  
-   Viene cancellata la cronologia delle password.  
  
-   Il valore di *lockout_time* viene reimpostato.  
  
Se si specifica MUST_CHANGE, è necessario impostare CHECK_EXPIRATION e CHECK_POLICY su ON. In caso contrario, l'istruzione non verrà eseguita correttamente.  
  
Se l'opzione CHECK_POLICY è impostata su OFF, non è possibile impostare CHECK_EXPIRATION su ON. Un'istruzione ALTER LOGIN che presenta questa combinazione di opzioni avrà esito negativo.  
  
Non è possibile utilizzare ALTER_LOGIN con l'argomento DISABLE per negare l'accesso a un gruppo di Windows. Ad esempio, ALTER_LOGIN [*domain\group*] DISABLE restituirà il messaggio di errore seguente:  
  
 "Messaggio 15151, livello 16, stato 1, riga 1"  
  
 "Non è possibile modificare l'account di accesso '*Domain\Group*', perché non esiste o non si dispone dell'autorizzazione."  
  
 Questo si verifica per motivi strutturali.  
  
In [!INCLUDE[ssSDS](../../includes/sssds-md.md)], dati di accesso necessarie per autenticare una connessione e le regole del firewall a livello di server temporaneamente vengono memorizzati nella cache in ogni database. Questa cache viene aggiornata periodicamente. Per forzare un aggiornamento della cache di autenticazione e assicurarsi che un database è la versione più recente della tabella gli account di accesso, eseguire [FLUSHAUTHCACHE DBCC &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER ANY LOGIN.  
  
 Se viene utilizzata l'opzione CREDENTIAL, è richiesta anche l'autorizzazione ALTER ANY CREDENTIAL.  
  
 Se l'account di accesso da modificare è un membro del **sysadmin** ruolo predefinito del server o un utente che dispongono dell'autorizzazione CONTROL SERVER, richiede l'autorizzazione CONTROL SERVER quando si apportano le modifiche seguenti:  
  
-   Reimpostazione della password senza specificare la vecchia password.  
  
-   Attivazione di MUST_CHANGE, CHECK_POLICY o CHECK_EXPIRATION.  
  
-   Modifica del nome dell'account di accesso.  
  
-   Attivazione o disabilitazione dell'account di accesso.  
  
-   Mapping dell'account di accesso a una diversa credenziale.  
  
 Un'entità può modificare la password, la lingua predefinita e il database predefinito per il proprio account di accesso.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-enabling-a-disabled-login"></a>A. Abilitazione di un account di accesso disabilitato  
 Nell'esempio seguente viene attivato l'account di accesso `Mary5`.  
  
```sql  
ALTER LOGIN Mary5 ENABLE;  
```  
  
### <a name="b-changing-the-password-of-a-login"></a>B. Modifica della password di un account di accesso  
 Nell'esempio seguente viene modificata la password dell'account di accesso `Mary5` in una password complessa.  
  
```sql  
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';  
```  
  
### <a name="c-changing-the-name-of-a-login"></a>C. Modifica del nome di un account di accesso  
 Nell'esempio seguente viene modificato il nome dell'account di accesso `Mary5` in `John2`.  
  
```sql  
ALTER LOGIN Mary5 WITH NAME = John2;  
```  
  
### <a name="d-mapping-a-login-to-a-credential"></a>D. Mapping tra un account di accesso e una credenziale  
 Nell'esempio seguente sull'account di accesso `John2` viene eseguito il mapping alla credenziale `Custodian04`.  
  
```sql  
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;  
```  
  
### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>E. Mapping di un account di accesso a una credenziale EKM  
 Nell'esempio seguente viene eseguito il mapping dell'account di accesso `Mary5` alla credenziale EKM `EKMProvider1`.  
  
 
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```sql  
ALTER LOGIN Mary5  
ADD CREDENTIAL EKMProvider1;  
GO  
```  
  
### <a name="f-unlocking-a-login"></a>F. Sblocco di un account di accesso  
 Per sbloccare un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], eseguire l'istruzione seguente, sostituendo **** con la password dell'account desiderata.  
  
  
```sql  
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;  

GO  
```  
  
 Per sbloccare un account di accesso senza modificare la password, disabilitare i criteri di controllo, quindi attivarli nuovamente.  
  
```sql  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;  
GO  
```  
  
### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. Modifica della password di un account di accesso mediante HASHED  
 Nell'esempio seguente viene modificata la password dell'account di accesso `TestUser` con un valore con hash.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```sql  
ALTER LOGIN TestUser WITH   
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;  
GO  
```  
  
 
  
## <a name="see-also"></a>Vedere anche  
 [Credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [DROP LOGIN &#40; Transact-SQL &#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  


