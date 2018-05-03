---
title: Utilizzo di una connessione | Documenti Microsoft
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
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 400b4adb2b4812c1eed0397b93b1a1e08d0b5b39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-a-connection"></a>Utilizzo di una connessione
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Nelle sezioni seguenti vengono forniscono esempi dei diversi modi per connettersi a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
> [!NOTE]  
>  Se si verificano problemi durante la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] utilizza il driver JDBC, vedere [risoluzione dei problemi di connettività](../../connect/jdbc/troubleshooting-connectivity.md) per suggerimenti su come correggerli.  
  
## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>Creazione di una connessione mediante la classe DriverManager  
 L'approccio più semplice per creare una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database consiste nel caricare il driver JDBC e chiamare il metodo getConnection della classe DriverManager, come illustrato di seguito:  
  
```  
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 Questa tecnica consente di creare una connessione di database utilizzando il primo driver disponibile nell'elenco dei driver in grado di connettersi con l'URL specificato.  
  
> [!NOTE]  
>  Quando si utilizza la libreria di classi sqljdbc4.jar, le applicazioni non è necessario registrare o caricare il driver tramite il metodo forName in modo esplicito. Quando viene chiamato il metodo getConnection della classe DriverManager, un driver appropriato viene individuato dal set di driver JDBC registrati. Per ulteriori informazioni, vedere Utilizzo del driver JDBC.  
  
## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>Creazione di una connessione mediante la classe SQLServerDriver  
 Se è necessario specificare un driver specifico nell'elenco dei driver di montaggio, è possibile creare una connessione al database utilizzando il [connettersi](../../connect/jdbc/reference/connect-method-sqlserverdriver.md) metodo il [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md) (classe), come illustrato di seguito:  
  
```  
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```  
  
## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>Creazione di una connessione mediante la classe SQLServerDataSource  
 Se è necessario creare una connessione utilizzando il [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) (classe), è possibile utilizzare diversi metodi per l'impostazione della classe prima di chiamare il [getConnection](../../connect/jdbc/reference/getconnection-method.md) (metodo), come illustrato di seguito:  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setUser("MyUserName");  
ds.setPassword("*****");  
ds.setServerName("localhost");  
ds.setPortNumber(1433);   
ds.setDatabaseName("AdventureWorks");  
Connection con = ds.getConnection();  
```  
  
## <a name="creating-a-connection-that-targets-a-very-specific-data-source"></a>Creazione di una connessione con un'origine dei dati di destinazione molto specifica  
 Se è necessario creare una connessione di database con un'origine dei dati di destinazione molto specifica, è possibile adottare diversi approcci. Ogni approccio dipende dalle proprietà impostate utilizzando l'URL della connessione.  
  
 Per connettersi all'istanza predefinita su un server remoto, utilizzare l'esempio seguente:  
  
 `String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"`  
  
 Per connettersi a una porta specifica su un server, utilizzare l'esempio seguente:  
  
 `String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"`  
  
 Per connettersi a un'istanza denominata su un server, utilizzare l'esempio seguente:  
  
 `String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"`  
  
 Per connettersi a un database specifico su un server, utilizzare l'esempio seguente:  
  
 `String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"`  
  
 Per ulteriori esempi di URL di connessione, vedere [creazione dell'URL di connessione](../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="creating-a-connection-with-a-custom-login-time-out"></a>Creazione di una connessione con un timeout di accesso personalizzato  
 Se è necessario adattarsi al carico del server o al traffico di rete, è possibile creare una connessione che abbia uno specifico valore di timeout di accesso, espresso in secondi, come nell'esempio seguente:  
  
 `String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"`  
  
## <a name="create-a-connection-with-application-level-identity"></a>Creazione di una connessione con identità a livello di applicazione  
 Se è necessario utilizzare la registrazione e il profiling, occorre identificare la connessione come avente origine da una specifica applicazione, come nell'esempio seguente:  
  
 `String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"`  
  
## <a name="closing-a-connection"></a>Chiusura di una connessione  
 È possibile chiudere in modo esplicito una connessione al database tramite la chiamata di [chiudere](../../connect/jdbc/reference/close-method-sqlserverconnection.md) metodo della classe SQLServerConnection, come illustrato di seguito:  
  
 `con.close();`  
  
 Questo verrà restituita la connessione al pool di connessioni in scenari con pool o rilasciare le risorse di database che utilizza l'oggetto SQLServerConnection.  
  
> [!NOTE]  
>  Chiamare il metodo close verrà inoltre annullare eventuali transazioni in sospeso.  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
