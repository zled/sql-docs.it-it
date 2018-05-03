---
title: Kerberos mediante l'autenticazione integrata di connettersi a SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d9023c31e0d7b985e17991a080a7c9afc077ff6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Uso dell'autenticazione integrata Kerberos per la connessione a SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  A partire da [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], un'applicazione può utilizzare il **authenticationScheme** proprietà di connessione per indicare che si desidera connettersi a un database tramite autenticazione integrata Kerberos di tipo 4. Vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md) per ulteriori informazioni sulle proprietà di connessione. Per ulteriori informazioni su Kerberos, vedere [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=100758).  
  
 Quando si utilizza l'autenticazione integrata con il linguaggio **Krb5LoginModule**, è possibile configurare il modulo utilizzando [classe Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).  
  
 Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] imposta le proprietà seguenti per Java Virtual Machine IBM:  
  
-   **useDefaultCcache = true**  
  
-   **moduleBanner = false**  
  
 Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] impostate le seguenti proprietà per tutte le altre macchine virtuali Java:  
  
-   **useTicketCache = true**  
  
-   **doNotPrompt = true**  
  
## <a name="remarks"></a>Osservazioni  
 Prima di [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], applicazioni è possibile specificare l'autenticazione integrata (tramite Kerberos o NTLM, a seconda di quale risulta disponibile) utilizzando il **integratedSecurity** proprietà di connessione e facendo riferimento a  **sqljdbc_auth.dll**, come descritto in [creazione dell'URL di connessione](../../connect/jdbc/building-the-connection-url.md).  
  
 A partire da [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], un'applicazione può utilizzare il **authenticationScheme** autenticazione di Kerberos Java pura di proprietà di connessione per indicare che si desidera connettersi a un database utilizzando Kerberos integrata implementazione:  
  
-   Se si desidera che l'autenticazione integrata tramite **Krb5LoginModule**, è comunque necessario specificare il **integratedSecurity = true** proprietà di connessione. È quindi opportuno specificare anche il **authenticationScheme = JavaKerberos** proprietà di connessione.  
  
-   Per continuare a utilizzare l'autenticazione integrata con **sqljdbc_auth.dll**, è sufficiente specificare **integratedSecurity = true** proprietà di connessione (e facoltativamente **authenticationScheme = NativeAuthentication**).  
  
-   Se si specifica **authenticationScheme = JavaKerberos** ma non si specifica anche **integratedSecurity = true**, il driver ignorerà il **authenticationScheme** proprietà di connessione si aspetta di trovare utente le credenziali di nome e la password nella stringa di connessione.  
  
 Quando si utilizza un'origine dati per creare connessioni, è possibile impostare a livello di codice lo schema di autenticazione utilizzando setAuthenticationScheme e (facoltativamente) impostare il nome SPN per le connessioni Kerberos utilizzando **setServerSpn**.  
  
 È stato aggiunto un nuovo logger per supportare l'autenticazione Kerberos: com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Per ulteriori informazioni, vedere [traccia operazione Driver](../../connect/jdbc/tracing-driver-operation.md).  
  
 Le linee guida seguenti consentono di configurare Kerberos:  
  
1.  Impostare **AllowTgtSessionKey** su 1 nel Registro di sistema per Windows. Per ulteriori informazioni, vedere [protocollo Kerberos, le voci del Registro di sistema e le chiavi di configurazione KDC in Windows Server 2003](http://support.microsoft.com/kb/837361).  
  
2.  Assicurarsi che la configurazione di Kerberos (krb5.conf in ambienti UNIX) punti all'area di autenticazione e al servizio KDC corretti per l'ambiente.  
  
3.  Inizializzare la cache TGT tramite kinit o accedendo al dominio.  
  
4.  Quando un'applicazione che utilizza **authenticationScheme = JavaKerberos** viene eseguito in Windows Vista o Windows 7 sistemi operativi, è necessario utilizzare un account utente standard. Se, tuttavia, si utilizza un account amministratore, l'applicazione deve essere eseguita con privilegi di amministratore.  
  
> [!NOTE]  
>  L'attributo di connessione serverSpn è supportato solo da Microsoft JDBC driver 4.2 e versioni successive.  
  
## <a name="service-principal-names"></a>Nomi dell'entità servizio  
 Un nome dell'entità servizio (SPN) è il nome con cui un client identifica in modo univoco un'istanza di un servizio.  
  
 È possibile specificare il nome SPN utilizzando il **serverSpn** proprietà di connessione, o lasciare che il driver crearlo automaticamente (impostazione predefinita).  Questa proprietà è nel formato: "MSSQLSvc/fqdn:port@REALM" dove fqdn è il nome di dominio completo, la porta è il numero di porta e REALM è l'area di autenticazione Kerberos di SQL Server in lettere maiuscole.  La parte dell'area di autenticazione di questa proprietà è facoltativa se l'area di autenticazione predefinita della configurazione di Kerberos è la stessa area di autenticazione del server e non è inclusa per impostazione predefinita.  Se si desidera supportare uno scenario di autenticazione tra diverse aree di autenticazione, in cui l'area di autenticazione predefinita nella configurazione di Kerberos è diversa dall'area di autenticazione del server, è necessario impostare il nome dell'entità servizio con la proprietà serverSpn.  
  
 Ad esempio, potrebbe essere simile il SPN: "MSSQLSvc/some-server.zzz.corp.contoso.com:1433@ZZZZ.CORP.CONTOSO.COM"  
  
 Per ulteriori informazioni sui nomi dell'entità servizio (SPN), vedere:  
  
-   [Come usare l'autenticazione Kerberos in SQL Server](http://support.microsoft.com/kb/319723)  
  
-   [Utilizzo di Kerberos con SQL Server](http://go.microsoft.com/fwlink/?LinkId=207814)  

> [!NOTE]  
> Prima di rilasciare 6.2.0 del driver JDBC, uso appropriato del Cross dell'area di autenticazione Kerberos, è necessario impostare in modo esplicito il **serverSpn**.
>
> A partire dal 6.2.0 versione, il driver sarà in grado di compilare il **serverSpn** per impostazione predefinita, anche quando si Usa Cross dell'area di autenticazione Kerberos. Anche se è possibile utilizzare **serverSpn** in modo esplicito troppo. 
  
## <a name="creating-a-login-module-configuration-file"></a>Creazione di un file di configurazione del modulo di accesso  
 È eventualmente possibile specificare un file di configurazione Kerberos. Se non si specifica un file di configurazione, vengono utilizzate le impostazioni seguenti:  
  
 JVM Sun  
 com.sun.security.auth.module.Krb5LoginModule necessari useTicketCache = true;  
  
 JVM IBM  
 com.ibm.security.auth.module.Krb5LoginModule necessari useDefaultCcache = true;  
  
 Se si sceglie di creare un file di configurazione del modulo di accesso, per il file è necessario utilizzare il formato seguente:  
  
```  
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```  
  
 Un file di configurazione di accesso è costituito da una o più voci, ciascuna indicante la tecnologia di autenticazione sottostante da utilizzare per un'applicazione o più applicazioni specifiche. Ad esempio,  
  
```  
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```  
  
 Di conseguenza, ogni voce del file di configurazione del modulo di accesso è costituita da un nome seguito da una o più voci specifiche di LoginModule, in cui ogni voce termina con un punto e virgola e l'intero gruppo di voci è racchiuso tra parentesi graffe. Ogni voce del file di configurazione termina con un punto e virgola.  
  
 Oltre a consentire al driver di acquisire credenziali Kerberos tramite le impostazioni specificate nel file di configurazione del modulo di accesso, il driver può utilizzare credenziali esistenti. Questo comportamento può risultare utile quando è necessario che tramite l'applicazione vengano create connessioni con credenziali di più di un utente.  
  
 Tramite il driver verrà effettuato il tentativo di utilizzare credenziali esistenti, se disponibili, prima di accedere utilizzando il modulo di accesso specificato. Di conseguenza, quando si utilizza il metodo Subject.doAs per l'esecuzione di codice in un contesto specifico, viene creata una connessione con le credenziali passate alla chiamata di Subject.doAs.  
  
 Per ulteriori informazioni, vedere [File di configurazione di account di accesso JAAS](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) e [classe Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).  

 A partire da Microsoft JDBC Driver 6.2, nome del file di configurazione di modulo di accesso può essere passato facoltativamente utilizzando jaasConfigurationName di proprietà di connessione, in questo modo ogni connessione per la propria configurazione di account di accesso.
 
## <a name="creating-a-kerberos-configuration-file"></a>Creazione di un file di configurazione Kerberos  
 Per ulteriori informazioni sui file di configurazione di Kerberos, vedere [Kerberos requisiti](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).  
  
 Di seguito viene presentato un esempio di file di configurazione di un dominio, in cui YYYY e ZZZZ sono nomi di dominio nel sito.  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
  
[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  
  
        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  
  
```  
  
## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>Abilitazione del file di configurazione del dominio e del file di configurazione del modulo di accesso  
 È possibile abilitare un file di configurazione del dominio con -Djava.security.krb5.conf. È possibile abilitare un file di configurazione di modulo di accesso con **-Djava.security.auth.login.config**.  
  
 Quando, ad esempio, si avvia l'applicazione, è possibile utilizzare la riga di comando seguente:  
  
```  
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  
  
```  
  
## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Verifica dell'accesso a SQL Server tramite Kerberos  
 Eseguire la query seguente in SQL Server Management Studio:  
  
 **Selezionare auth_scheme DM exec_connections dove session_id = @@spid**  
  
 Assicurarsi di disporre dell'autorizzazione necessaria per l'esecuzione della query.  

## <a name="constrained-delegation"></a>Delega vincolata
A partire da Microsoft JDBC Driver 6.2, il driver supporta la delega vincolata Kerberos. Le credenziali delegate possono essere passata come oggetto org.ietf.jgss.GSSCredential, queste credenziali vengono utilizzate dal driver per stabilire una connessione. 

```
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Connessione Kerberos utilizzando nomi dell'entità e una Password
A partire da Microsoft JDBC Driver 6.2, il driver può stabilire Kerberos connessione utilizzando il nome dell'entità e la Password passata nella stringa di connessione. 
```
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```
La proprietà username non richiede l'area di autenticazione se l'utente appartiene al default_realm impostato nel file krb5. Quando `userName` e `password` è impostato insieme a `integratedSecurity=true;` e `authenticationScheme=JavaKerberos;` proprietà, la connessione viene stabilita con il valore del nome utente come entità Kerberos lungo con la password fornita.
 
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
