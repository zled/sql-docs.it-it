---
title: Metodo getTablePrivileges (SQLServerDatabaseMetaData) | Documenti Microsoft
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
apiname: SQLServerDatabaseMetaData.getTablePrivileges
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 0610d667-a16d-4201-a14b-0a40048911e1
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b0164ce48c06196a71bd9831bb5b66b4a2ad4395
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="gettableprivileges-method-sqlserverdatabasemetadata"></a>Metodo getTablePrivileges (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione dei diritti di accesso di ogni tabella disponibile nel modello di nome di catalogo, di schema o di tabella specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getTablePrivileges(java.lang.String catalog,  
                                             java.lang.String schema,  
                                             java.lang.String table)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalogo*  
  
 Oggetto **stringa** che contiene il nome del catalogo. Se si specifica Null per questo parametro, non è necessario utilizzare il nome del catalogo.  
  
 *schema*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema. Se si specifica Null per questo parametro, non è necessario utilizzare il nome dello schema.  
  
 *table*  
  
 Oggetto **stringa** che contiene il modello di nome di tabella.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getTablePrivileges viene specificato dal metodo getTablePrivileges nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getTablePrivileges conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nome del catalogo.|  
|TABLE_SCHEM|**String**|Nome dello schema della tabella.|  
|TABLE_NAME|**String**|Il nome della tabella.|  
|GRANTOR|**String**|Oggetto che concede l'accesso.|  
|GRANTEE|**String**|Oggetto a cui si concede l'accesso.|  
|PRIVILEGE|**String**|Tipo di accesso concesso.|  
|IS_GRANTABLE|**String**|Indica se l'utente autorizzato può concedere l'accesso agli altri utenti.|  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getTablePrivileges, vedere "sp_table_privileges (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo getTablePrivileges per restituire i diritti di accesso per la tabella Person Contact il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
public static void executeGetTablePrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTablePrivileges("AdventureWorks", "Person", "Contact");  
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
  
  
