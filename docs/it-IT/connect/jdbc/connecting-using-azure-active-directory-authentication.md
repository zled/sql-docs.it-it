---
title: Connessione tramite autenticazione di Azure Active Directory | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.technology:
- drivers
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8ee49e767d8d0b92b1c8a6548b8870822460fa6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Connessione tramite autenticazione di Azure Active Directory

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Questo articolo fornisce informazioni su come sviluppare applicazioni Java per utilizzare la funzionalità di autenticazione di Azure Active Directory con Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server.

È possibile utilizzare l'autenticazione di Azure Active Directory (AAD), che è un meccanismo di connessione al Database SQL di Azure v12 usando le identità in Azure Active Directory. Utilizzare l'autenticazione di Azure Active Directory per gestire centralmente le identità di utenti del database e come alternativa all'autenticazione di SQL Server. Il Driver JDBC consente di specificare le credenziali di Azure Active Directory nella stringa di connessione JDBC per connettersi al database SQL di Azure. Per informazioni su come configurare l'autenticazione di Azure Active Directory, visitare [la connessione al Database SQL da usando Azure Active Directory l'autenticazione](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Due nuove proprietà di connessione sono state aggiunte per supportare l'autenticazione di Azure Active Directory:
*   **autenticazione**: utilizzare questa proprietà per indicare il metodo di autenticazione SQL da utilizzare per la connessione. I valori possibili sono: **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword**e il valore predefinito **NotSpecified**.
    * Usare ' authentication = ActiveDirectoryIntegrated' per la connessione a un Database SQL tramite l'autenticazione integrata di Windows. Per utilizzare questa modalità di autenticazione, è necessario stabilire una federazione di locali Active Directory Federation Services (ADFS) con Azure AD nel cloud. Dopo la configurazione e un ticket Kerberos, è possibile accedere a database SQL di Azure senza la richiesta di credenziali quando si è connessi in un computer appartenente a un dominio. 
    * Usare ' authentication = ActiveDirectoryPassword' per la connessione a un Database di SQL utilizzando un nome dell'entità di Azure AD e una password.
    * Usare ' authentication = SqlPassword' per la connessione a SQL Server utilizzando le proprietà di nome utente/utente e password.
    * Usare ' authentication = NotSpecified' o lasciare il campo come valore predefinito quando nessuno di questi metodi di autenticazione sono necessari.

*   **accessToken**: utilizzare questa proprietà per connettersi a un database SQL tramite un token di accesso. accessToken può essere impostato solo utilizzando il parametro di proprietà del metodo getConnection() nella classe DriverManager. Non può essere utilizzato nell'URL della connessione.  

Per informazioni dettagliate, vedere la proprietà di autenticazione nel [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md) pagina.  


## <a name="client-setup-requirements"></a>Requisiti di installazione client
Assicurarsi che i componenti seguenti siano installati nel computer client:
* Java 7 o versione successiva
*   Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server
*   Se si utilizza la modalità di autenticazione basata su token di accesso, è necessario [azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze per eseguire gli esempi in questo articolo. Per ulteriori informazioni, vedere **connessione tramite Token di accesso** sezione.
*   Se si utilizza la modalità di autenticazione ActiveDirectoryPassword, è necessario [azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze. Per ulteriori informazioni, vedere **connessione mediante la modalità di autenticazione ActiveDirectoryPassword** sezione.
*   Se si utilizza la modalità ActiveDirectoryIntegrated, è necessario azure-activedirectory-libreria-per-java e le relative dipendenze. Per ulteriori informazioni, vedere **connessione mediante la modalità di autenticazione ActiveDirectoryIntegrated** sezione.
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Connessione tramite la modalità di autenticazione ActiveDirectoryIntegrated
 Con la versione 6.4, Microsoft JDBC Driver aggiunge il supporto per l'autenticazione ActiveDirectoryIntegrated mediante un ticket Kerberos su più piattaforme (Windows/Linux e Mac).
Vedere [ticket Kerberos impostato su Windows, Linux e Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) per altri dettagli. In alternativa, in Windows, sqljdbc_auth.dll anche utilizzabile per l'autenticazione ActiveDirectoryIntegrated con il Driver JDBC.

> [!NOTE]
>  Selezionare questa opzione se si utilizza una versione precedente del driver, [collegamento](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) per le rispettive dipendenze che devono utilizzare questa modalità di autenticazione. 

Nell'esempio seguente viene illustrato come utilizzare ' authentication = ActiveDirectoryIntegrated' modalità. Eseguire questo esempio in un computer aggiunti a un dominio federato con Azure Active Directory. Un utente del database indipendente che rappresenta l'entità di Azure AD, o uno dei gruppi, si appartiene al, deve esistere nel database e deve disporre dell'autorizzazione CONNECT. 

Prima di compilare ed eseguire l'esempio, nel computer client (in cui, si desidera eseguire l'esempio), scaricare il [libreria di azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze e includerli nel percorso di compilazione Java

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
Esecuzione automatica di questo esempio in un computer client utilizza il ticket Kerberos e password non è necessaria. Se viene stabilita una connessione, è visualizzato il messaggio seguente:
```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Impostare il ticket Kerberos in Windows, Linux e Mac

È necessario impostare un ticket Kerberos, il collegamento all'utente corrente a un account di dominio di Windows. Ecco un riepilogo dei passaggi principali.

#### <a name="windows"></a>Windows
JDK fornito con `kinit` che è possibile utilizzare per ottenere un ticket TGT dal KDC (Key Distribution Center) in un dominio aggiunti a un computer in cui è federata con Azure Active Directory.

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>Passaggio 1: Il recupero di Ticket di concessione Ticket
- **Eseguire in**: Windows
- **Azione**:
  - Utilizzare il comando `kinit username@DOMAIN.COMPANY.COM` per ottenere un ticket TGT dal KDC, quindi verrà chiesto di specificare la password di dominio.
  - Utilizzare `klist` per visualizzare il ticket disponibile. Se il kinit ha avuto esito positivo, verrà visualizzato un ticket da krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

> [!NOTE]
>  È necessario specificare un `.ini` file con `-Djava.security.krb5.conf` per l'applicazione individuare KDC.

#### <a name="linux-and-mac"></a>Linux e Mac

##### <a name="requirements"></a>Requisiti
Accedere a un computer appartenenti a un dominio di Windows per eseguire query di Controller di dominio Kerberos

##### <a name="step-1-find-kerberos-kdc"></a>Passaggio 1: Trovare Kerberos KDC
- **Eseguire in**: riga di comando di Windows
- **Azione**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (dove "DOMAIN.COMPANY.COM" esegue il mapping al nome del dominio)
- **Esempio di output**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **Informazioni per estrarre** denominare il controller di dominio, in questo caso `co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>Passaggio 2: Configurazione KDC in krb5
- **Eseguire in**: Linux/Mac
- **Azione**: modificare /etc/krb5.conf in un editor di propria scelta. Configurare le chiavi seguenti
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  Quindi salvare il file krb5 conf e uscita

> [!NOTE]
>  Dominio deve essere in lettere maiuscole.

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>Passaggio 3: Test il recupero di Ticket di concessione Ticket
- **Eseguire in**: Linux/Mac
- **Azione**:
  - Utilizzare il comando `kinit username@DOMAIN.COMPANY.COM` per ottenere un ticket TGT dal KDC, quindi verrà chiesto di specificare la password di dominio.
  - Utilizzare `klist` per visualizzare il ticket disponibile. Se il kinit ha avuto esito positivo, verrà visualizzato un ticket da krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

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
Se viene stabilita una connessione, vedrai il seguente messaggio di output:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Deve essere presente un database utente indipendente e un utente del database indipendente che rappresenta il parametro utente AD Azure o uno dei gruppi di Azure specificato appartiene a utente di Active Directory, deve esistere nel database e deve disporre dell'autorizzazione CONNECT (ad eccezione di Azure Active Directory amministratore del server o gruppo)


## <a name="connecting-using-access-token"></a>Connessione tramite Token di accesso
Applicazioni/servizi è possibile recuperare un token di accesso da Azure Active Directory e usarla per connettersi al Database di SQL Azure. Si noti che accessToken può essere impostata solo utilizzando il parametro di proprietà del metodo getConnection() nella classe DriverManager. Non può essere utilizzato nella stringa di connessione.
 
Nell'esempio seguente contiene una semplice applicazione Java che si connette al Database di SQL Azure mediante l'autenticazione basata su token di accesso. Prima di compilare ed eseguire l'esempio, eseguire la procedura seguente:
1.  Creare un account di applicazione in Azure Active Directory per il servizio.
    1. Accedi al portale di gestione di Azure
    2. Fare clic su Azure Active Directory nel riquadro di spostamento a sinistra
    3. Fare clic sulla scheda "Registrazioni di App".
    4. Nel cassetto, fare clic su "Nuova registrazione dell'applicazione".
    5. Immettere mytokentest come un nome descrittivo per l'applicazione, selezionare "App/API Web".
    6. URL accesso non è necessaria. Sufficiente fornire un valore: "http://mytokentest".
    7. Fare clic su "Crea" nella parte inferiore.
    9. Nel portale di Azure, fare clic sulla scheda "Impostazioni" dell'applicazione e aprire la scheda "Proprietà".
    10. Trovare il valore "ID applicazione" (noto anche come ID Client) e copiarlo riservato, necessaria in fase di configurazione dell'applicazione (ad esempio, 1846943b-ad04-4808-aa13-4702d908b5c1). Vedere il seguente snapshot.
    11. Trovare il valore "URL ID App" e copiarlo, si tratta dell'URL di servizio token di sicurezza.
    12. Nella sezione "Chiavi", creare una chiave per la compilazione nel campo nome, selezionando la durata della chiave e il salvataggio della configurazione (lasciare vuoto il campo valore). Dopo il salvataggio, il campo valore deve essere compilato automaticamente, copiare il valore generato. Questo è il segreto client.

    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Accedere al database del Server SQL Azure come un amministratore di Azure Active Directory e l'utilizzo di un utente del database indipendente una disposizione di comando T-SQL per l'applicazione principale. Vedere il [la connessione al Database SQL o Data Warehouse da usando Azure Active Directory l'autenticazione di SQL](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/) per ulteriori informazioni su come creare un amministratore di Azure Active Directory e un utente del database indipendente.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  Nel computer client (in cui, si desidera eseguire l'esempio), scaricare il [azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) libreria e le relative dipendenze e includerli nel percorso di compilazione Java. Si noti che azure-activedirectory-libreria-per-java è solo necessario per eseguire questo esempio specifico, in quanto utilizza le API da questa raccolta per recuperare il token di accesso da Azure AD. Se si dispone già di un token di accesso, è possibile ignorare questo passaggio. Si noti che è necessario rimuovere anche la sezione nell'esempio che recupera il token di accesso.

Nell'esempio seguente, sostituire il nome URL servizio token di sicurezza, ID Client, segreto Client, server e database con i valori.

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
        String stsurl = "https://microsoft.onmicrosoft.com/..."; // Replace with your STS URL.
        String clientId = "1846943b-ad04-4808-aa13-4702d908b5c1"; // Replace with your client ID.
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

Se la connessione ha esito positivo, vedrai il seguente messaggio di output:
```
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
