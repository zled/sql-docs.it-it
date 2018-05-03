---
title: Metodo getColumnPrivileges (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getColumnPrivileges
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ab6a671-9573-4b95-8c23-364306c60d25
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7321560bcfaaf5b448841319280a9dd4f6b8fd38
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getcolumnprivileges-method-sqlserverdatabasemetadata"></a>Metodo getColumnPrivileges (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione dei diritti di accesso per le colonne di una tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getColumnPrivileges(java.lang.String catalog,  
                                              java.lang.String schema,  
                                              java.lang.String table,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
 *schema*  
  
 Oggetto **stringa** che contiene il nome dello schema.  
  
 *table*  
  
 Oggetto **stringa** che contiene il nome della tabella.  
  
 *col*  
  
 Oggetto **stringa** che contiene il modello di nome di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getColumnPrivileges viene specificato dal metodo getColumnPrivileges nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getColumnPrivileges conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nome del catalogo.|  
|TABLE_SCHEM|**String**|Nome dello schema della tabella.|  
|TABLE_NAME|**String**|Il nome della tabella.|  
|COLUMN_NAME|**String**|Nome della colonna.|  
|GRANTOR|**String**|Oggetto che concede l'accesso.|  
|GRANTEE|**String**|Oggetto a cui si concede l'accesso.|  
|PRIVILEGE|**String**|Tipo di accesso concesso.|  
|IS_GRANTABLE|**String**|Indica se l'utente autorizzato può concedere l'accesso agli altri utenti.|  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getColumnPrivileges, vedere "sp_column_privileges (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo getColumnPrivileges per restituire i diritti di accesso per la colonna FirstName nella tabella Person. Contact il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
public static void executeGetColumnPrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getColumnPrivileges("AdventureWorks", "Person", "Contact", "FirstName");  
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
  
  
