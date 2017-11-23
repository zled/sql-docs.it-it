---
title: Metodo getTypeInfo (SQLServerDatabaseMetaData) | Documenti Microsoft
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
apiname: SQLServerDatabaseMetaData.getTypeInfo
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 23208f01-c1bf-4235-b29c-9051d3df59a3
caps.latest.revision: "21"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2424ec8f3b484272d2311ac7880cc8810561bd2e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="gettypeinfo-method-sqlserverdatabasemetadata"></a>Metodo getTypeInfo (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione di tutti i tipi SQL standard supportati dal database corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getTypeInfo()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getTypeInfo viene specificato dal metodo getTypeInfo nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getTypeInfo conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|TYPE_NAME|**String**|Nome del tipo di dati.|  
|DATA_TYPE|**breve**|Tipo di dati SQL da java.sql.Types.|  
|PRECISION|**int**|Numero totale di cifre significative.|  
|LITERAL_PREFIX|**String**|Uno o più caratteri che precedono il nome di una costante.|  
|LITERAL_SUFFIX|**String**|Uno o più caratteri che seguono il nome di una costante.|  
|CREATE_PARAMS|**String**|Descrizione dei parametri di creazione per il tipo di dati.|  
|NULLABLE|**breve**|Indica se la colonna può contenere un valore Null. Può essere uno dei valori seguenti:<br /><br /> typeNoNulls (0)<br /><br /> typeNullable (1)<br /><br /> typeNullableUnknown (2)|  
|CASE_SENSITIVE|**boolean**|Indica se il tipo di dati supporta la distinzione tra maiuscole e minuscole. "**true**"se il tipo viene fatta distinzione tra maiuscole e minuscole; in caso contrario,"**false**".|  
|SEARCHABLE|**breve**|Indica se la colonna può essere utilizzata in una clausola WHERE SQL. Può essere uno dei valori seguenti:<br /><br /> typePredNone (0)<br /><br /> typePredChar (1)<br /><br /> typePredBasic (2)<br /><br /> typeSeachable (3)|  
|UNSIGNED_ATTRIBUTE|**boolean**|Indica il segno del tipo di dati. "**true**"se il tipo è senza segno; in caso contrario,"**false**".|  
|FIXED_PREC_SCALE|**boolean**|Indica se il tipo di dati può essere un valore money. "**true**" se il tipo di dati è di tipo money; in caso contrario, "**false**".|  
|AUTO_INCREMENT|**boolean**|Indica se il tipo di dati può essere incrementato automaticamente. "**true**"se il tipo può essere incrementato automaticamente; in caso contrario,"**false**".|  
|LOCAL_TYPE_NAME|**String**|Nome localizzato del tipo di dati.|  
|MINIMUM_SCALE|**breve**|Numero massimo di cifre a destra del separatore decimale.|  
|MAXIMUM_SCALE|**breve**|Numero minimo di cifre a destra del separatore decimale.|  
|SQL_DATA_TYPE|**int**|Non supportato dal driver JDBC.|  
|SQL_DATETIME_SUB|**int**|Non supportato dal driver JDBC.|  
|NUM_PREC_RADIX|**int**|Numero di bit o di cifre per il calcolo del numero massimo che una colonna può contenere.|  
|INTERVAL_PRECISION|**smallint**|Valore di precisione iniziale dell'intervallo.|  
|USERTYPE|**smallint**|Il **usertype** valore il **systypes** tabella. Per ulteriori informazioni, vedere la documentazione online di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getTypeInfo, vedere "sp_datatype_info (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare il metodo getTypeInfo per restituire informazioni sui tipi di dati utilizzati un [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)] (o versione successiva) database.  
  
```  
public static void executeGetTypeInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTypeInfo();  
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
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
