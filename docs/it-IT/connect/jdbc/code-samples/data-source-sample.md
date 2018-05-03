---
title: Esempio di origine dati | Documenti Microsoft
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
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f900b1b91bb3d9114c4f7da2e4450da45fd9ec21
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-sample"></a>Esempio di origine dei dati
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] applicazione di esempio illustra come connettersi a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database utilizzando un oggetto origine dati. Viene inoltre illustrato come recuperare i dati da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database utilizzando una stored procedure.  
  
 Il file di codice per questo esempio è connectDS.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\connections  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario impostare il classpath per includere il file sqljdbc.jar o sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc.jar o sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Sarà inoltre necessario l'accesso per il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fornisce sqljdbc.jar e sqljdbc4.jar file della libreria di classe da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE). Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il codice di esempio imposta diverse proprietà di connessione utilizzando i metodi di impostazione del [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto e quindi chiama il [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) metodo il Oggetto SQLServerDataSource per restituire un [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.  
  
 Successivamente, il codice di esempio utilizza il [prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) metodo dell'oggetto SQLServerConnection per creare un [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetto, quindi il [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) metodo viene chiamato per eseguire la stored procedure.  
  
 Infine, viene utilizzato il [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto restituito dal metodo executeQuery per scorrere i risultati restituiti dalla stored procedure.  
  
```java
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class connectDS {  
  
   public static void main(String[] args) {  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      CallableStatement cstmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.   
         SQLServerDataSource ds = new SQLServerDataSource();  
         ds.setUser("UserName");  
         ds.setPassword("*****");  
         ds.setServerName("localhost");  
         ds.setPortNumber(1433);   
         ds.setDatabaseName("AdventureWorks");  
         con = ds.getConnection();  
  
         // Execute a stored procedure that returns some data.  
         cstmt = con.prepareCall("{call dbo.uspGetEmployeeManagers(?)}");  
         cstmt.setInt(1, 50);  
         rs = cstmt.executeQuery();  
  
         // Iterate through the data in the result set and display it.  
         while (rs.next()) {  
            System.out.println("EMPLOYEE: " + rs.getString("LastName") +   
               ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER: " + rs.getString("ManagerLastName") +   
               ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
         }  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      finally {  
         if (rs != null) try { rs.close(); } catch(Exception e) {}  
         if (cstmt != null) try { cstmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
         System.exit(1);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione e recupero dei dati](../../../connect/jdbc/connecting-and-retrieving-data.md)  
  
  
