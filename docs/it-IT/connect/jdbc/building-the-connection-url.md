---
title: Creazione dell'URL di connessione | Documenti Microsoft
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
ms.assetid: 44996746-d373-4f59-9863-a8a20bb8024a
caps.latest.revision: 53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe815ba6f983d5d9523413066a1f6f168c23bf65
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="building-the-connection-url"></a>Costruzione dell'URL della connessione
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il formato generale dell'URL della connessione è  
  
 `jdbc:sqlserver://[serverName[\instanceName][:portNumber]][;property=value[;property=value]]`  
  
 dove:  
  
-   **JDBC: / /** (obbligatorio) è noto come sottoprotocollo ed è costante.  
  
-   **serverName** (facoltativo) è l'indirizzo del server a cui connettersi. Si tratta del valore DNS o dell'indirizzo IP oppure di localhost o 127.0.0.1 nel caso del computer locale. Se non viene specificato nell'URL della connessione, il nome del server deve essere specificato nella raccolta delle proprietà.  
  
-   **instanceName** (facoltativo) indica l'istanza a cui connettersi su serverName. Se non viene specificata alcuna impostazione, la connessione viene eseguita all'istanza predefinita.  
  
-   **portNumber** (facoltativo) è la porta a cui connettersi su serverName. Il valore predefinito è 1433. Se si utilizza tale valore, non è necessario specificare nell'URL né la porta né il carattere ':' che la precede.  
  
    > [!NOTE]  
    >  Per una connessione ottimale a un'istanza denominata, si consiglia di impostare un valore per portNumber. In questo modo si evita un round trip al server per determinare il numero di porta. Se si utilizzano sia portNumber che instanceName, portNumber avrà la precedenza e instanceName verrà ignorato.  
  
-   **proprietà** (facoltativo) indica una o più proprietà della connessione. Per ulteriori informazioni, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md). È possibile specificare qualsiasi proprietà presente nell'elenco. Le proprietà, tuttavia, possono essere delimitate solo utilizzando il carattere di punto e virgola (';') e non possono essere duplicate.  
  
> [!CAUTION]  
>  Per garantire maggiore sicurezza, si consiglia di evitare di costruire l'URL della connessione sulla base dei dati inseriti dall'utente. Nell'URL dovrebbero essere specificati solo il nome del server e il driver. Per i valori relativi a nome utente e password, utilizzare le raccolte delle proprietà della connessione. Per ulteriori informazioni sulla sicurezza delle applicazioni JDBC, vedere [protezione delle applicazioni JDBC Driver](../../connect/jdbc/securing-jdbc-driver-applications.md).  
  
## <a name="connection-examples"></a>Esempi di connessioni  
 Connessione al database predefinito sul computer locale utilizzando un nome utente e la password:  
  
 `jdbc:sqlserver://localhost;user=MyUserName;password=*****;`  
  
> [!NOTE]  
>  Sebbene nell'esempio precedente siano stati utilizzati un nome utente e una password nella stringa di connessione, è consigliabile utilizzare la sicurezza integrata per garantire maggiore protezione. Per ulteriori informazioni, vedere il [connessione con autenticazione integrata](#Connectingintegrated) sezione più avanti in questo argomento.  
  
 Stringa di connessione seguente viene illustrato un esempio di come connettersi a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database tramite autenticazione integrata e Kerberos da un'applicazione in esecuzione su qualsiasi sistema operativo supportato dal [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]:  
  
```  
jdbc:sqlserver://;servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos  
```  
  
 Connessione al database predefinito sul computer locale utilizzando l'autenticazione integrata:  
  
 `jdbc:sqlserver://localhost;integratedSecurity=true;`  
  
 Connessione a un database denominato su un server remoto:  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 Connessione alla porta predefinita su un server remoto:  
  
 `jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 Connessione specificando un nome di applicazione personalizzato:  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;applicationName=MyApp;`  
  
## <a name="named-and-multiple-sql-server-instances"></a>Più istanze denominate di SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Consente l'installazione di più istanze di database per server. Ciascuna istanza è definita in base a un nome specifico. Per connettersi a un'istanza denominata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile specificare il numero di porta dell'istanza denominata (scelta consigliata) o è possibile specificare il nome dell'istanza come proprietà URL di JDBC o **datasource** proprietà. Se non viene specificato né il nome né il numero della porta, viene creata una connessione all'istanza predefinita. Vedere gli esempi seguenti:  
  
 Per utilizzare un numero di porta, procedere come segue:  
  
 `jdbc:sqlserver://localhost:1433;integratedSecurity=true;<more properties as required>;`  
  
 Per utilizzare una proprietà URL di JDBC, procedere come segue:  
  
 `jdbc:sqlserver://localhost;instanceName=instance1;integratedSecurity=true;<more properties as required>;`  
  
## <a name="escaping-values-in-the-connection-url"></a>Utilizzo della sequenza di escape dei valori nell'URL della connessione  
 Se nell'URL della connessione vengono utilizzati caratteri speciali, quali spazi, punti e virgola, virgolette, è necessario includere alcune parti dell'URL in una sequenza di escape. L'impostazione di una sequenza di escape per tali caratteri è supportata nel driver JDBC se tali caratteri sono racchiusi tra parentesi graffe. Ad esempio con {;} il carattere di punto e virgola è incluso in una sequenza di escape.  
  
 I valori inclusi in una sequenza di escape possono contenere caratteri speciali (in particolare '=', ';', '[]' e lo spazio) ma non parentesi graffe. I valori che contengono parentesi graffe e che devono essere inclusi in una sequenza di escape devono essere aggiunti a una raccolta di proprietà.  
  
> [!NOTE]  
>  Lo spazio all'interno delle parentesi graffe è letterale e non viene eliminato.  
  
##  <a name="Connectingintegrated"></a> Connessione con autenticazione integrata in Windows  
 Il driver JDBC supporta l'utilizzo dell'autenticazione integrata di tipo 2 nei sistemi operativi Windows tramite la proprietà della stringa di connessione integratedSecurity. Per utilizzare l'autenticazione integrata, copiare il file sqljdbc_auth.dll in una directory nel percorso di sistema di Windows nel computer in cui è installato il driver JDBC.  
  
 I file sqljdbc_auth.dll sono installati nel percorso seguente:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \auth\  
  
 Per i sistemi operativi supportati dal [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], vedere [utilizzando l'autenticazione integrata Kerberos per connettersi a SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md) per una descrizione di una funzionalità aggiunta in [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] che consente a un'applicazione per connettersi a un database con l'autenticazione integrata Kerberos di tipo 4.  
  
> [!NOTE]  
>  Se si esegue Java Virtual Machine (JVM) a 32 bit, utilizzare il file sqljdbc_auth.dll nella cartella x86, anche se la versione del sistema operativo è x64. Se si esegue JVM a 64 bit in un processore x64, utilizzare il file sqljdbc_auth.dll nella cartella x64.  
  
 In alternativa è possibile impostare la proprietà di sistema java.libary.path in modo da specificare la directory di sqljdbc_auth.dll. Ad esempio, se il driver JDBC è installato nella directory predefinita, specificare il percorso della DLL utilizzando il seguente argomento della VM (Virtual Machine) quando l'applicazione Java viene avviata:  
  
 `-Djava.library.path=C:\Microsoft JDBC Driver 6.4 for SQL Server\sqljdbc_<version>\enu\auth\x86`  
  
## <a name="connecting-with-ipv6-addresses"></a>Connessione con indirizzi IPv6  
 Il driver JDBC supporta l'utilizzo di indirizzi IPv6 con la raccolta delle proprietà di connessione e con la proprietà della stringa di connessione serverName. Il valore serverName iniziale, quale jdbc:*sqlserver*://*serverName*, non è supportata per gli indirizzi IPv6 nelle stringhe di connessione. Utilizzando un nome per *serverName* anziché IPv6 non elaborato indirizzo funzionerà in ogni caso la connessione. Di seguito sono riportati alcuni esempi.  
  
 **Utilizzare la proprietà serverName**  
  
 `jdbc:sqlserver://;serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1;integratedSecurity=true;`  
  
 **Utilizzare la raccolta di proprietà**  
  
 `Properties pro = new Properties();`  
  
 `pro.setProperty("serverName", "serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1");`  
  
 `Connection con = DriverManager.getConnection("jdbc:sqlserver://;integratedSecurity=true;", pro);`  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
