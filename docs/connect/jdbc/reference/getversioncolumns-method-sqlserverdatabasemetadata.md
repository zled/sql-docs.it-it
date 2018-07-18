---
title: Metodo getVersionColumns (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getVersionColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dd275d3-d9b2-4db7-938a-d4406c940a7a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 722fd20c9210b14cb503ab3a0189815fa3cc83dd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32841626"
---
# <a name="getversioncolumns-method-sqlserverdatabasemetadata"></a>Metodo getVersionColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione delle colonne di una tabella che viene aggiornata automaticamente all'aggiornamento di un valore di una riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getVersionColumns(java.lang.String catalog,  
                                            java.lang.String schema,  
                                            java.lang.String table)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
 *schema*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema.  
  
 *table*  
  
 Oggetto **stringa** che contiene il nome della tabella.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getVersionColumns viene specificato dal metodo getVersionColumns nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getVersionColumns conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|SCOPE|**short**|Non supportato dal driver JDBC.|  
|COLUMN_NAME|**String**|Nome della colonna.|  
|DATA_TYPE|**short**|Tipo di dati SQL da java.sql.Types.|  
|TYPE_NAME|**String**|Nome del tipo di dati.|  
|COLUMN_SIZE|**int**|Precisione della colonna.|  
|BUFFER_LENGTH|**int**|Lunghezza della colonna in byte.|  
|DECIMAL_DIGITS|**short**|Scala della colonna.|  
|PSEUDO_COLUMN|**short**|Indica se la colonna è una pseudocolonna. Può essere uno dei valori seguenti:<br /><br /> versionColumnUnknown (0)<br /><br /> versionColumnNotPseudo (1)<br /><br /> versionColumnPseudo (2)|  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getVersionColumns, vedere "sp_datatype_info (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo getVersionColumns per restituire informazioni sulle colonne che vengono aggiornate automaticamente nella tabella Person. Contact il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
public static void executeGetVersionColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getVersionColumns("AdventureWorks", "Person", "Contact");  
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
  
  
