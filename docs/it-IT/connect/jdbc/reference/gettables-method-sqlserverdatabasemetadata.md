---
title: Metodo getTables (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
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
apiname:
- SQLServerDatabaseMetaData.getTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a7514673-3457-4541-9560-28a8284ad9e3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 049fa3d23b4555534d4b82cbc8ae4d8f5cbd58a6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="gettables-method-sqlserverdatabasemetadata"></a>Metodo getTables (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione delle tabelle disponibili nel modello di nome di catalogo, di schema o di tabella specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getTables(java.lang.String catalog,  
                                    java.lang.String schema,  
                                    java.lang.String table,  
                                    java.lang.String[] types)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Oggetto **stringa** che contiene il nome del catalogo. Se si specifica Null per questo parametro, non è necessario utilizzare il nome del catalogo.  
  
 *schema*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema. Se si specifica Null per questo parametro, non è necessario utilizzare il nome dello schema.  
  
 *tableName*  
  
 Oggetto **stringa** che contiene il modello di nome di tabella.  
  
 *Tipi*  
  
 Matrice di stringhe contenente i tipi di tabelle da includere. Null indica che devono essere inclusi tutti i tipi di tabelle.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getTables viene specificato dal metodo getTables nell'interfaccia DatabaseMetaData.  
  
 Set di risultati restituito dal metodo getTables conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nome del database contenente la tabella specificata.|  
|TABLE_SCHEM|**String**|Nome dello schema della tabella.|  
|TABLE_NAME|**String**|Il nome della tabella.|  
|TABLE_TYPE|**String**|Tipo di tabella.|  
|REMARKS|**String**|Descrizione della tabella.<br /><br /> **Nota:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] non restituisce un valore per questa colonna.  |  
|TYPE_CAT|**String**|Non supportato dal driver JDBC.|  
|TYPE_SCHEM|**String**|Non supportato dal driver JDBC.|  
|TYPE_NAME|**String**|Non supportato dal driver JDBC.|  
|SELF_REFERENCING_COL_NAME|**String**|Non supportato dal driver JDBC.|  
|REF_GENERATION|**String**|Non supportato dal driver JDBC.|  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getTables, vedere "sp_tables (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo getTables per restituire le informazioni di descrizione di tabella per la tabella Person Contact il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
public static void executeGetTables(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTables("AdventureWorks", "Person", "Contact", null);  
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
  
  
