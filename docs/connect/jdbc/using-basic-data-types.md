---
title: Utilizzo di tipi di dati di base | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d7044936-5b8c-4def-858c-28a11ef70a97
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab39b74b4e5a2c243622bbd352a71c943e07a3d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852669"
---
# <a name="using-basic-data-types"></a>Utilizzo di tipi di dati di base
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] vengono utilizzati i tipi di dati di base di JDBC per convertire il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati in un formato comprensibile nel linguaggio di programmazione Java e viceversa. Il driver JDBC fornisce supporto per l'API di JDBC 4.0, che include il **SQLXML** tipo di dati e i tipi di dati nazionali (Unicode), ad esempio **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, e **NCLOB**.  
  
## <a name="data-type-mappings"></a>Mapping di tipi di dati  
 Nella tabella seguente sono elencati i mapping predefiniti tra gli elementi di base [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], JDBC e i tipi di dati del linguaggio di programmazione Java:  
  
|Tipi di SQL Server|Tipi JDBC (java.sql.Types)|Tipi del linguaggio Java|  
|----------------------|-----------------------------------|-------------------------|  
|bigint|bigint|long|  
|BINARY|BINARY|byte[]|  
|bit|BIT|boolean|  
|char|CHAR|String|  
|data|DATE|java.sql.Date|  
|datetime|TIMESTAMP|java.sql.Timestamp|  
|datetime2|TIMESTAMP|java.sql.Timestamp|  
|datetimeoffset (2)|microsoft.sql.Types.DATETIMEOFFSET|microsoft.sql.DateTimeOffset|  
|Decimal|DECIMAL|java.math.BigDecimal|  
|float|DOUBLE|double|  
|image|LONGVARBINARY|byte[]|  
|int|INTEGER|int|  
|money|DECIMAL|java.math.BigDecimal|  
|NCHAR|CHAR<br /><br /> NCHAR (Java SE 6.0)|String|  
|ntext|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|String|  
|numeric|NUMERIC|java.math.BigDecimal|  
|nvarchar|VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)|String|  
|nvarchar(max)|VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)|String|  
|real|REAL|float|  
|smalldatetime|TIMESTAMP|java.sql.Timestamp|  
|smallint|SMALLINT|short|  
|smallmoney|DECIMAL|java.math.BigDecimal|  
|text|LONGVARCHAR|String|  
|time|TIME (1)|java.sql.Time (1)|  
|timestamp|BINARY|byte[]|  
|tinyint|TINYINT|short|  
|udt|VARBINARY|byte[]|  
|uniqueidentifier|CHAR|String|  
|varbinary|VARBINARY|byte[]|  
|varbinary(max)|VARBINARY|byte[]|  
|varchar|VARCHAR|String|  
|ntext|VARCHAR|String|  
|xml|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|String<br /><br /> SQLXML|  
|SQLVARIANT|SQLVARIANT|Oggetto|  
  
 (1) per utilizzare Java.SQL. Time con il tempo [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo, è necessario impostare il **sendTimeAsDatetime** proprietà di connessione su false.  
  
 (2) è possibile accedere a livello di codice i valori di **datetimeoffset** con [classe DateTimeOffset](../../connect/jdbc/reference/datetimeoffset-class.md).  
  
 Nelle sezioni seguenti vengono forniti esempi di come sia possibile utilizzare il driver JDBC e i tipi di dati di base. Per un esempio più dettagliato di come utilizzare i tipi di dati di base in un'applicazione Java, vedere [esempio tipi di dati Basic](../../connect/jdbc/basic-data-types-sample.md).  
  
## <a name="retrieving-data-as-a-string"></a>Recupero di dati in forma di stringa  
 Se è necessario recuperare dati da un'origine dati che esegue il mapping a uno dei tipi di dati di base di JDBC per visualizzarli come stringa o se non sono necessari dati fortemente tipizzati, è possibile utilizzare il [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) (classe), come illustrato di seguito:  
  
 [!code[JDBC#UsingBasicDataTypes1](../../connect/jdbc/codesnippet/Java/using-basic-data-types_1.java)]  
  
## <a name="retrieving-data-by-data-type"></a>Recupero di dati per tipo di dati  
 È necessario recuperare dati da un'origine dati, se si conosce il tipo di dati che viene recuperati, utilizzare uno dei get\<tipo > metodi di SQLServerResultSet, noto anche come classe di *metodi di richiamo*. È possibile utilizzare un nome di colonna o un indice di colonna con get\<tipo > metodi, come illustrato di seguito:  
  
 [!code[JDBC#UsingBasicDataTypes2](../../connect/jdbc/codesnippet/Java/using-basic-data-types_2.java)]  
  
> [!NOTE]  
>  Il getUnicodeStream getBigDecimal con metodi di scala sono deprecati e non sono supportate dal driver JDBC.  
  
## <a name="updating-data-by-data-type"></a>Aggiornamento di dati per tipo di dati  
 Se è necessario aggiornare il valore di un campo in un'origine dati, utilizzare uno dell'aggiornamento\<tipo > metodi della classe SQLServerResultSet. Nell'esempio seguente, il [updateInt](../../connect/jdbc/reference/updateint-method-sqlserverresultset.md) metodo viene utilizzato in combinazione con il [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) metodo per aggiornare i dati nell'origine dati:  
  
 [!code[JDBC#UsingBasicDataTypes3](../../connect/jdbc/codesnippet/Java/using-basic-data-types_3.java)]  
  
> [!NOTE]  
>  Il driver JDBC non è in grado di aggiornare una colonna SQL Server il cui nome contiene più di 127 caratteri. Se si tenta di aggiornare una colonna il cui nome contiene più di 127 caratteri, verrà generata un'eccezione.  
  
## <a name="updating-data-by-parameterized-query"></a>Aggiornamento di dati mediante query con parametri  
 Se è necessario aggiornare i dati in un'origine dati utilizzando una query con parametri, è possibile impostare il tipo di dati dei parametri utilizzando uno dei set di\<tipo > metodi del [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) , noto anche come classe di *metodi setter*. Nell'esempio seguente, il [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) metodo viene utilizzato per precompilare la query con parametri, quindi il [setString](../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md) metodo viene utilizzato per impostare il valore di stringa del parametro prima di [executeUpdate](../../connect/jdbc/reference/executeupdate-method.md) metodo viene chiamato.  
  
 [!code[JDBC#UsingBasicDataTypes4](../../connect/jdbc/codesnippet/Java/using-basic-data-types_4.java)]  
  
 Per ulteriori informazioni sulle query con parametri, vedere [utilizzando un'istruzione SQL con parametri](../../connect/jdbc/using-an-sql-statement-with-parameters.md).  
  
## <a name="passing-parameters-to-a-stored-procedure"></a>Passaggio di parametri a una stored procedure  
 Se è necessario passare parametri tipizzati in una stored procedure, è possibile impostare i parametri in base all'indice o al nome utilizzando uno dei set di\<tipo > metodi di [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe. Nell'esempio seguente, il [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) metodo viene utilizzato per impostare la chiamata alla stored procedure e quindi la [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) metodo viene utilizzato per impostare il parametro per la chiamata prima di [ executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) metodo viene chiamato.  
  
 [!code[JDBC#UsingBasicDataTypes5](../../connect/jdbc/codesnippet/Java/using-basic-data-types_5.java)]  
  
> [!NOTE]  
>  In questo esempio viene restituito un set di risultati con i risultati dell'esecuzione della stored procedure.  
  
 Per ulteriori informazioni sull'utilizzo del driver JDBC con stored procedure e parametri di input, vedere [utilizzando una Stored Procedure con parametri di Input](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md).  
  
## <a name="retrieving-parameters-from-a-stored-procedure"></a>Recupero di parametri da una stored procedure  
 Se è necessario recuperare parametri da una stored procedure, innanzitutto registrare un parametro out in base al nome o indice utilizzando il [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) metodo della classe SQLServerCallableStatement e assegnare quindi il ha restituito il parametro out a una variabile appropriata dopo aver eseguito la chiamata alla stored procedure. Nell'esempio seguente viene utilizzato il metodo prepareCall per impostare la chiamata alla stored procedure, il metodo registerOutParameter viene utilizzato per impostare il parametro out e quindi la [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) metodo viene utilizzato per impostare il parametro per il chiamata prima della chiamata al metodo executeQuery. Il valore restituito dal parametro out della stored procedure viene recuperato utilizzando il [getShort](../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md) metodo.  
  
 [!code[JDBC#UsingBasicDataTypes6](../../connect/jdbc/codesnippet/Java/using-basic-data-types_6.java)]  
  
> [!NOTE]  
>  Oltre al parametro out, può essere restituito anche un set di risultati con i risultati dell'esecuzione della stored procedure.  
  
 Per ulteriori informazioni su come utilizzare il driver JDBC con stored procedure e parametri di output, vedere [utilizzando una Stored Procedure con parametri di Output](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
