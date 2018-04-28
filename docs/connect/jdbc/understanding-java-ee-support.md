---
title: Informazioni sul supporto di Java EE | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9448b80-b7a3-49cf-8bb4-322c73676005
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff6d631ec236a861fb00d4107cc9f04078449c53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="understanding-java-ee-support"></a>Informazioni sul supporto Java EE
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il documento nelle sezioni seguenti come [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il supporto per Java Platform, Enterprise Edition (Java EE) e caratteristiche API facoltative JDBC 3.0. Gli esempi di codice sorgente forniti in questo sistema di Guida costituiscono un buon riferimento per iniziare a utilizzare queste caratteristiche.  
  
 Assicurarsi innanzitutto che l'ambiente Java (JDK, JRE) includa il pacchetto javax.sql. Questo pacchetto è necessario per qualsiasi applicazione JDBC che utilizzi l'API facoltativa. JDK 1.5 e le versioni successive contengono già questo pacchetto, pertanto non è necessario installarlo separatamente.  
  
## <a name="driver-name"></a>Nome del driver  
 Nome della classe driver **sqlserverdriver**. Per JDBC driver 4.1, 4.2 e 6.0, il driver è incluso nel file sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar o sqljdbc42.jar. Per 6.2 Driver JDBC, il driver è incluso in mssql-jdbc-6.2.1.jre7.jar o mssql-jdbc-6.2.1.jre8.jar. Per 6.4 Driver JDBC, il driver è incluso in mssql-jdbc-6.4.0.jre7.jar, mssql-jdbc-6.4.0.jre8.jar o mssql-jdbc-6.4.0.jre9.jar.
  
 Il nome della classe viene utilizzato quando si carica il driver con la classe DriverManager JDBC. nonché quando è necessario specificare il nome della classe del driver in qualsiasi configurazione del driver. Per configurare un'origine dati all'interno di un server applicazioni Java EE potrebbe ad esempio essere necessario immettere il nome della classe del driver.  
  
## <a name="data-sources"></a>Origini dei dati  
 Il driver JDBC fornisce supporto per le origini dati Java EE e JDBC 3.0. Il driver JDBC [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) classe è implementata da **sqlserverxadatasource**.  
  
### <a name="datasource-names"></a>Nomi delle origini dati  
 È possibile stabilire connessioni al database utilizzando le origini dati. Le origini dati disponibili con il driver JDBC sono descritte nella tabella seguente:  
  
|Tipo di origine dati|Descrizione e nome di classe|  
|---------------|--------------------------|  
|DataSource|com.microsoft.sqlserver.jdbc.SQLServerDataSource <br/> <br/> Origine dati non per i pool.|  
|ConnectionPoolDataSource|com.microsoft.sqlserver.jdbc.SQLServerConnectionPoolDataSource <br/> <br/> Origine dati per la configurazione dei pool di connessioni al server applicazioni JAVA EE. Utilizzata in genere quando l'applicazione è in esecuzione in un server applicazioni JAVA EE.|  
|XADataSource|com.microsoft.sqlserver.jdbc.SQLServerXADataSource <br/> <br/> Origine dati per la configurazione delle origini dati JAVA EE XA. Utilizzata in genere quando l'applicazione è in esecuzione in un server applicazioni JAVA EE e in uno strumento di gestione transazioni XA.|  
  
### <a name="data-source-properties"></a>Proprietà dell'origine dati  
 Tutte le origini dati consentono di impostare e ottenere qualsiasi proprietà associata al set di proprietà del driver sottostante.  
  
 Esempi:  
  
 `setServerName("localhost");`  
  
 `setDatabaseName("AdventureWorks");`  
  
 Di seguito viene illustrato in che modo un'applicazione si connette utilizzando un'origine dati:  
  
```  
initialize JNDI ..  
Context ctx = new InitialContext(System.getProperties());  
...  
DataSource ds = (DataSource) ctx.lookup("MyDataSource");  
Connection c = ds.getConnection("user", "pwd");  
```  
  
 Per ulteriori informazioni sulle proprietà delle origini dati, vedere [impostando le proprietà dell'origine dati](../../connect/jdbc/setting-the-data-source-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
