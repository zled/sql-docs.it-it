---
title: EXECUTE AS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
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
f1_keywords:
- EXECUTE AS
- EXECUTE_AS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REVERT statement
- WITH NO REVERT clause
- sessions [SQL Server], execution context
- EXECUTE AS
- execution context [SQL Server]
- switching execution context
ms.assetid: 613b8271-7f7d-4378-b7a2-5a7698551dbd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b89c78d286feaace6ec6bb2c85e854cb0ddbb5e0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="execute-as-transact-sql"></a>EXECUTE AS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Imposta il contesto di esecuzione di una sessione.  
  
 Per impostazione predefinita, una sessione inizia quando un utente si connette e termina quando l'utente si disconnette. Tutte le operazioni eseguite durante una sessione sono soggette alle verifiche delle autorizzazioni dell'utente connesso. Quando un **EXECUTE AS** istruzione viene eseguita, il contesto di esecuzione della sessione viene impostato il nome di account di accesso o utente specificato. Dopo il cambio di contesto, le autorizzazioni vengono confrontate con i token di sicurezza di accesso e utente per tale account invece che la persona che ha chiamato la **EXECUTE AS** istruzione. In pratica, l'account utente o l'account di accesso viene rappresentato per l'intera durata dell'esecuzione della sessione o del modulo oppure il passaggio di contesto viene ripristinato in modo esplicito.  
  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
{ EXEC | EXECUTE } AS <context_specification>  
[;]  
  
<context_specification>::=  
{ LOGIN | USER } = 'name'  
    [ WITH { NO REVERT | COOKIE INTO @varbinary_variable } ]   
| CALLER  
```  
  
## <a name="arguments"></a>Argomenti  
 Account di accesso  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica che il contesto di esecuzione da rappresentare è un account di accesso. L'ambito di rappresentazione è a livello di server.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente o in Database SQL.  
  
 Utente  
 Specifica che il contesto da rappresentare è un utente nel database corrente. L'ambito di rappresentazione è limitato al database corrente. Un cambio di contesto a un utente del database non eredita le autorizzazioni a livello di server di tale utente.  
  
> [!IMPORTANT]  
>  Mentre il cambio di contesto all'utente del database è attivo, qualsiasi tentativo di accesso alle risorse esterne al database comporterà l'esito negativo dell'esecuzione dell'istruzione. Ciò include l'utilizzo *database* istruzioni, le query distribuite e le query che fanno riferimento a un altro database che utilizza gli identificatori di tre o quattro parti.  
  
 **'** *nome* **'**  
 Nome utente o nome account di accesso valido. *nome* deve essere un membro del **sysadmin** ruolo predefinito del server, oppure esistere come entità nel [Sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) o [Sys. server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md), rispettivamente.  
  
 *nome* possono essere specificati come una variabile locale.  
  
 *nome* deve essere un account singleton e non può essere un gruppo, ruolo, certificato, chiave o un account predefinito, ad esempio NT AUTHORITY\LocalService, NT AUTHORITY\NetworkService o NT AUTHORITY\LocalSystem..  
  
 Per ulteriori informazioni, vedere [specificando un utente o un nome di accesso](#_user) più avanti in questo argomento.  
  
 NO REVERT  
 Specifica che non è possibile ripristinare il contesto precedente in seguito a un cambio di contesto. Il **NO REVERT** opzione può essere usata solo a livello ad hoc.  
  
 Per ulteriori informazioni sul ripristino del contesto precedente, vedere [REVERT &#40; Transact-SQL &#41; ](../../t-sql/statements/revert-transact-sql.md).  
  
 COOKIE in  **@**  *varbinary_variable*  
 Specifica il contesto di esecuzione possa solo essere ripristinare il contesto precedente se l'istruzione REVERT WITH COOKIE chiamante include il corretto  **@**  *varbinary_variable* valore. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] passa il cookie a  **@**  *varbinary_variable*. Il **COOKIE in** opzione può essere usata solo a livello ad hoc.  
  
 **@***varbinary_variable* è **varbinary (8000)**.  
  
> [!NOTE]  
>  Il cookie **OUTPUT** parametro per è attualmente documentato come **varbinary (8000)** che è la lunghezza massima corretta. Tuttavia, l'implementazione corrente restituisce **varbinary(100)**. Applicazioni devono riservare **varbinary (8000)** in modo che l'applicazione continua a funzionare correttamente se il cookie restituito dimensioni aumentano in una versione futura.  
  
 CALLER  
 Se utilizzato all'interno di un modulo, specifica che le istruzioni all'interno del modulo vengono eseguite nel contesto del chiamante del modulo.  
  
 Se utilizzato all'esterno di un modulo, l'istruzione non esegue alcuna azione.  
  
## <a name="remarks"></a>Osservazioni  
 Il cambio di contesto di esecuzione rimane valido finché non si verifica una delle situazioni seguenti:  
  
-   Viene eseguita un'altra istruzione EXECUTE AS.  
  
-   Viene eseguita un'istruzione REVERT.  
  
-   La sessione viene rimossa.  
  
-   La stored procedure o il trigger in cui è stato eseguito il comando è esistente.  
  
È possibile creare uno stack di contesti di esecuzione eseguendo più volte una chiamata all'istruzione EXECUTE AS in più entità. Quando viene chiamata, l'istruzione REVERT imposta il contesto sull'account di accesso o sull'utente nel successivo livello superiore nello stack di contesti. Per una dimostrazione di questo comportamento, vedere [esempio](#_exampleA).  
  
##  <a name="_user"></a>Specifica un utente o un nome di accesso  
 Il nome utente o account di accesso specificato in EXECUTE AS \<context_specification > deve esistere come entità nel **Sys. database_principals** o **Sys. server_principals**, rispettivamente, o Istruzione EXECUTE AS avrà esito negativo. È inoltre necessario concedere le autorizzazioni IMPERSONATE per l'entità. A meno che il chiamante è il proprietario del database, o un membro del **sysadmin** ruolo predefinito del server, l'entità deve esistere anche quando l'utente effettua l'accesso al database o all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite un gruppo di Windows l'appartenenza. Si suppongano ad esempio le condizioni seguenti: 
  
-   **CompanyDomain\SQLUsers** gruppo disponga dell'accesso per il **Sales** database.  
  
-   **CompanyDomain\SqlUser1** è un membro di **SQLUsers** e, di conseguenza, ha accesso implicito al **Sales** database.  
  
 Anche se **CompanyDomain\SqlUser1** ha accesso al database tramite l'appartenenza di **SQLUsers** gruppo, l'istruzione `EXECUTE AS USER = 'CompanyDomain\SqlUser1'` ha esito negativo perché `CompanyDomain\SqlUser1` non esiste come entità nel il database.  
  
Se l'utente è reso orfano (l'account di accesso associato non esiste più), e l'utente non è stato creato con **WITHOUT LOGIN**, **EXECUTE AS** avrà esito negativo per l'utente.  
  
## <a name="best-practice"></a>Procedura consigliata  
 Specificare un account di accesso o un utente che disponga almeno dei privilegi necessari per eseguire operazioni nella sessione. Ad esempio, non specificare un nome account di accesso con autorizzazioni a livello di server se sono richieste solo autorizzazioni a livello di database oppure non specificare l'account di un proprietario di database a meno che siano richieste le autorizzazioni corrispondenti.  
  
> [!CAUTION]  
>  L'istruzione EXECUTE AS può avere esito positivo, a condizione che il [!INCLUDE[ssDE](../../includes/ssde-md.md)] sia in grado di risolvere il nome. Se è presente un utente di dominio, è possibile che Windows sia in grado di risolvere l'utente per [!INCLUDE[ssDE](../../includes/ssde-md.md)], anche se l'utente di Windows non dispone dell'accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ciò potrebbe creare una condizione in cui un account di accesso privo di autorizzazione di accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risulti apparentemente connesso, sebbene l'account di accesso rappresentato disponga solo delle autorizzazioni concesse a public o guest.  
  
## <a name="using-with-no-revert"></a>Utilizzo di WITH NO REVERT  
 Se l'istruzione EXECUTE AS include la clausola facoltativa WITH NO REVERT, il contesto di esecuzione di una sessione non può essere ripristinato tramite REVERT oppure tramite l'esecuzione di un'altra istruzione EXECUTE AS. Il contesto impostato dall'istruzione rimane valido fino all'eliminazione della sessione.  
  
 Quando il WITH NO REVERT COOKIE = @*varbinary_variabl*clausola è specificato, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] passa il valore del cookie a @*varbinary_variabl*e. Il contesto di esecuzione impostato tale istruzione può essere ripristinata al contesto precedente se il chiamante REVERT WITH COOKIE = @*varbinary_variable* istruzione contiene lo stesso  *@varbinary_variable*  valore.  
  
 Questa opzione risulta utile in un ambiente in cui vengono utilizzati i pool di connessioni. Tramite i pool di connessioni vengono gestiti i gruppi di connessioni al database in modo che tali connessioni possano essere riutilizzate dalle applicazioni in un server applicazioni. Poiché il valore passato a  *@varbinary_variable*  è noto solo al chiamante di EXECUTE AS istruzione, il chiamante può garantire che il contesto di esecuzione stabilito non può essere modificato da altri utenti.  
  
## <a name="determining-the-original-login"></a>Determinazione dell'account di accesso originale  
 Utilizzare il [ORIGINAL_LOGIN](../../t-sql/functions/original-login-transact-sql.md) funzione per restituire il nome dell'account di accesso connesso all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile utilizzare questa funzione per restituire l'identità dell'account di accesso originale in sessioni in cui si verificano numerosi cambi di contesto espliciti o impliciti.  
  
## <a name="permissions"></a>Permissions  
 Per specificare **EXECUTE AS** un account di accesso, il chiamante deve disporre **IMPERSONATE** sull'account di accesso specificato un nome e non deve essere negato il **IMPERSONATE ANY LOGIN** autorizzazione . Per specificare **EXECUTE AS** per un utente del database, il chiamante deve disporre **IMPERSONATE** le autorizzazioni per il nome utente specificato. Quando **EXECUTE AS CALLER** è specificato, **IMPERSONATE** non sono necessarie autorizzazioni.  
  
## <a name="examples"></a>Esempi  
  
###  <a name="_exampleA"></a> A. Utilizzo di EXECUTE AS e REVERT per cambiare contesto  
 Nell'esempio seguente viene creato uno stack di contesti di esecuzione utilizzando più entità. Viene quindi utilizzata l'istruzione `REVERT` per ripristinare il contesto di esecuzione al chiamante precedente. L'istruzione `REVERT` viene eseguita più volte per innalzare di livello lo stack finché il contesto di esecuzione viene impostato sul chiamante originale.  
  
```  
USE AdventureWorks2012;  
GO  
--Create two temporary principals  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE LOGIN login2 WITH PASSWORD = 'Uor80$23b';  
GO  
CREATE USER user1 FOR LOGIN login1;  
CREATE USER user2 FOR LOGIN login2;  
GO  
--Give IMPERSONATE permissions on user2 to user1  
--so that user1 can successfully set the execution context to user2.  
GRANT IMPERSONATE ON USER:: user2 TO user1;  
GO  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- Set the execution context to login1.   
EXECUTE AS LOGIN = 'login1';  
--Verify the execution context is now login1.  
SELECT SUSER_NAME(), USER_NAME();  
--Login1 sets the execution context to login2.  
EXECUTE AS USER = 'user2';  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- The execution context stack now has three principals: the originating caller, login1 and login2.  
--The following REVERT statements will reset the execution context to the previous context.  
REVERT;  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
REVERT;  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
  
--Remove temporary principals.  
DROP LOGIN login1;  
DROP LOGIN login2;  
DROP USER user1;  
DROP USER user2;  
GO  
```  
  
### <a name="b-using-the-with-cookie-clause"></a>B. Utilizzo della clausola WITH COOKIE  
 Nell'esempio seguente imposta il contesto di esecuzione di una sessione a un utente specificato e specifica di WITH NO REVERT COOKIE = @*varbinary_variabl*clausola. Nell'istruzione `REVERT` è necessario specificare il valore passato alla variabile `@cookie` nell'istruzione `EXECUTE AS` per ripristinare correttamente il contesto al chiamante originale. Per eseguire questo esempio, l'account di accesso `login1` e l'utente `user1` creato nell'esempio A devono esistere.  
  
```  
DECLARE @cookie varbinary(8000);  
EXECUTE AS USER = 'user1' WITH COOKIE INTO @cookie;  
-- Store the cookie in a safe location in your application.  
-- Verify the context switch.  
SELECT SUSER_NAME(), USER_NAME();  
--Display the cookie value.  
SELECT @cookie;  
GO  
-- Use the cookie in the REVERT statement.  
DECLARE @cookie varbinary(8000);  
-- Set the cookie value to the one from the SELECT @cookie statement.  
SET @cookie = <value from the SELECT @cookie statement>;  
REVERT WITH COOKIE = @cookie;  
-- Verify the context switch reverted.  
SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristina &#40; Transact-SQL &#41;](../../t-sql/statements/revert-transact-sql.md)   
 [EXECUTE AS clausola &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)  
  
  

