---
title: Metodo getColumns (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f173fa5d-e114-4a37-a5c4-2baad9ff3af1
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 75d9ab3fb70f854e56df0c659275a2983a8487ff
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumns-method-sqlserverdatabasemetadata"></a>Metodo getColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione delle colonne di una tabella disponibili nel catalogo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getColumns(java.lang.String catalog,  
                                     java.lang.String schema,  
                                     java.lang.String table,  
                                     java.lang.String col)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalogo*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
 *schema*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema.  
  
 *table*  
  
 Oggetto **stringa** che contiene il modello di nome di tabella.  
  
 *col*  
  
 Oggetto **stringa** che contiene il modello di nome di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getColumns viene specificato dal metodo getColumns nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getColumns conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nome del catalogo.|  
|TABLE_SCHEM|**String**|Nome dello schema della tabella.|  
|TABLE_NAME|**String**|Il nome della tabella.|  
|COLUMN_NAME|**String**|Nome della colonna.|  
|DATA_TYPE|**smallint**|Tipo di dati SQL da java.sql.Types.|  
|TYPE_NAME|**String**|Nome del tipo di dati.|  
|COLUMN_SIZE|**int**|Precisione della colonna.|  
|BUFFER_LENGTH|**smallint**|Dimensioni di trasferimento dei dati.|  
|DECIMAL_DIGITS|**smallint**|Scala della colonna.|  
|NUM_PREC_RADIX|**smallint**|Radice della colonna.|  
|NULLABLE|**smallint**|Indica se la colonna ammette i valori Null. Può essere uno dei valori seguenti:<br /><br /> columnNoNulls (0)<br /><br /> columnNullable (1)|  
|REMARKS|**String**|Commenti associati alla colonna.<br /><br /> **Nota:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] restituisce sempre null per questa colonna.  |  
|COLUMN_DEF|**String**|Valore predefinito della colonna.|  
|SQL_DATA_TYPE|**smallint**|Valore del tipo di dati SQL visualizzato nel campo TYPE del descrittore. Questa colonna corrisponde alla colonna DATA_TYPE, tranne per i tipi di dati datetime e interval SQL-92. In questa colonna viene sempre restituito un valore.|  
|SQL_DATETIME_SUB|**smallint**|Codice di sottotipo per i tipi di dati SQL-92 datetime e interval. Per gli altri tipi di dati in questa colonna viene restituito NULL.|  
|CHAR_OCTET_LENGTH|**int**|Numero massimo di byte nella colonna.|  
|ORDINAL_POSITION|**int**|Indice della colonna all'interno della tabella.|  
|IS_NULLABLE|**String**|Indica se la colonna ammette valori Null.|  
|SS_IS_SPARSE|**smallint**|Se la colonna è una colonna di tipo sparse, questo presenta il valore 1. in caso contrario, 0. <sup>1</sup>|  
|SS_IS_COLUMN_SET|**smallint**|Se la colonna è la colonna column_set di tipo sparse, il relativo valore è 1; in caso contrario, è 0. <sup>1</sup>|  
|SS_IS_COMPUTED|**smallint**|Indica se una colonna in TABLE_TYPE è una colonna calcolata. <sup>1</sup>|  
|IS_AUTOINCREMENT|**String**|"YES" se la colonna è incrementata automaticamente. "NO" se la colonna non è incrementata automaticamente. "" (stringa vuota) se il driver non è in grado di determinare se la colonna è incrementata automaticamente. <sup>1</sup>|  
|SS_UDT_CATALOG_NAME|**String**|Nome del catalogo contenente il tipo definito dall'utente (UDT). <sup>1</sup>|  
|SS_UDT_SCHEMA_NAME|**String**|Nome dello schema contenente il tipo definito dall'utente (UDT). <sup>1</sup>|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|Tipo definito dall'utente (UDT) del nome completo. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|Nome del catalogo in cui viene definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome del catalogo, questa variabile contiene una stringa vuota. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|Nome dello schema in cui viene definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome dello schema, viene visualizzata una stringa vuota. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|Nome di una raccolta di XML Schema. Se non è possibile trovare il nome, viene visualizzata una stringa vuota. <sup>1</sup>|  
|SS_DATA_TYPE|**tinyint**|Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di dati utilizzato da stored procedure estese.<br /><br /> **Nota** per ulteriori informazioni sui tipi di dati restituito da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], vedere "Tipi di dati (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.|  
  
 (1) questa colonna non sarà presente se ci si connette a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)].  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getColumns, vedere "sp_columns (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
 Nel [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0, verrà visualizzato il seguente comportamento cambia da versioni precedenti del Driver JDBC:  
  
 La colonna DATA_TYPE include le modifiche seguenti:  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Tipo di dati|Tipo restituito in JDBC Driver 2.0 (o, se connessi a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)]) e costante numerica associata|Tipo restituito in JDBC Driver 3.0 quando si è connessi a [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)] o versione successiva|  
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|  
|tipo definito dall'utente maggiore di 8 kB|LONGVARBINARY (-4)|VARBINARY (-3)|  
|geography|LONGVARBINARY (-4)|VARBINARY (-3)|  
|geometry|LONGVARBINARY (-4)|VARBINARY (-3)|  
|varbinary(max)|LONGVARBINARY (-4)|VARBINARY (-3)|  
|nvarchar(max)|LONGVARCHAR (-1) o LONGNVARCHAR (JDBC 4) (-16)|VARCHAR (12) o NVARCHAR (JDBC 4) (-9)|  
|varchar(max)|LONGVARCHAR (-1)|VARCHAR (12)|  
|time|VARCHAR (12) o NVARCHAR (JDBC 4) (-9)|TIME (-154)|  
|data|VARCHAR (12) o NVARCHAR (JDBC 4) (-9)|DATE (91)|  
|datetime2|VARCHAR (12) o NVARCHAR (JDBC 4) (-9)|TIMESTAMP (93)|  
|datetimeoffset|VARCHAR (12) o NVARCHAR (JDBC 4) (-9)|microsoft.sql.Types.DATETIMEOFFSET (-155)|  
  
 La colonna COLUMN_SIZE presenta le modifiche seguenti:  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Tipo di dati|Tipo restituito in Microsoft JDBC Driver 2.0|Tipo restituito in Microsoft JDBC Driver 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|nvarchar(max)|1073741823|2147483647 (metadati del database)|  
|xml|1073741823|2147483647 (metadati del database)|  
|tipo definito dall'utente minore o uguale a 8 kB|8 KB (set di risultati e metadati del parametro)|Dimensioni effettive restituite dalla stored procedure.|  
|time||Lunghezza in caratteri della rappresentazione di stringa del tipo, presupponendo la precisione massima consentita del componente delle frazioni di secondo.|  
|data||Uguale a time|  
|datetime2||Uguale a time|  
|datetimeoffset||Uguale a time|  
  
 La colonna BUFFER_LENGTH presenta la modifica seguente:  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Tipo di dati|Tipo restituito in Microsoft JDBC Driver 2.0|Tipo restituito in Microsoft JDBC Driver 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|tipo definito dall'utente maggiore di 8 kB||2147483647|  
  
 La colonna TYPE_NAME presenta le modifiche seguenti:  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Tipo di dati|Tipo restituito in Microsoft JDBC Driver 2.0|Tipo restituito in Microsoft JDBC Driver 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|varchar(max)|text|varchar|  
|varbinary(max)|image|varbinary|  
  
 La colonna DECIMAL_DIGITS presenta le modifiche seguenti:  
  
|Tipo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]|Driver JDBC 2.0|Driver JDBC 3.0|  
|--------------------------------------------------------------|---------------------|---------------------|  
|time|null|7 (o inferiore se specificato)|  
|data|null|null|  
|datetime2|null|7 (o inferiore se specificato)|  
|datetimeoffset|null|7 (o inferiore se specificato)|  
  
 La colonna SQL_DATA_TYPE presenta le modifiche seguenti:  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Tipo di dati|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Valore di dati di 2008 in JDBC Driver 2.0|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Valore di dati di 2008 in JDBC Driver 3.0|  
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|varchar(max)|-10|-9|  
|nvarchar(max)|-1|-9|  
|xml|-10|-152|  
|tipo definito dall'utente minore o uguale a 8 kB|-3|-151|  
|tipo definito dall'utente maggiore di 8 kB|Non disponibile in JDBC Driver 2.0|-151|  
|geography|-4|-151|  
|geometry|-4|-151|  
|hierarchyid|-4|-151|  
|time|-9|92|  
|data|-9|91|  
|datetime2|-9|93|  
|datetimeoffset|-9|-155|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo getColumns per restituire informazioni per la tabella Person Contact il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
import java.sql.*;  
public class c1 {  
   public static void main(String[] args) {  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedsecurity=true";  
  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
         DatabaseMetaData dbmd = con.getMetaData();  
         rs = dbmd.getColumns("AdventureWorks", "Person", "Contact", "FirstName");  
  
         ResultSet r = dbmd.getColumns(null, null, "Contact", null);  
         ResultSetMetaData rm = r.getMetaData();   
         int noofcols = rm.getColumnCount();  
  
         if (r.next())  
            for (int i = 0 ; i < noofcols ; i++ )  
            System.out.println(rm.getColumnName( i + 1 ) + ": \t\t" + r.getString( i + 1 ));  
      }  
  
      catch (Exception e) {}  
      finally {}  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

