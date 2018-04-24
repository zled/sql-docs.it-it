---
title: CREATE LOGIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_LOGIN_TSQL
- CREATE LOGIN
- LOGIN_TSQL
- LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], logins
- mapping logins [SQL Server]
- logins [SQL Server], creating
- CREATE LOGIN statement
- permissions [SQL Server], logins
- Windows domain accounts [SQL Server]
- re-hashing passwords
- certificates [SQL Server], logins
ms.assetid: eb737149-7c92-4552-946b-91085d8b1b01
caps.latest.revision: 101
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5173c5680356703b027e8ae6b705cf7f085cedb4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-login-transact-sql"></a>CREATE LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Crea un account di accesso del [!INCLUDE[ssDE](../../includes/ssde-md.md)] per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
CREATE LOGIN login_name { WITH <option_list1> | FROM <sources> }  
  
<option_list1> ::=   
    PASSWORD = { 'password' | hashed_password HASHED } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
    SID = sid  
    | DEFAULT_DATABASE = database      
    | DEFAULT_LANGUAGE = language  
    | CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
    | CREDENTIAL = credential_name   
  
<sources> ::=  
    WINDOWS [ WITH <windows_options>[ ,... ] ]  
    | CERTIFICATE certname  
    | ASYMMETRIC KEY asym_key_name  
  
<windows_options> ::=        
    DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
```  
  
```  
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse  
  
CREATE LOGIN login_name  
 { WITH <option_list3> }  
  
<option_list3> ::=   
    PASSWORD = { 'password' }  
    [ SID = sid ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
CREATE LOGIN loginName { WITH <option_list1> | FROM WINDOWS }  
  
<option_list1> ::=   
    PASSWORD = { 'password' } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
      CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
```  
  
## <a name="arguments"></a>Argomenti  
 *login_name*  
 Specifica il nome dell'account di accesso creato. Esistono quattro tipi di account di accesso: account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], account di accesso di Windows, account di accesso sui quali viene eseguito il mapping a certificati e account di accesso sui quali viene eseguito il mapping a chiavi asimmetriche. Quando si creano account di accesso che vengono mappati da un account di dominio di Windows, è necessario usare il nome di accesso utente precedente a Windows 2000 nel formato [\<NomeDominio>\\<nome_account_accesso>]. Non è possibile usare un nome UPN nel formato login_name@DomainName. Vedere l'esempio D più avanti in questo argomento. Gli account di accesso di autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono di tipo **sysname** e devono essere conformi alle regole per gli [Identificatori](http://msdn.microsoft.com/library/ms175874.aspx) e non possono contenere un simbolo "**\\**". Gli account di accesso di Windows possono contenere un simbolo "**\\**". I nomi degli account di accesso basati sugli utenti di Active Directory devono avere un numero di caratteri inferiore a 21.  
  
 PASSWORD **='***password***'**  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica la password per l'account di accesso che viene creato. È consigliabile utilizzare una password complessa. Per altre informazioni, vedere [Password complesse](../../relational-databases/security/strong-passwords.md) e [Criteri password](../../relational-databases/security/password-policy.md). A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le informazioni relative alle password archiviate vengono calcolate tramite SHA-512 della password salt.  
  
 Per le password viene fatta distinzione tra maiuscole e minuscole. Le password devono essere sempre composte da almeno 8 caratteri e non possono superare i 128 caratteri.  Le password possono includere i caratteri a-z, A-Z, 0-9 e la maggior parte dei caratteri non alfanumerici. Le password non possono contenere virgolette singole o il valore di *login_name*.  
  
 PASSWORD **=***hashed_password*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo alla parola chiave HASHED. Specifica il valore hash della password per l'account di accesso in fase di creazione.  
  
 HASHED  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica che è già stato eseguito l'hashing per la password immessa dopo l'argomento PASSWORD. Se questa opzione non è selezionata, viene generato l'hash della stringa immessa come password prima che questa venga archiviata nel database. Questa opzione deve essere utilizzata solo per la migrazione dei database da un server a un altro. Non utilizzare l'opzione HASHED per creare nuovi account di accesso. L'opzione HASHED non può essere utilizzata con hash creati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7 o versioni precedenti.  
  
 MUST_CHANGE  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se questa opzione è inclusa, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene richiesto all'utente di immettere una nuova password al primo utilizzo del nuovo account di accesso.  
  
 CREDENTIAL **=***credential_name*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nome della credenziale su cui eseguire il mapping al nuovo account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La credenziale deve già esistere nel server. Attualmente questa opzione consente solo di connettere la credenziale a un account di accesso. Non è possibile eseguire il mapping di una credenziale all'account di accesso dell'amministratore di sistema.  
  
 SID = *sid*  
 Utilizzato per ricreare un account di accesso. Si applica solo agli account di accesso con autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], non agli account di accesso con autenticazione di Windows. Specifica il SID del nuovo account di accesso con autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se questa opzione non viene usata, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna un SID automaticamente. La struttura del SID dipende dalla versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   SID di account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: valore letterale (**Binary(16)**) a 16 byte basato su un GUID. Ad esempio `SID = 0x14585E90117152449347750164BA00A7`.  
  
-   SID di account di accesso del [!INCLUDE[ssSDS](../../includes/sssds-md.md)]: struttura SID valida per il [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Si tratta in genere di un valore letterale (**binary(32)**) a 32 byte costituito da `0x01060000000000640000000000000000` e 16 byte che rappresentano un GUID. Ad esempio `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`.  
  
DEFAULT_DATABASE **=***database*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il database predefinito da assegnare all'account di accesso. Se questa opzione non è inclusa, il database predefinito viene impostato su master.  
  
DEFAULT_LANGUAGE **=***language*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica la lingua predefinita da assegnare all'account di accesso. Se questa opzione non è inclusa, la lingua predefinita viene impostata sulla lingua predefinita corrente del server. Se la lingua predefinita del server viene modificata in seguito, la lingua predefinita dell'account di accesso rimane inalterata.  
  
CHECK_EXPIRATION **=** { ON | **OFF** }  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica se i criteri di scadenza delle password devono essere applicati a questo account di accesso. Il valore predefinito è OFF.  
  
CHECK_POLICY **=** { **ON** | OFF }  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica che i criteri password di Windows del computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere applicati a questo account di accesso. Il valore predefinito è ON.  
  
 Se i criteri di Windows richiedono password complesse, queste devono contenere almeno tre dei quattro caratteri seguenti:  
  
-   Un carattere maiuscolo (A-Z).  
-   Un carattere minuscolo (a-z)  
-   Una cifra (0-9).  
-   Un carattere non alfanumerico, ad esempio uno spazio, _, @, *, ^, %, !, $, # o &.  
  
WINDOWS  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica che sull'account di accesso deve essere eseguito il mapping a un account di accesso di Windows.  
  
CERTIFICATE *certname*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il nome di un certificato da associare a questo account di accesso. Questo certificato deve essere già presente nel database master.  
  
ASYMMETRIC KEY *asym_key_name*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il nome di una chiave asimmetrica da associare a questo account di accesso. Questa chiave deve essere già presente nel database master.  
  
## <a name="remarks"></a>Remarks  
 Per le password viene fatta distinzione tra maiuscole e minuscole.  
  
 L'utilizzo di password con hashing già eseguito è supportato solo quando si creano gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se si specifica MUST_CHANGE, è necessario impostare CHECK_EXPIRATION e CHECK_POLICY su ON. In caso contrario, l'istruzione non verrà eseguita correttamente.  
  
 Una combinazione di CHECK_POLICY = OFF e CHECK_EXPIRATION = ON non è supportata.  
  
 Quando l'opzione CHECK_POLICY è impostata su OFF, il valore di *lockout_time* viene reimpostato e l'opzione CHECK_EXPIRATION viene impostata su OFF.  
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION e CHECK_POLICY sono imposte solo in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] e versioni successive. Per ulteriori informazioni, vedere [Password Policy](../../relational-databases/security/password-policy.md).  
  
 Gli account di accesso creati da certificati o chiavi asimmetriche vengono utilizzati solo per la firma del codice e non possono essere utilizzati per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile creare un account di accesso da un certificato o una chiave asimmetrica solo quando il certificato o la chiave asimmetrica esistono già nel database master.  
  
 Per uno script con cui trasferire gli account di accesso, vedere [Trasferimento di accessi e password tra istanze di SQL Server](http://support.microsoft.com/kb/918992).  
  
 La creazione automatica di un account di accesso abilita il nuovo account a cui viene concessa l'autorizzazione **CONNECT SQL** a livello di server.  
 
 La [modalità di autenticazione](../../relational-databases/security/choose-an-authentication-mode.md) del server deve corrispondere al tipo di account di accesso per consentire l'accesso.
  
 Per informazioni sulla progettazione di un sistema di autorizzazioni, vedere [Introduzione alle autorizzazioni del motore di database](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
## <a name="includesssdsfullincludessssdsfull-mdmd-and-includesssdwincludessssdw-mdmd-logins"></a>[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] e account di accesso di [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
 Nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] l'istruzione **CREATE LOGIN** deve essere l'unica istruzione in un batch.  
  
 In alcuni metodi di connessione al [!INCLUDE[ssSDS](../../includes/sssds-md.md)], ad esempio **sqlcmd**, è necessario aggiungere il nome del server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] al nome di accesso nella stringa di connessione usando la notazione *\<login>*@*\<server>*. Se, ad esempio, l'account di accesso è `login1` e il nome completo del server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è `servername.database.windows.net`, il parametro *username* della stringa di connessione deve essere `login1@servername`. Poiché la lunghezza totale del parametro *username* è di 128 caratteri, *login_name* è limitato a 127 caratteri meno la lunghezza del nome del server. Nell'esempio la lunghezza di `login_name` può essere solo di 117 caratteri poiché `servername` è costituito da 10 caratteri.  
  
 Nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] e in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] è necessario essere connessi al database master per creare un account di accesso.  
  
 Le regole di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consentono di creare un account di accesso con autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel formato \<nomeaccountaccesso>@\<nomeserver>. Se il server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in uso è **myazureserver** e l'account di accesso è **myemail@live.com**, l'account di accesso deve essere specificato nel formato **myemail@live.com@myazureserver**.  
  
 Nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] i dati dell'account di accesso necessari per autenticare una connessione e le regole del firewall a livello di server vengono memorizzati temporaneamente nella cache in ogni database. Questa cache viene aggiornata periodicamente. Per forzare un aggiornamento della cache di autenticazione e assicurarsi che un database abbia la versione più recente della tabella di account di accesso, eseguire [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
 Per altre informazioni sugli account di accesso del [!INCLUDE[ssSDS](../../includes/sssds-md.md)], vedere [Controllo e concessione dell'accesso al database](http://msdn.microsoft.com/library/ee336235.aspx).  
  
## <a name="permissions"></a>Autorizzazioni  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è richiesta l'autorizzazione **ALTER ANY LOGIN** per il server o l'appartenenza al ruolo predefinito del server **securityadmin**.  
  
 In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] solo l'account di accesso dell'entità di livello server (creato dal processo di provisioning) o i membri del ruolo del database `loginmanager` nel database master possono creare nuovi account di accesso.  
  
 Se viene usata l'opzione **CREDENTIAL**, è richiesta anche l'autorizzazione **ALTER ANY CREDENTIAL** nel server.  
  
## <a name="next-steps"></a>Next Steps  
 Una volta creato, un account di accesso può connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)] o al [!INCLUDE[ssSDS](../../includes/sssds-md.md)], ma avrà solo delle autorizzazioni concesse al ruolo **public**. Provare a effettuare alcune delle attività seguenti:  
  
-   Per connettersi a un database, creare un utente del database per l'account di accesso. Per altre informazioni, vedere [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md).  
  
-   Creare un ruolo del server definito dall'utente tramite [CREATE SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-role-transact-sql.md). Usare **ALTER SERVER ROLE** … **ADD MEMBER** per aggiungere il nuovo account di accesso al ruolo del server definito dall'utente. Per altre informazioni, vedere [CREATE SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-role-transact-sql.md) e [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
-   Usare **sp_addsrvrolemember** per aggiungere l'account di accesso a un ruolo predefinito del server. Per altre informazioni, vedere [Ruoli a livello di Server](../../relational-databases/security/authentication-access/server-level-roles.md) e [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).  
  
-   Usare l'istruzione **GRANT** per concedere le autorizzazioni a livello di server al nuovo account di accesso o a un ruolo in cui esso è contenuto. Per altre informazioni, vedere [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Creazione di un account di accesso con una password  
 Nell'esempio seguente viene creato un account di accesso per un utente specifico e viene assegnata una password.  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-with-a-password-that-must-be-changed"></a>B. Creazione di un account di accesso con una password da modificare
 Nell'esempio seguente viene creato un account di accesso per un utente specifico e viene assegnata una password. L'opzione `MUST_CHANGE` richiede all'utente di modificare questa password alla prima connessione al server.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>' 
    MUST_CHANGE,  CHECK_EXPIRATION = ON;
GO  
```  
[!NOTE] Impossibile utilizzare l'opzione MUST_CHANGE se CHECK_EXPIRATION è impostato su OFF.
  
### <a name="c-creating-a-login-mapped-to-a-credential"></a>C. Creazione di un account di accesso sul quale viene eseguito il mapping a una credenziale  
 Nell'esempio seguente viene creato l'account di accesso per utente specifico, utilizzando il relativo nome. Su questo account di accesso viene eseguito il mapping alla credenziale.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>',   
    CREDENTIAL = <credentialName>;  
GO  
```  
  
### <a name="d-creating-a-login-from-a-certificate"></a>D. Creazione di un account di accesso da un certificato  
 Nell'esempio seguente viene creato un account di accesso per un utente specifico da un certificato nel database master.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE MASTER;  
CREATE CERTIFICATE <certificateName>  
    WITH SUBJECT = '<login_name> certificate in master database',  
    EXPIRY_DATE = '12/05/2025';  
GO  
CREATE LOGIN <login_name> FROM CERTIFICATE <certificateName>;  
GO  
```  
  
### <a name="e-creating-a-login-from-a-windows-domain-account"></a>E. Creazione di un account di accesso da un account di dominio di Windows  
 Nell'esempio seguente viene creato un account di accesso da un account di dominio di Windows.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE LOGIN [<domainName>\<login_name>] FROM WINDOWS;  
GO  
```  
  
### <a name="f-creating-a-login-from-a-sid"></a>F. Creazione di un account di accesso da un SID  
 L'esempio seguente crea prima un account di accesso con autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e determina il SID dell'account di accesso.  
  
```  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 La query restituisce 0x241C11948AEEB749B0D22646DB1A19F2 come SID. La query dell'utente restituirà un valore diverso. Le istruzioni seguenti eliminano l'account di accesso e quindi ricreano l'account di accesso. Utilizzare il SID della query precedente.  
  
```  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="g-creating-a-sql-server-authentication-login-with-a-password"></a>G. Creazione di un account di accesso di autenticazione di SQL Server con una password  
 Nell'esempio seguente viene creato l'account di accesso `Mary7` con la password `A2c3456`.  
  
```sql  
CREATE LOGIN Mary7 WITH PASSWORD = 'A2c3456$#' ;  
```  
  
### <a name="h-using-options"></a>H. Uso delle opzioni  
 Nell'esempio seguente viene creato l'account di accesso `Mary8` con password e alcuni degli argomenti facoltativi.  
  
```  
CREATE LOGIN Mary8 WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
```  
  
### <a name="i-creating-a-login-from-a-windows-domain-account"></a>I. Creazione di un account di accesso da un account di dominio di Windows  
 Nell'esempio seguente viene creato un account di accesso da un account di dominio di Windows denominato `Mary` nel dominio `Contoso`.  
  
```  
CREATE LOGIN [Contoso\Mary] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione alle autorizzazioni del motore di database](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Criteri password](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Creare un account di accesso](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
