---
title: Uso di una connessione | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a4b2cdefeecc56c331224cd7453e861defafb8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687966"
---
# <a name="working-with-a-connection"></a>Utilizzo di una connessione

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Nelle sezioni seguenti vengono illustrati alcuni esempi dei diversi modi di connessione a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].

> [!NOTE]  
> Se si verificano problemi durante la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite il driver JDBC, vedere [Risoluzione dei problemi di connettività](../../connect/jdbc/troubleshooting-connectivity.md) per suggerimenti su come correggerli.

## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>Creazione di una connessione mediante la classe DriverManager

L'approccio più semplice per creare una connessione a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consiste nel caricare il driver JDBC e chiamare il metodo getConnection della classe DriverManager, come nell'esempio seguente:

```java
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```

Questa tecnica consente di creare una connessione di database utilizzando il primo driver disponibile nell'elenco dei driver in grado di connettersi con l'URL specificato.

> [!NOTE]  
> Quando si usa la libreria di classi sqljdbc4.jar, le applicazioni non devono registrare o caricare in modo esplicito il driver tramite il metodo Class.forName. Quando viene chiamato il metodo getConnection della classe DriverManager, un driver appropriato viene individuato il set di driver JDBC registrati. Per ulteriori informazioni, vedere Utilizzo del driver JDBC.

## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>Creazione di una connessione mediante la classe SQLServerDriver

Se è necessario specificare uno particolare dei driver presenti nell'elenco dei driver per DriverManager, è possibile creare una connessione di database usando il metodo [connect](../../connect/jdbc/reference/connect-method-sqlserverdriver.md) della classe [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md), come nell'esempio seguente:

```java
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```

## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>Creazione di una connessione mediante la classe SQLServerDataSource

Se è necessario creare una connessione usando la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), è possibile usare diversi metodi per l'impostazione della classe prima di chiamare il metodo [getConnection](../../connect/jdbc/reference/getconnection-method.md), come nell'esempio seguente:

```java
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

```java
String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"
```

Per connettersi a una porta specifica su un server, utilizzare l'esempio seguente:

```java
String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"
```

Per connettersi a un'istanza denominata su un server, utilizzare l'esempio seguente:

```java
String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"
```

Per connettersi a un database specifico su un server, utilizzare l'esempio seguente:

```java
String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"
```

Per ulteriori esempi di URL di connessione, vedere [Costruzione dell'URL della connessione](../../connect/jdbc/building-the-connection-url.md).

## <a name="creating-a-connection-with-a-custom-login-time-out"></a>Creazione di una connessione con un timeout di accesso personalizzato

Se è necessario adattarsi al carico del server o al traffico di rete, è possibile creare una connessione che abbia uno specifico valore di timeout di accesso, espresso in secondi, come nell'esempio seguente:

```java
String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"
```

## <a name="create-a-connection-with-application-level-identity"></a>Creazione di una connessione con identità a livello di applicazione

Se è necessario utilizzare la registrazione e il profiling, occorre identificare la connessione come avente origine da una specifica applicazione, come nell'esempio seguente:

```java
String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"
```

## <a name="closing-a-connection"></a>Chiusura di una connessione

È possibile chiudere una connessione di database in modo esplicito chiamando il metodo [close](../../connect/jdbc/reference/close-method-sqlserverconnection.md) della classe SQLServerConnection, come nell'esempio seguente:

```java
con.close();
```

In questo modo verranno rilasciate le risorse di database usate dall'oggetto SQLServerConnection o, negli scenari con pool, verrà restituita la connessione al pool di connessioni.

> [!NOTE]  
> Se si chiama il metodo Close verrà eseguito anche il rollback di tutte le transazioni in sospeso.

## <a name="see-also"></a>Vedere anche

[Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
