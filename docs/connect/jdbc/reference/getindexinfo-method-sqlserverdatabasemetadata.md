---
title: Metodo getIndexInfo (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getIndexInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 028937d023b6cf899eb5fa47354cb0c5d21545bc
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getindexinfo-method-sqlserverdatabasemetadata"></a>Metodo getIndexInfo (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione degli indici e delle statistiche per la tabella specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getIndexInfo(java.lang.String cat,  
                                       java.lang.String schema,  
                                       java.lang.String table,  
                                       boolean unique,  
                                       boolean approximate)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Cat*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
 *schema*  
  
 Oggetto **stringa** che contiene il nome dello schema.  
  
 *table*  
  
 Oggetto **stringa** che contiene il nome della tabella.  
  
 *univoco*  
  
 **true** se solo vengono restituiti gli indici per i valori univoci. **false** se vengono restituiti tutti gli indici.  
  
 *approssimativo*  
  
 **true** se i risultati riflettono i valori approssimativi o non aggiornati. **false** se i risultati sono precisi.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getIndexInfo viene specificato dal metodo getIndexInfo nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getIndexInfo conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nome del database contenente la tabella specificata.|  
|TABLE_SCHEM|**String**|Schema della tabella.|  
|TABLE_NAME|**String**|Nome della tabella.|  
|NON_UNIQUE|**boolean**|Indica se i valori di indice possono essere non univoci.|  
|INDEX_QUALIFIER|**String**|Nome del proprietario dell'indice. Sarà Null se TYPE è tableIndexStatistic.|  
|INDEX_NAME|**String**|Nome dell'indice.|  
|TYPE|**breve**|Tipo dell'indice. Può essere uno dei valori seguenti:<br /><br /> tableIndexStatistic (0)<br /><br /> tableIndexClustered (1)<br /><br /> tableIndexHashed (2)<br /><br /> tableIndexOther (3)|  
|ORDINAL_POSITION|**breve**|Posizione ordinale della colonna nell'indice. La prima colonna nell'indice è 1.|  
|COLUMN_NAME|**String**|Nome della colonna.|  
|ASC_OR_DESC|**String**|Ordine utilizzato nelle regole di confronto dell'indice. Può essere uno dei valori seguenti:<br /><br /> A (crescente)<br /><br /> D (decrescente)<br /><br /> NULL (non applicabile)<br /><br /> **Nota:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] restituisce sempre "A".  |  
|CARDINALITY|**int**|Numero di righe nella tabella o di valori univoci nell'indice.|  
|PAGES|**int**|Numero di pagine utilizzate per l'archiviazione dell'indice o della tabella.|  
|FILTER_CONDITION|**String**|Condizione di filtro.<br /><br /> **Nota:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] restituisce sempre null.  |  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getIndexInfo, vedere "sp_indexes (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare il metodo getIndexInfo per restituire informazioni sugli indici e statistiche della tabella Person Contact il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
public static void executeGetIndexInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getIndexInfo("AdventureWorks", "Person", "Contact", false, true);  
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
  
  
