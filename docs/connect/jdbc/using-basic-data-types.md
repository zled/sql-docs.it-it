---
title: Utilizzo di tipi di dati di base | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d7044936-5b8c-4def-858c-28a11ef70a97
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8aa3b6b211095f3c27693928dab6518a6a2e895
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759409"
---
# <a name="using-basic-data-types"></a>Utilizzo di tipi di dati di base

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] usa i tipi di dati JDBC di base per convertire i tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un formato comprensibile nel linguaggio di programmazione Java e viceversa. Il driver JDBC fornisce supporto per le API di JDBC 4.0, che include il **SQLXML** tipo di dati e tipi di dati nazionali (Unicode), ad esempio **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, e **NCLOB**.  
  
## <a name="data-type-mappings"></a>Mapping di tipi di dati

Nella tabella seguente sono elencati i mapping predefiniti tra i tipi di dati di base di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], JDBC e del linguaggio di programmazione Java:  
  
| Tipi di SQL Server   | Tipi JDBC (java.sql.Types)                        | Tipi del linguaggio Java          |
| ------------------ | -------------------------------------------------- | ---------------------------- |
| BIGINT             | bigint                                             | long                         |
| BINARY             | BINARY                                             | byte[]                       |
| bit                | BIT                                                | boolean                      |
| char               | CHAR                                               | String                       |
| Data               | DATE                                               | java.sql.Date                |
| DATETIME           | timestamp                                          | java.sql.Timestamp           |
| datetime2          | timestamp                                          | java.sql.Timestamp           |
| datetimeoffset (2) | microsoft.sql.Types.DATETIMEOFFSET                 | microsoft.sql.DateTimeOffset |
| Decimal            | DECIMAL                                            | java.math.BigDecimal         |
| FLOAT              | DOUBLE                                             | double                       |
| image              | LONGVARBINARY                                      | byte[]                       |
| INT                | INTEGER                                            | INT                          |
| money              | DECIMAL                                            | java.math.BigDecimal         |
| NCHAR              | CHAR<br /><br /> NCHAR (Java SE 6.0)               | String                       |
| ntext              | LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0) | String                       |
| NUMERIC            | NUMERIC                                            | java.math.BigDecimal         |
| NVARCHAR           | VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)         | String                       |
| nvarchar(max)      | VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)         | String                       |
| REAL               | real                                               | FLOAT                        |
| smalldatetime      | timestamp                                          | java.sql.Timestamp           |
| SMALLINT           | SMALLINT                                           | short                        |
| smallmoney         | DECIMAL                                            | java.math.BigDecimal         |
| text               | LONGVARCHAR                                        | String                       |
| time               | TIME (1)                                           | java.sql.Time (1)            |
| timestamp          | BINARY                                             | byte[]                       |
| TINYINT            | TINYINT                                            | short                        |
| udt                | VARBINARY                                          | byte[]                       |
| UNIQUEIDENTIFIER   | CHAR                                               | String                       |
| varbinary          | VARBINARY                                          | byte[]                       |
| varbinary(max)     | VARBINARY                                          | byte[]                       |
| varchar            | VARCHAR                                            | String                       |
| ntext       | VARCHAR                                            | String                       |
| xml                | LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0) | String<br /><br /> SQLXML    |
| sqlvariant         | SQLVARIANT                                         | Object                       |
| geometry           | VARBINARY                                          | byte[]                       |
| geography          | VARBINARY                                          | byte[]                       |
  
(1) Per usare java.sql.Time con il tipo time di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario impostare la proprietà di connessione **sendTimeAsDatetime** su false.  
  
(2) è possibile accedere a livello di codice ai valori della **datetimeoffset** con [classe DateTimeOffset](../../connect/jdbc/reference/datetimeoffset-class.md).  
  
Nelle sezioni seguenti vengono forniti esempi di come sia possibile utilizzare il driver JDBC e i tipi di dati di base. Per un esempio più dettagliato dell'utilizzo dei tipi di dati di base in un'applicazione Java, vedere [Esempio di tipi di dati di base](../../connect/jdbc/basic-data-types-sample.md).  
  
## <a name="retrieving-data-as-a-string"></a>Recupero di dati in forma di stringa

Se è necessario recuperare dati da un'origine dati con mapping a uno qualsiasi dei tipi di dati JDBC di base, per visualizzarli come stringa, o se non sono richiesti dati fortemente tipizzati, è possibile usare il metodo [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) della classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), come nell'esempio seguente:  
  
[!code[JDBC#UsingBasicDataTypes1](../../connect/jdbc/codesnippet/Java/using-basic-data-types_1.java)]  
  
## <a name="retrieving-data-by-data-type"></a>Recupero di dati per tipo di dati

Se è necessario recuperare dati di cui si conosce il tipo da un'origine dati, usare uno dei metodi get\<Type> della classe SQLServerResultSet, noti anche come *metodi getter*. Con i metodi get\<Type> è possibile usare un nome o un indice di colonna, come nell'esempio seguente:  
  
[!code[JDBC#UsingBasicDataTypes2](../../connect/jdbc/codesnippet/Java/using-basic-data-types_2.java)]  
  
> [!NOTE]  
> Il getUnicodeStream getBigDecimal con i metodi di scalabilità sono deprecati e non sono supportati dal driver JDBC.

## <a name="updating-data-by-data-type"></a>Aggiornamento di dati per tipo di dati

Se è necessario aggiornare il valore di un campo in un'origine dati, usare uno dell'aggiornamento\<tipo > i metodi della classe SQLServerResultSet. Nell'esempio seguente il metodo [updateInt](../../connect/jdbc/reference/updateint-method-sqlserverresultset.md) viene usato insieme al metodo [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) per aggiornare i dati nell'origine dati:  
  
[!code[JDBC#UsingBasicDataTypes3](../../connect/jdbc/codesnippet/Java/using-basic-data-types_3.java)]  
  
> [!NOTE]  
> Il driver JDBC non è in grado di aggiornare una colonna SQL Server il cui nome contiene più di 127 caratteri. Se si tenta di aggiornare una colonna il cui nome contiene più di 127 caratteri, verrà generata un'eccezione.  
  
## <a name="updating-data-by-parameterized-query"></a>Aggiornamento di dati mediante query con parametri

Se è necessario aggiornare dati in un'origine dati usando una query con parametri, è possibile impostare il tipo di dati dei parametri usando uno dei metodi set\<Type> della classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), noti anche come *metodi setter*. Nell'esempio seguente viene usato il metodo [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) per precompilare la query con parametri, quindi viene usato il metodo [setString](../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md) per impostare il valore stringa del parametro prima di chiamare il metodo [executeUpdate](../../connect/jdbc/reference/executeupdate-method.md).  
  
[!code[JDBC#UsingBasicDataTypes4](../../connect/jdbc/codesnippet/Java/using-basic-data-types_4.java)]  
  
Per altre informazioni sulle query con parametri, vedere [tramite un'istruzione SQL con parametri](../../connect/jdbc/using-an-sql-statement-with-parameters.md).  

## <a name="passing-parameters-to-a-stored-procedure"></a>Passaggio di parametri a una stored procedure

Se è necessario passare parametri tipizzati in una stored procedure, è possibile impostare i parametri in base all'indice o al nome usando uno dei metodi set\<Type> della classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Nell'esempio seguente viene usato il metodo [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) per impostare la chiamata alla stored procedure, quindi viene usato il metodo [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) per impostare il parametro per la chiamata prima di chiamare il metodo [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md).  
  
[!code[JDBC#UsingBasicDataTypes5](../../connect/jdbc/codesnippet/Java/using-basic-data-types_5.java)]  
  
> [!NOTE]  
> In questo esempio viene restituito un set di risultati con i risultati dell'esecuzione della stored procedure.

Per altre informazioni sull'utilizzo del driver JDBC con stored procedure e parametri di input, vedere [utilizzando una Stored Procedure con parametri di Input](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md).  

## <a name="retrieving-parameters-from-a-stored-procedure"></a>Recupero di parametri da una stored procedure

Se è necessario recuperare parametri da una stored procedure, occorre innanzitutto registrare un parametro OUT in base al nome o all'indice, usando il metodo [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) della classe SQLServerCallableStatement, e quindi assegnare il parametro OUT restituito a una variabile appropriata, dopo aver eseguito la chiamata alla stored procedure. Nell'esempio seguente viene usato il metodo prepareCall per impostare la chiamata alla stored procedure, quindi viene usato il metodo registerOutParameter per impostare il parametro OUT e infine viene usato il metodo [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) per impostare il parametro per la chiamata prima di chiamare il metodo executeQuery. Il valore restituito dal parametro OUT della stored procedure viene recuperato usando il metodo [getShort](../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md).  
  
[!code[JDBC#UsingBasicDataTypes6](../../connect/jdbc/codesnippet/Java/using-basic-data-types_6.java)]  
  
> [!NOTE]  
> Oltre al parametro out, può essere restituito anche un set di risultati con i risultati dell'esecuzione della stored procedure.  
  
Per altre informazioni su come usare il driver JDBC con stored procedure e parametri di output, vedere [utilizzando una Stored Procedure con parametri di Output](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md).  

## <a name="see-also"></a>Vedere anche

[Informazioni sui tipi di dati del driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
