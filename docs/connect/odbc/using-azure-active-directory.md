---
title: Utilizzo di Azure Active Directory con il Driver ODBC | Documenti di Microsoft per SQL Server
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6af10b10a3b2669dceb1035f38f3099c5b3177b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Utilizzo di Azure Active Directory con il Driver ODBC
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Scopo

Microsoft ODBC Driver for SQL Server con versione 13.1 o versioni successive consente alle applicazioni ODBC per connettersi a un'istanza di SQL Azure utilizzando un'identità federata in Azure Active Directory con un nome utente/password, un token di accesso di Azure Active Directory o Windows L'autenticazione integrata (_solo i driver di Windows_). Per il Driver ODBC versione 13.1, l'accesso di Azure Active Directory è l'autenticazione con token _solo Windows_. Il tuffatore ODBC versione 17 e 17.1 supportano l'autenticazione tra tutte le piattaforme (Windows, Linux e Mac). Una nuova autenticazione interattiva di Azure Active Directory con ID di accesso è stato introdotto nella versione 17.1 del Driver ODBC per Windows. Tutti questi vengono eseguiti tramite l'utilizzo di DSN nuovi e parole chiave delle stringhe di connessione e gli attributi di connessione.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>DSN nuovi e/o modificato e parole chiave delle stringhe di connessione

Il `Authentication` parola chiave può essere utilizzata quando ci si connette con una stringa di connessione o DSN per controllare la modalità di autenticazione. Il valore impostato nella stringa di connessione esegue l'override che nel DSN, se fornita. Il _pre-valore dell'attributo_ del `Authentication` è il valore calcolato dai valori DSN e stringa di connessione.

|Nome|Valori|Valore predefinito|Description|
|-|-|-|-|
|`Authentication`|(non impostato), (una stringa vuota), `SqlPassword`, `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`|(non impostato)|Controlla la modalità di autenticazione.<table><tr><th>Value<th>Description<tr><td>(non impostato)<td>Modalità di autenticazione di base a parole chiave (opzioni di connessione preesistenti esistente).<tr><td>(stringa vuota)<td>(Stringa di connessione solo.) Eseguire l'override e annullare un `Authentication` valore impostato nel DSN.<tr><td>`SqlPassword`<td>Eseguire l'autenticazione direttamente a un'istanza di SQL Server utilizzando un nome utente e password.<tr><td>`ActiveDirectoryPassword`<td>Eseguire l'autenticazione con un'identità di Azure Active Directory utilizzando un nome utente e password.<tr><td>`ActiveDirectoryIntegrated`<td>_Solo i driver di Windows_. Eseguire l'autenticazione con un'identità di Azure Active Directory utilizzando l'autenticazione integrata.<tr><td>`ActiveDirectoryInteractive`<td>_Solo i driver di Windows_. Eseguire l'autenticazione con un'identità di Azure Active Directory utilizzando l'autenticazione interattiva.</table>|
|`Encrypt`|(non impostato), `Yes`, `No`|(vedere la descrizione)|Controlla la crittografia per una connessione. Se il valore pre-dell'attributo di il `Authentication` non _Nessuno_, il valore predefinito è `Yes`. In caso contrario, il valore predefinito è `No`. Il valore pre-dell'attributo di crittografia `Yes` se il valore è impostato su `Yes` nella stringa di connessione o DSN.|

## <a name="new-andor-modified-connection-attributes"></a>Attributi di connessione di nuovo e/o modificato

Di seguito pre-connessione gli attributi sono stati introdotti o modificati per supportare l'autenticazione di Azure Active Directory. Quando un attributo di connessione è una stringa di connessione corrispondente o una parola chiave DSN e viene impostato, l'attributo di connessione ha la precedenza.

|Attribute|Tipo|Valori|Valore predefinito|Description|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_RESET`|(non impostato)|Vedere la descrizione di `Authentication` parola chiave precedente. `SQL_AU_NONE` viene fornito per eseguire l'override esplicito di un set `Authentication` valore nella stringa di DSN e/o di connessione, mentre `SQL_AU_RESET` deseleziona l'attributo se è stata impostata, consentendo il valore di stringa di connessione o DSN a hanno la precedenza.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Puntatore a `ACCESSTOKEN` o NULL|NULL|Se diverso da null, specifica il Token azuread dell'accesso da utilizzare. È possibile specificare un token di accesso e anche `UID`, `PWD`, `Trusted_Connection`, o `Authentication` parole chiave delle stringhe di connessione o dei relativi attributi equivalente. <br> **Nota:** ODBC Driver 13.1 versione solo questa funzionalità è supportata sul _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(vedere la descrizione)|Controlla la crittografia per una connessione. `SQL_EN_OFF` e `SQL_EN_ON` disabilitare e abilitare la crittografia, rispettivamente. Se il valore pre-dell'attributo di il `Authentication` non _Nessuno_ o `SQL_COPT_SS_ACCESS_TOKEN` è impostata, e `Encrypt` non è stato specificato nella stringa di connessione o DSN, il valore predefinito è `SQL_EN_ON`. In caso contrario, il valore predefinito è `SQL_EN_OFF`. Il valore effettivo dei controlli attributo [se la crittografia verrà utilizzata per la connessione.](https://docs.microsoft.com/en-us/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Non è supportata con Azure Active Directory, poiché le modifiche delle password per le entità di AAD non può essere eseguite tramite una connessione ODBC. <br><br>Scadenza della password per l'autenticazione di SQL Server è stato introdotto in SQL Server 2005. Il `SQL_COPT_SS_OLDPWD` attributo è stato aggiunto per consentire al client di fornire sia la vecchia che la nuova password per la connessione. Quando questa proprietà è impostata, il provider non utilizzerà il pool di connessioni per la prima connessione o per le connessioni successive, in quanto la stringa di connessione conterrà la password precedente che è stata modificata.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Deprecato_; usare `SQL_COPT_SS_AUTHENTICATION` impostato su `SQL_AU_AD_INTEGRATED` invece. <br><br>Forza utilizzo dell'autenticazione di Windows (Kerberos su Linux e macOS) per la convalida dell'accesso in account di accesso server. Quando viene utilizzata l'autenticazione di Windows, il driver ignora i valori di identificatore e la password utente forniti come parte di `SQLConnect`, `SQLDriverConnect`, o `SQLBrowseConnect` l'elaborazione.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Componenti aggiuntivi dell'interfaccia utente per Azure Active Directory (solo per i driver di Windows)

L'installazione DSN e la connessione, le interfacce utente del driver sono stati migliorati con le opzioni aggiuntive necessarie per utilizzare l'autenticazione con Azure AD.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Creazione e modifica i DSN nell'interfaccia utente

È possibile utilizzare di nuovo AD Azure le opzioni di autenticazione durante la creazione o la modifica di un DSN esistente tramite l'installazione del driver dell'interfaccia utente:

`Authentication=ActiveDirectoryIntegrated` per l'autenticazione di Azure Active Directory Integrated a SQL Azure

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword` per l'autenticazione di nome utente/password di Azure Active Directory in SQL Azure

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` per l'autenticazione interattiva di Azure Active Directory in SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword` per l'autenticazione di nome utente/password a SQL Server (Azure o in caso contrario)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes` per Windows SSPI legacy l'autenticazione integrata

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

Le cinque opzioni corrispondono alle `Trusted_Connection=Yes` (Windows legacy esistente SSPI sola l'autenticazione integrata) e `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryPassword`, e `ActiveDirectoryInteractive`, rispettivamente.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect prompt dei comandi (solo per i driver di Windows)

La finestra di dialogo dei messaggi di richiesta visualizzato dal SQLDriverConnect quando vengono richieste informazioni necessarie per completare la connessione contiene tre nuove opzioni per l'autenticazione di Azure AD:

![ServerLogin.png](windows/ServerLogin.png)

Queste opzioni corrispondono ai cinque stesso disponibili nel programma di installazione DSN dell'interfaccia utente precedente.

### <a name="example-connection-strings"></a>Esempi di stringhe di connessione
1. Autenticazione di SQL Server: sintassi legacy. Certificato server non viene convalidato e viene utilizzata la crittografia solo se il server impone. Il nome utente e la password viene passata nella stringa di connessione.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. Autenticazione di SQL: nuova sintassi. Il client richiede la crittografia (il valore predefinito di `Encrypt` è `true`) e il certificato del server ottiene convalidato, indipendentemente dall'impostazione di crittografia (a meno che non `TrustServerCertificate` è impostato su `true`). Il nome utente e la password viene passata nella stringa di connessione.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Autenticazione integrata di Windows (Kerberos su Linux e macOS) tramite SSPI (per SQL Server o SQL IaaS): la sintassi corrente. Certificato server non viene convalidato, a meno che non viene utilizzata la crittografia. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Solo i driver di Windows_.) Autenticazione integrata di Windows tramite SSPI (se il database di destinazione è in SQL Server o SQL IaaS)-nuova sintassi. Il client richiede la crittografia (il valore predefinito di `Encrypt` è `true`) e il certificato del server ottiene convalidato, indipendentemente dall'impostazione di crittografia (a meno che non `TrustServerCertificate` è impostato su `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Autenticazione di nome utente e Password di AAD (se il database di destinazione nel database di SQL Azure). Certificato server è convalidato, indipendentemente dall'impostazione di crittografia (a meno che non `TrustServerCertificate` è impostato su `true`). Il nome utente e la password viene passata nella stringa di connessione. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Solo i driver di Windows_.) Autenticazione integrata di Windows utilizza la libreria ADAL, che prevede di utilizzare le credenziali dell'account di Windows per un token di accesso rilasciato da Azure ad, presupponendo che il database di destinazione è in Database SQL di Azure. Certificato server è convalidato, indipendentemente dall'impostazione di crittografia (a meno che non `TrustServerCertificate` è impostato su `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Solo i driver di Windows_.) Autenticazione interattivo AAD utilizza la tecnologia di Azure multi-factor Authentication per impostare connessione. In questa modalità, fornendo l'ID di accesso, una finestra di dialogo di autenticazione di Windows Azure viene attivata e consente all'utente di immettere la password per completare la connessione. Il nome utente viene passato nella stringa di connessione.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

> [!NOTE] 
>- Quando si utilizzano le nuove opzioni di Active Directory con il driver ODBC di Windows, assicurarsi che il [Active Directory Authentication Library per SQL Server](http://go.microsoft.com/fwlink/?LinkID=513072) è stato installato. I driver di Linux e macOS non richiedono le dipendenze aggiuntive per l'autenticazione con Azure Active Directory.
>- Per connettersi usando un nome utente account SQL Server e una password, è ora possibile utilizzare il nuovo `SqlPassword` opzione, è consigliabile soprattutto per SQL Azure, poiché questa opzione consente di impostazioni predefinite di connessione più sicure.
>- Per connettersi usando un nome utente account Azure Active Directory e una password, specificare `Authentication=ActiveDirectoryPassword` nella stringa di connessione e `UID` e `PWD` le parole chiave con il nome utente e password, rispettivamente.
>- Per connettersi usando integrata di Windows o autenticazione integrata di Active Directory (solo per i driver di Windows), specificare `Authentication=ActiveDirectoryIntegrated` nella stringa di connessione. Il driver sceglierà automaticamente la modalità di autenticazione corretto. `UID` e `PWD` non deve essere specificato.
>- Per connettersi utilizzando l'autenticazione di Active Directory interattiva (solo driver di Windows), `UID` deve essere specificato.

## <a name="authenticating-with-an-access-token"></a>L'autenticazione con un Token di accesso

Il `SQL_COPT_SS_ACCESS_TOKEN` attributo pre-connessione consente di usare un token di accesso ottenuto da Azure AD per l'autenticazione anziché nome utente e password e ignora inoltre la negoziazione e ottenere un token di accesso dal driver. Per utilizzare un token di accesso, impostare il `SQL_COPT_SS_ACCESS_TOKEN` attributo di connessione a un puntatore a un `ACCESSTOKEN` struttura:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

Il `ACCESSTOKEN` è una struttura di lunghezza variabile costituita da 4 byte _lunghezza_ seguito da _lunghezza_ byte di dati opachi che formano il token di accesso. A causa di come SQL Server gestisce i token di accesso, una ottenuto tramite un [OAuth 2.0](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-scenarios) risposta JSON deve essere espanso in modo che ogni byte è seguita da uno 0 byte, simili a una stringa di UCS-2 contenente solo caratteri ASCII di padding; tuttavia, il token è un valore opaco e la lunghezza specificata, in byte, non devono includere qualsiasi carattere di terminazione null. I vincoli di lunghezza e il formato considerevoli, a causa di questo metodo di autenticazione è disponibile solo a livello di programmazione tramite le `SQL_COPT_SS_ACCESS_TOKEN` attributo coonnection; Nessuna corrispondente DSN o la parola chiave di stringa di connessione. La stringa di connessione non deve contenere `UID`, `PWD`, `Authentication`, o `Trusted_Connection` parole chiave.

> [!NOTE]
> Il Driver ODBC versione 13.1 supporta solo l'autenticazione nel _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Codice di esempio l'autenticazione di Azure Active Directory

L'esempio seguente viene illustrato il codice necessario per connettersi a SQL Server tramite Azure Active Directory con le parole chiave di connessione. Si noti che non è necessario modificare il codice dell'applicazione stessa. la stringa di connessione o DSN se viene utilizzato uno, è l'unica modifica da apportare necessaria per l'utilizzo di Azure ad per l'autenticazione:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
L'esempio seguente viene illustrato il codice necessario per connettersi a SQL Server con l'autenticazione del token di accesso di Azure Active Directory. In questo caso, è necessario modificare il codice dell'applicazione per elaborare il token di accesso e impostare l'attributo di connessione associata.
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server}"
    SQLCHAR accessToken[] = "eyJ0eXAiOi..."; // In the format extracted from an OAuth JSON response
    ...
    DWORD dataSize = 2 * strlen(accessToken);
    ACCESSTOKEN *pAccToken = malloc(sizeof(ACCESSTOKEN) + dataSize);
    pAccToken->dataSize = dataSize;
    // Expand access token with padding bytes
    for(int i = 0, j = 0; i < dataSize; i += 2, j++) {
        pAccToken->data[i] = accessToken[j];
        pAccToken->data[i+1] = 0;
    }
    ...
    SQLSetConnectAttr(hDbc, SQL_COPT_SS_ACCESS_TOKEN, (SQLPOINTER)pAccToken, SQL_IS_POINTER);
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);      
    ...
    free(pAccToken);
~~~
Di seguito è una stringa di connessione di esempio per l'utilizzo con Azure Active Directory interattivo Authentication. Si noti che non contiene campi PWD come verrebbe immesso la password utilizzando l'autenticazione di Windows Azure schermo.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~

## <a name="see-also"></a>Vedere anche
[Supporto dell'autenticazione basata su token per il database di SQL Azure utilizzando l'autenticazione di Azure AD](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

