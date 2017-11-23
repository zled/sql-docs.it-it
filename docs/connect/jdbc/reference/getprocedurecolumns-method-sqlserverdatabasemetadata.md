---
title: Metodo getProcedureColumns (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getProcedureColumns
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 4f0df8fe-3cd6-46e4-ae3c-dc23c35676b2
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d8fa1fbb84392dba636c8aa5649f45cd54e397d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="getprocedurecolumns-method-sqlserverdatabasemetadata"></a>Metodo getProcedureColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione dei parametri delle stored procedure e delle colonne dei risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getProcedureColumns(java.lang.String sCatalog,  
                                              java.lang.String sSchema,  
                                              java.lang.String proc,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCatalog*  
  
 Oggetto **stringa** che contiene il nome del catalogo. Se si specifica Null per questo parametro, non è necessario utilizzare il nome del catalogo.  
  
 *SLO*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema. Se si specifica Null per questo parametro, non è necessario utilizzare il nome dello schema.  
  
 *proc*  
  
 Oggetto **stringa** che contiene il modello di nome di stored procedure.  
  
 *col*  
  
 Oggetto **stringa** che contiene il modello di nome di colonna. Se si specifica Null per questo parametro, viene restituita una riga per ogni colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getProcedureColumns viene specificato dal metodo getProcedureColumns nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getProcedureColumns conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**String**|Nome del database in cui si trova la stored procedure specificata.|  
|PROCEDURE_SCHEM|**String**|Schema per la stored procedure.|  
|PROCEDURE_NAME|**String**|Nome della stored procedure.|  
|COLUMN_NAME|**String**|Nome della colonna.|  
|COLUMN_TYPE|**breve**|Tipo di colonna. Può essere uno dei valori seguenti:<br /><br /> procedureColumnUnknown (0)<br /><br /> procedureColumnIn (1)<br /><br /> procedureColumnInOut (2)<br /><br /> procedureColumnOut (4)<br /><br /> procedureColumnReturn (5)<br /><br /> procedureColumnResult (3)|  
|DATA_TYPE|**smallint**|Tipo di dati SQL da java.sql.Types.|  
|TYPE_NAME|**String**|Nome del tipo di dati.|  
|PRECISION|**int**|Numero totale di cifre significative.|  
|LENGTH|**int**|Lunghezza dei dati in byte.|  
|SCALE|**breve**|Numero di cifre a destra del separatore decimale.|  
|RADIX|**breve**|Base per i tipi numerici.|  
|NULLABLE|**breve**|Indica se la colonna può contenere un valore Null. Può essere uno dei valori seguenti:<br /><br /> procedureNoNulls (0)<br /><br /> procedureNullable (1)<br /><br /> procedureNullableUnknown (2)|  
|REMARKS|**String**|Descrizione della colonna della procedura.<br /><br /> <br /><br /> **Nota:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] non restituisce un valore per questa colonna.|  
|COLUMN_DEF|**String**|Valore predefinito della colonna.|  
|SQL_DATA_TYPE|**smallint**|Questa colonna corrisponde alla **DATA_TYPE** colonna, tranne che per il **datetime** e ISO **intervallo** tipi di dati.|  
|SQL_DATETIME_SUB|**smallint**|Il **datetime** ISO **intervallo** sottocodice se il valore di **SQL_DATA_TYPE** è **SQL_DATETIME** o **SQL_INTERVAL**. Per i dati di tipi diversi da **datetime** e ISO **intervallo**, questa colonna è NULL.|  
|CHAR_OCTET_LENGTH|**int**|Numero massimo di byte nella colonna.|  
|ORDINAL_POSITION|**int**|Indice della colonna all'interno della tabella.|  
|IS_NULLABLE|**String**|Indica se la colonna ammette valori Null.|  
|SS_TYPE_CATALOG_NAME|**String**|Nome del catalogo contenente il tipo definito dall'utente (UDT).|  
|SS_TYPE_SCHEMA_NAME|**String**|Nome dello schema contenente il tipo definito dall'utente (UDT).|  
|SS_UDT_CATALOG_NAME|**String**|Tipo definito dall'utente (UDT) del nome completo.|  
|SS_UDT_SCHEMA_NAME|**String**|Nome del catalogo in cui viene definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome del catalogo, questa variabile contiene una stringa vuota.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|Nome dello schema in cui viene definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome dello schema, viene visualizzata una stringa vuota.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|Nome di una raccolta di XML Schema. Se non è possibile trovare il nome, viene visualizzata una stringa vuota.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|Nome del catalogo contenente il tipo definito dall'utente (UDT).|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|Nome dello schema contenente il tipo definito dall'utente (UDT).|  
|SS_DATA_TYPE|**tinyint**|Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di dati utilizzato da stored procedure estese.<br /><br /> <br /><br /> **Nota:** per ulteriori informazioni sui tipi di dati restituito da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], vedere "Tipi di dati (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.|  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getProcedureColumns, vedere "sp_sproc_columns (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo getProcedureColumns per restituire informazioni sulle stored procedure uspGetBillOfMaterials nel [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
public static void executeGetProcedureColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedureColumns(null, null, "uspGetBillOfMaterials", null);  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
