---
title: ALTER LOGIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 68
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9faa9de82ed9b5db0ba2ccac071d038fb430f096
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43061574"
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
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse 
  
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
-- Syntax for Parallel Data Warehouse  
  
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
 Abilita o disabilita questo account di accesso. La disabilitazione di un account di accesso non influisce sul comportamento degli account di accesso già connessi. (Usare l'istruzione `KILL` per terminare le connessioni esistenti.) Gli account di accesso disabilitati conservano le autorizzazioni e possono essere ancora rappresentati.  
  
 PASSWORD **='***password***'**  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica la password per l'account di accesso che viene modificato. Per le password viene fatta distinzione tra maiuscole e minuscole.  
  
 Le connessioni continuamente attive a database SQL richiedono la riautorizzazione (eseguita dal motore di database) almeno ogni 10 ore. Il motore di database prova la riautorizzazione usando la password inviata originariamente e non richiede alcun input da parte dell'utente. Per motivi di prestazioni, quando si reimposta una password nel database SQL la connessione non viene nuovamente autenticata, anche se viene reimpostata a causa del pool di connessioni. Questo comportamento è diverso da quello dell'istanza locale di SQL Server. Se la password è stata cambiata dopo l'autorizzazione iniziale della connessione, è necessario terminare la connessione e stabilirne una nuova usando la nuova password. Un utente con l'autorizzazione KILL DATABASE CONNECTION può terminare in modo esplicito una connessione al database SQL usando il comando KILL. Per altre informazioni, vedere [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md).  
  
 PASSWORD **=***hashed_password*  
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
 **Si applica a**: da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e Parallel Data Warehouse.  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si include questa opzione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiederà una password aggiornata al primo utilizzo dell'account di accesso modificato.  
  
 DEFAULT_DATABASE **=***database*  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica un database predefinito da assegnare all'account di accesso.  
  
 DEFAULT_LANGUAGE **=***language*  
 
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica una lingua predefinita da assegnare all'account di accesso. La lingua predefinita per tutti gli account di accesso dei database SQL è l'inglese e non può essere modificata. La lingua predefinita dell'account di accesso `sa` per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su Linux, è l'inglese, ma può essere modificata.  
  
 NAME = *login_name*  
 Nuovo nome dell'account di accesso che viene rinominato. Se si tratta di un account di accesso di Windows, il SID dell'entità di Windows corrispondente al nuovo nome deve corrispondere al SID associato all'account di accesso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il nuovo nome di un account di accesso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non può contenere una barra rovesciata (\\).  
  
 CHECK_EXPIRATION = { ON | **OFF** }  
 **Si applica a**: da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e Parallel Data Warehouse.  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica se i criteri di scadenza delle password devono essere applicati a questo account di accesso. Il valore predefinito è OFF.  
  
 CHECK_POLICY **=** { **ON** | OFF }  
 **Si applica a**: da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e Parallel Data Warehouse.  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica che i criteri password di Windows del computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere applicati a questo account di accesso. Il valore predefinito è ON.  
  
 CREDENTIAL = *credential_name*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nome della credenziale su cui eseguire il mapping all'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La credenziale deve già esistere nel server. Per altre informazioni, vedere [Credenziali &#40;Motore di database&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md). Non è possibile eseguire il mapping di credenziali all'account di accesso sa.  
  
 NO CREDENTIAL  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Rimuove gli eventuali mapping esistenti tra l'account di accesso e una credenziale del server. Per altre informazioni, vedere [Credenziali &#40;Motore di database&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 UNLOCK  
 **Si applica a**: da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e Parallel Data Warehouse.  
  
 Si applica solo agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specifica che un account di accesso bloccato deve essere sbloccato.  
  
 ADD CREDENTIAL  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Aggiunge una credenziale del provider EKM per l'account di accesso. Per altre informazioni, vedere [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 DROP CREDENTIAL  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
Rimuove una credenziale del provider EKM dall'account di accesso. Per altre informazioni, vedere [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Remarks  
 Quando CHECK_POLICY è impostato su ON, non è possibile utilizzare l'argomento HASHED.  
  
 Quando si modifica l'opzione CHECK_POLICY impostandola su ON, si verifica il comportamento seguente:  
  
-   La cronologia delle password viene inizializzata con il valore dell'hash della password corrente.  
  
 Quando si modifica l'opzione CHECK_POLICY impostandola su OFF, si ottengono le conseguenze seguenti:  
  
-   Anche l'opzione CHECK_EXPIRATION viene impostata su OFF.  
  
-   Viene cancellata la cronologia delle password.  
  
-   Il valore di *lockout_time* viene reimpostato.  
  
Se si specifica MUST_CHANGE, è necessario impostare CHECK_EXPIRATION e CHECK_POLICY su ON. In caso contrario, l'istruzione non verrà eseguita correttamente.  
  
Se l'opzione CHECK_POLICY è impostata su OFF, non è possibile impostare CHECK_EXPIRATION su ON. Un'istruzione ALTER LOGIN che presenta questa combinazione di opzioni avrà esito negativo.  
  
Non è possibile utilizzare ALTER_LOGIN con l'argomento DISABLE per negare l'accesso a un gruppo di Windows. Ad esempio, ALTER_LOGIN [*domain\group*] DISABLE restituisce il messaggio di errore seguente:  
  
 "Messaggio 15151, livello 16, stato 1, riga 1"  
  
 "Non è possibile modificare l'oggetto account di accesso '*Domain\Group*' perché non esiste oppure perché non si ha l'autorizzazione".  
  
 Questo si verifica per motivi strutturali.  
  
Nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] i dati dell'account di accesso necessari per autenticare una connessione e le regole del firewall a livello di server vengono memorizzati temporaneamente nella cache in ogni database. Questa cache viene aggiornata periodicamente. Per forzare un aggiornamento della cache di autenticazione e assicurarsi che un database abbia la versione più recente della tabella di account di accesso, eseguire [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY LOGIN.  
  
 Se viene utilizzata l'opzione CREDENTIAL, è richiesta anche l'autorizzazione ALTER ANY CREDENTIAL.  
  
 Se l'account di accesso da modificare è un membro del ruolo predefinito del server **sysadmin** o un utente che dispone dell'autorizzazione CONTROL SERVER, è richiesta anche l'autorizzazione CONTROL SERVER quando si apportano le modifiche seguenti:  
  
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
 [Credenziali &#40;motore di database&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  


