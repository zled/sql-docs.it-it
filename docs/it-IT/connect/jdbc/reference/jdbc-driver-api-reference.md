---
title: Riferimento all'API del Driver JDBC | Documenti Microsoft
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
ms.topic: conceptual
ms.assetid: e4e1ae9d-18a6-41db-8bd2-9cf0eee4cccb
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a004657257c1b8695902fdab33ae2e4f7ec010dc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="jdbc-driver-api-reference"></a>Riferimento all'API del driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fornisce un'API che può essere utilizzata all'interno di linguaggio di programmazione codice per connettersi e interagire con un [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database.  
  
> [!NOTE]  
>  Per informazioni concettuali sull'utilizzo del driver JDBC, vedere [Panoramica del Driver JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
>  Per JDBC 4.1 e 4.2 il supporto di conformità, usare Microsoft JDBC Driver 4.2 (o versione successiva) per SQL Server. Le precedenti versioni Microsoft JDBC Drivers 4.1 e 4.0 non supportano i nuovi metodi introdotti con JDBC 4.1 o 4.2.  
>   
>  I dettagli dell'API per la conformità con JDBC 4.1 non sono riportati in questa sezione. Vedere [JDBC 4.1 conformità per il Driver JDBC](../../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md).  
>   
>  I dettagli dell'API per la conformità con JDBC 4.2 non sono riportati in questa sezione. Vedere [JDBC 4.2 conformità per il Driver JDBC](../../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).  
>   
>  I dettagli dell'API per la copia Bulk, disponibile a partire da Microsoft JDBC Driver 4.2 per SQL Server, non disponibili in questa sezione. Vedere [con la copia Bulk con il Driver JDBC](../../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).  
>   
>  Dettagli dell'API per Always Encrypted, disponibili a partire da Microsoft JDBC Driver 6.0 per SQL Server, non disponibili in questa sezione. Vedere [Always Encrypted riferimento API per il Driver JDBC](../../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  
>   
>  I dettagli dell'API per i parametri Using Table-Valued, disponibile a partire da Microsoft JDBC Driver 6.0 per SQL Server, non disponibili in questa sezione. Vedere [utilizzando parametri con valori di tabella](../../../connect/jdbc/using-table-valued-parameters.md)  
>   
>  Microsoft JDBC Driver 6.4 supporta la compilazione con JDK 7.0, 8.0 e 9.0.  
>   
>  Microsoft JDBC Driver 6.2 supporta la compilazione con JDK 7.0 e 8.0.  
>   
>  Microsoft JDBC driver 6.0 e compilazione di supporto 4.2 con JDK 5.0, 6.0, 7.0 e 8.0.  
>   
>  Microsoft JDBC Driver 4.1 supporta la compilazione con JDK 5.0, 6.0 e 7.0.  

## <a name="interfaces"></a>Interfacce  
  
|Nome interfaccia|Description|  
|--------------------|-----------------|  
|[Interfaccia ISQLServerCallableStatement](../../../connect/jdbc/reference/isqlservercallablestatement-interface.md)|Consente di specificare il nome della stored procedure da chiamare insieme ai parametri di input e di output.|  
|[Interfaccia ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md)|Rappresenta una connessione JDBC a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database.|  
|[Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)|Rappresenta un elenco di proprietà specifiche per la connessione a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database utilizzando un [ISQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)|Rappresenta l'implementazione di base della funzionalità dell'istruzione preparata di JDBC.|  
|[ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)|Rappresenta un set di risultati JDBC.|  
|[ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)|Rappresenta l'implementazione di base della funzionalità dell'istruzione JDBC.|  
  
## <a name="classes"></a>Classi  
  
|Nome classe|Description|  
|----------------|-----------------|  
|[DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)|Rappresenta un oggetto di tipo microsoft.sql.DateTimeOffset.|  
|[SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)|Rappresenta un oggetto BLOB (Binary Large Object).|  
|[SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)|Implementa l'oggetto ISQLServerCallableStatement.|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)|Rappresenta un oggetto CLOB (Character Large Binary Object).|  
|[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)|Implementa l'oggetto ISQLServerConnectopn.|  
|[SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)|Rappresenta connessioni di database fisiche per le gestioni dei pool di connessioni.|  
|[SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)|Rappresenta i metadati per il database.|  
|[SQLServerDataSource](../../../connect/jdbc/reference/isqlserverdatasource-interface.md)|Rappresenta un elenco di proprietà specifiche per la connessione a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database utilizzando un [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)|Rappresenta una object factory per la materializzazione delle origini dati dall'interfaccia JNDI (Java Naming and Directory Interface).|  
|[SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)|Rappresenta il driver JDBC. Questa classe include metodi per la connessione a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database e per ottenere informazioni sul driver JDBC.|  
|[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)|Rappresenta un'esecuzione non riuscita o incompleta di un'istruzione SQL.|  
|[Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)|Rappresenta un oggetto CLOB (Character Large Binary Object) che utilizza il set di caratteri nazionali.|  
|[SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)|Rappresenta i metadati per i parametri delle istruzioni preparate.|  
|[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)|Rappresenta una connessione di database fisica in un pool di connessioni.|  
|[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)|Implementa l'oggetto ISQLServerPreparedStatement.|  
|[SQLServerResource](../../../connect/jdbc/reference/sqlserverresource-class.md)|Rappresenta una risorsa di tipo stringa di errore localizzata. Questa classe è destinata al solo uso interno.|  
|[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)|Implementa l'oggetto ISQLServerResultSet.|  
|[SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)|Rappresenta i metadati delle colonne contenute in un set di risultati.|  
|[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)|Rappresenta il checkpoint in corrispondenza del quale può essere eseguito il rollback di una transazione.|  
|[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)|Implementa l'oggetto ISQLServerStatement.|  
|[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)|Rappresenta le connessioni JDBC che possono partecipare alle transazioni distribuite (XA).|  
|[SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)|Rappresenta una factory per [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) gli oggetti che viene utilizzata internamente.|  
|[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)|Rappresenta un XAResource XA per la gestione di transazioni distribuite.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
