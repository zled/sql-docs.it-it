---
title: "JDBC 4.1 conformità per il Driver JDBC | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f087fd40-8451-478e-b465-43112c711515
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8221755d220caec5588c8ed1343e360799b82694
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="jdbc-41-compliance-for-the-jdbc-driver"></a>Conformità con JDBC 4.1 per il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Le versioni precedenti a Microsoft JDBC Driver 4.2 per SQL Server sono compatibili con le specifiche Java Database Connectivity API 4.0. Questa sezione non è applicabile per le versioni precedenti alla 4.2.  
  
 La specifica Java Database Connectivity API 4.1 è supportata da Microsoft JDBC Driver 4.2 per SQL Server, con i metodi API seguenti.  
  
 **Classe SQLServerConnection**  
  
|Nuovo metodo|Description|Implementazione del driver JDBC|  
|----------------|-----------------|--------------------------------|  
|void abort(Executor executor)|Termina una connessione aperta a SQL Server.|Implementato come descritto nell'interfaccia java.sql.Connection. Per ulteriori informazioni, vedere [Java.SQL. Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
|void setSchema(String schema)|Imposta lo schema per la connessione corrente.|SQL Server non supporta l'impostazione dello schema per la sessione corrente. Se questo metodo viene chiamato, il driver registra un messaggio di avviso in modo invisibile all'utente. Per ulteriori informazioni, vedere [Java.SQL. Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
|String getSchema()|Restituisce il nome dello schema per la connessione corrente.|Poiché SQL Server non supporta l'impostazione dello schema per la connessione corrente, il driver restituisce lo schema predefinito dell'utente. Per ulteriori informazioni, vedere [Java.SQL. Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
  
 **Classe SQLServerDatabaseMetaData**  
  
|Nuovo metodo|Description|Implementazione del driver JDBC|  
|----------------|-----------------|--------------------------------|  
|boolean generatedKeyAlwaysReturned()|Restituisce true, dal momento che il driver supporta il recupero delle chiavi generate|Implementato come descritto in java.sql. Interfaccia DatabaseMetaData. Per ulteriori informazioni, vedere [DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html).|  
|ResultSet getPseudoColumns(String catalog, String schemaPattern,String tableNamePattern,String columnNamePattern)|Recupera una descrizione delle pseudocolonne o delle colonne nascoste|Restituisce un set di risultati vuoto, dal momento che SQL Server non dispone di una nozione formale di pseudocolonne. Per ulteriori informazioni, vedere [DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html).|  
  
 **Classe SQLServerStatement**  
  
|Nuovo metodo|Description|Implementazione del driver JDBC|  
|----------------|-----------------|--------------------------------|  
|void closeOnCompletion()|Specifica che l'istruzione verrà chiusa quando vengono chiusi tutti i relativi set di risultati dipendenti.|Implementato come descritto nell'interfaccia java.sql.Statement. Per ulteriori informazioni, vedere [Java.SQL. Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html).|  
|boolean isCloseOnCompletion()|Restituisce un valore che indica se l'istruzione verrà chiusa quando vengono chiusi tutti i relativi set di risultati dipendenti.|Implementato come descritto nell'interfaccia java.sql.Statement. Per ulteriori informazioni, vedere [Java.SQL. Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html).|  
  
 La specifica Java Database Connectivity API 4.1 è supportata da Microsoft JDBC Driver 4.2 per SQL Server, con le funzionalità seguenti.  
  
|Nuova funzionalità|Description|  
|-----------------|-----------------|  
|Nuova funzione di escape<br /><br /> Escape di righe restituite limitate|Parzialmente supportato<br /><br /> Sintassi di escape: limite \<righe > [OFFSET < offset_righe >]<br /><br /> La sintassi di escape è costituita da due parti: la parte obbligatoria 'righe' specifica il numero di righe da restituire, la parte facoltativa 'offset_righe' specifica il numero di righe da ignorare prima di iniziare a restituire le righe<br /><br /> Il driver supporta solo la parte obbligatoria trasformando la query per l'utilizzo di 'TOP' anziché LIMIT (SQL Server non supporta 'LIMIT').<br /><br /> Il driver genera un'eccezione se viene utilizzata la parte facoltativa 'offset_righe', dal momento che SQL Server non dispone di un costrutto predefinito per il supporto di tale parte.<br /><br /> Per informazioni dettagliate, vedere [utilizzando sequenze di Escape SQL](https://msdn.microsoft.com/en-us/library/ms378045.aspx).|  
  
 La specifica Java Database Connectivity API 4.1 è supportata da Microsoft JDBC Driver 4.2 per SQL Server, con i mapping dei tipi di dati seguenti.  
  
|Mapping di tipi di dati|Description|  
|------------------------|-----------------|  
|Ora sono supportati nuovi mapping dei tipi di dati nei metodi PreparedStatement.setObject() e PreparedStatement.setNull().|1. Nuovo mapping dei tipi da Java a JDBC<br /><br /> (a) Da java.math.BigInteger a BIGINT JDBC<br /><br /> (b) Da java.util.Date e java.util.Calendar a TIMESTAMP JDBC<br /><br /> 2. Nuove conversioni dei tipi di dati:<br /><br /> (a) Da java.math.BigInteger a CHAR, VARCHAR, LONGVARCHAR e BIGINT<br /><br /> (b) Da java.util.Date e java.util.Calendar a CHAR, VARCHAR, LONGVARCHAR, DATE, TIME e TIMESTAMP<br /><br /> Per ulteriori informazioni, vedere la specifica JDBC 4.1.|  
  
  
