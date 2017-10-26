---
title: Connessione tramite autenticazione di Azure Active Directory | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.topic: article
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 83d5ad3bae131b58dd344c3f5f9bfc7f5d0c4f5a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-using-azure-active-directory-authentication"></a>Connessione tramite autenticazione di Azure Active Directory
Questo articolo fornisce informazioni su come sviluppare applicazioni Java per utilizzare la funzionalità di autenticazione di Azure Active Directory con Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server.

A partire da Microsoft JDBC Driver 6.0 per SQL Server, è possibile utilizzare l'autenticazione di Azure Active Direcoty (AAD) che è un meccanismo di connessione al Database SQL di Azure v12 usando le identità in Azure Active Directory. Utilizzare l'autenticazione di Azure Active Directory per gestire centralmente le identità di utenti del database e come alternativa all'autenticazione di SQL Server. Il Driver JDBC 6.0 (o versione successiva) consente di specificare le credenziali di Azure Active Directory nella stringa di connessione JDBC per connettersi al database SQL di Azure. Per informazioni su come configurare l'autenticazione di Azure Active Directory, visitare [la connessione al Database SQL da usando Azure Active Directory l'autenticazione](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Due nuove proprietà di connessione sono state aggiunte per supportare l'autenticazione di Azure Active Directory:
*   **autenticazione**: utilizzare questa proprietà per indicare il metodo di autenticazione SQL da utilizzare per la connessione. I valori possibili sono: **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword** e il valore predefinito **NotSpecified** .
    * Usare ' authentication = ActiveDirectoryIntegrated' per la connessione a un Database SQL tramite l'autenticazione integrata di Windows. Per utilizzare questa modalità di autenticazione è necessario stabilire una federazione di locali Active Directory Federation Services (ADFS) con Azure AD nel cloud. Dopo aver attivato il programma di installazione, è possibile accedere a database SQL di Azure senza che venga richiesto ceredentials quando si è connessi in un computer appartenente a un dominio. 
    * Usare ' authentication = ActiveDirectoryPassword' per la connessione a un Database di SQL utilizzando un nome dell'entità di Azure AD e una password.
    * Usare ' authentication = SqlPassword' per la connessione a SQL Server utilizzando le proprietà di nome utente/utente e password.
    * Usare ' authentication = NotSpecified' o lasciare il campo come valore predefinito se nessuno di questi metodi di autenticazione è necessaria.

*   **accessToken**: utilizzare questa proprietà per connettersi a un database SQL tramite un token di accesso. accessToken può essere impostato solo utilizzando il parametro di proprietà del metodo getConnection() nella classe DriverManager. Non può essere utilizzato nell'URL della connessione.  

Per informazioni dettagliate, vedere la proprietà di autenticazione nel [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md) pagina.  


## <a name="client-setup-requirements"></a>Requisiti di installazione client
Assicurarsi che i componenti seguenti siano installati nel computer client:
* Java 7 o versione successiva
*   6.2 (o versione successiva) di Microsoft JDBC Driver per SQL Server
*   Se si utilizza la modalità di autenticazione basata su token di accesso, sarà necessario [azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze per eseguire gli esempi in questo articolo. Vedere **connessione tramite Token di accesso** sezione per ulteriori dettagli.
*   Se si utilizza la modalità di autenticazione ActiveDirectoryPassword occorre [azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze. Vedere **connessione mediante la modalità di autenticazione ActiveDirectoryPassword** sezione per ulteriori dettagli.
*   Se si utilizza la modalità ActiveDirectoryIntegrated, è necessario installare Active Directory Authentication Library per SQL Server (ADALSQL. DLL) e di sqljdbc_auth.dll.
    * ADALSQL. DLL consente alle applicazioni di eseguire l'autenticazione al Database SQL di Microsoft Azure tramite Azure Active Directory. Scaricare la DLL di [Microsoft Active Directory Authentication Library per Microsoft SQL Server](http://www.microsoft.com/en-us/download/details.aspx?id=48742)
    * Per ADALSQL. DLL binarie X86 e X64 sono disponibili due versioni per il download. Se è installata la versione binaria errata o se la DLL è manca, il driver genera l'errore seguente: "Impossibile caricare adalsql.dll (Authentication =...). Codice di errore: 0x2. ". In tal caso, scaricare la versione corretta del ADALSQL. DLL. 
    * sqljdbc_auth.dll è disponibile nel pacchetto driver. Copiare il file sqljdbc_auth.dll in una directory nel percorso di sistema di Windows nel computer in cui è installato il driver JDBC. In alternativa è possibile impostare la proprietà di sistema java.libary.path in modo da specificare la directory di sqljdbc_auth.dll. 
    * Se si esegue JVM a 64 bit in un processore x64, utilizzare il file sqljdbc_auth.dll nella cartella x64. 
    * Se si esegue Java Virtual Machine (JVM) a 32 bit, utilizzare il file sqljdbc_auth.dll nella cartella x86, anche se la versione del sistema operativo è x64. 
    * Ad esempio, se si utilizza la JVM a 32 bit e il driver JDBC è installato nella directory predefinita, è possibile specificare il percorso della DLL con il seguente argomento della macchina virtuale (VM) quando viene avviata l'applicazione Java:  
        ```
        -Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86
        ```
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Connessione tramite la modalità di autenticazione ActiveDirectoryIntegrated
Nell'esempio seguente viene illustrato come utilizzare ' authentication = ActiveDirectoryIntegrated' modalità. Eseguire questo esempio in un computer aggiunti a un dominio federato con Azure Active Directory. Un utente del database indipendente che rappresenta l'entità di Azure AD, o uno dei gruppi, si appartiene al, deve esistere nel database e deve disporre dell'autorizzazione CONNECT. 
    
Prima di eseguire l'esempio, sostituire il nome del server/database con il nome del server/database nelle righe seguenti:

```
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

L'esempio per utilizzare la modalità di autenticazione ActiveDirectoryIntegrated:
```
import java.sql.Connection;
import java.sql.ResultSet;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class IntegratedExample {

    public static void main(String[] args) throws Exception {
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");
        ds.setHostNameInCertificate("*.database.windows.net");

        Connection connection = ds.getConnection();

        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
```
Eseguire questo esempio in un computer aggiunto a un dominio federato con Azure Active Directory utilizzerà automaticamente le credenziali di Windows e password non è necessaria. Se viene stabilita una connessione, si verrà visualizzato il messaggio seguente:
```
You have successfully logged on as: <your domain user name>
```

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Connessione tramite la modalità di autenticazione ActiveDirectoryPassword
Nell'esempio seguente viene illustrato come utilizzare ' authentication = ActiveDirectoryPassword' modalità.

Prima di compilare ed eseguire l'esempio:
1.  Nel computer client (in cui, si desidera eseguire l'esempio), scaricare il [libreria di azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze e includerli nel percorso di compilazione Java
2.  Individuare le seguenti righe di codice e sostituire il nome del server/database con il nome del server/database.
    ```
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  Individuare le seguenti righe di codice e sostituire il nome utente, con il nome dell'utente di Azure AD a cui che si desidera connettersi come.
    ```
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

L'esempio per utilizzare la modalità di autenticazione ActiveDirectoryPassword:
```
import java.sql.Connection;
import java.sql.ResultSet;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class UserPasswordExample {
    
    public static void main(String[] args) throws Exception{
        SQLServerDataSource ds = new SQLServerDataSource();
        
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        ds.setHostNameInCertificate("*.database.windows.net");
        
        Connection connection = ds.getConnection();
        
        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
```
Se viene stabilita una connessione, si verrà visualizzato il seguente messaggio di output:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Deve essere presente un database utente indipendente e un utente del database indipendente che rappresenta il parametro utente AD Azure o uno dei gruppi di Azure specificato appartiene a utente di Active Directory, deve esistere nel database e deve disporre dell'autorizzazione CONNECT (ad eccezione di Azure Active Directory amministratore del server o gruppo)


## <a name="connecting-using-access-token"></a>Connessione tramite Token di accesso
Applicazioni/servizi è possibile recuperare un token di accesso da Azure Active Directory e usarla per connettersi al Database di SQL Azure. Si noti che accessToken può essere impostata solo utilizzando il parametro di proprietà del metodo getConnection() nella classe DriverManager. Non può essere utilizzato nella stringa di connessione.
 
Nell'esempio seguente contiene una semplice applicazione Java che si connette al Database di SQL Azure utilizzando l'autenticazione basata su token di accesso. Prima di compilare ed eseguire l'esempio, eseguire la procedura seguente:
1.  Creare un account di applicazione in Azure Active Directory per il servizio.
    1. Accedi al portale di gestione di Azure
    2. Fare clic su Azure Active Directory nel riquadro di spostamento a sinistra
    3. Fare clic su tenant di directory in cui si desidera registrare l'applicazione di esempio. Deve essere la stessa directory in cui è associata il database (server che ospita il database).
    4. Fare clic sulla scheda applicazioni.
    5. Nel cassetto, fare clic su Aggiungi.
    6. Fare clic su "Aggiungi un'applicazione che l'organizzazione sta sviluppando".
    7. Immettere mytokentest come un nome descrittivo per l'applicazione, selezionare "Applicazione di Web e/o API Web" e fare clic su Avanti.
    8. Supponendo che l'applicazione è un servizio/daemon e non è un'applicazione web, non ha un accesso URL o URI ID app. Per questi due campi, immettere http://mytokentest
    9. Nel portale di Azure, fare clic sulla scheda Configura dell'applicazione
    10. Trovare il valore dell'ID Client e copiarlo, sarà necessaria in un secondo momento durante la configurazione dell'applicazione (ad esempio  a4bbfe26-dbaa-4fec-8ef5-223d229f647d). Vedere lo snapshot seguente.
    11. Nella sezione "Chiavi", selezionare la durata della chiave, salvare la configurazione e copiare la chiave per un uso successivo. Questo è il segreto client.
    12. Nella parte inferiore, fare clic su "Visualizza endpoint" e copiare l'URL in "ENDPOINT di autorizzazione OAUTH 2.0" per un uso successivo. Si tratta dell'URL di servizio token di sicurezza.


![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)


2. Accesso al database del Server SQL Azure come un amministratore di Azure Active Directory e l'utilizzo di un utente del database indipendente una disposizione di comando T-SQL per l'entità di applicazione. Vedere il [la connessione al Database SQL o Data Warehouse da usando Azure Active Directory l'autenticazione di SQL](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/) per ulteriori informazioni su come creare un amministratore di Azure Active Directory e un utente del database indipendente.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  Nel computer client (in cui, si desidera eseguire l'esempio), scaricare il [azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) libreria e le relative dipendenze e includerli nel percorso di compilazione Java. Si noti che azure-activedirectory-libreria-per-java è solo necessario per eseguire questo esempio specifico, in quanto utilizza le API da questa raccolta per recuperare il token di accesso da Azure AD. Se si dispone già di un token di accesso, è possibile ignorare questo passaggio. Si noti che è anche necessario rimuovere la sezione nell'esempio che recupera il token di accesso.

Nell'esempio seguente, sostituire l'URL di servizio token di sicurezza, ID Client, segreto Client, server e nome del database con i valori.

```
import java.sql.Connection;
import java.sql.ResultSet;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD. 
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;


public class TokenBasedExample {

    public static void main(String[] args) throws Exception{

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
        String clientId = "a4bbfe26-dbaa-4fec-8ef5-223d229f647d"; // Replace with your client ID.
        String clientSecret = "..."; // Replace with your client secret.

        AuthenticationContext context = new AuthenticationContext(stsurl, false, Executors.newFixedThreadPool(1));
        ClientCredential cred = new ClientCredential(clientId, clientSecret);

        Future<AuthenticationResult> future = context.acquireToken(spn, cred, null);
        String accessToken = future.get().getAccessToken();

        System.out.println("Access Token: " + accessToken);     
        
        // Connect with the access token.
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name.
        ds.setDatabaseName("demo"); // Replace with your database name.
        ds.setAccessToken(accessToken);
        ds.setHostNameInCertificate("*.database.windows.net");

        Connection connection = ds.getConnection();

        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
``` 

Se la connessione ha esito positivo, si verrà visualizzato il seguente messaggio di output:
```
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 

