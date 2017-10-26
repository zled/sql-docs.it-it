---
title: Il recupero dei risultati imposta dati di esempio | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b190c36-3d38-49a2-8599-612329675851
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a2399dd259a9b06e2410c88c07991feb400b9080
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="retrieving-result-set-data-sample"></a>Esempio di recupero dei dati del set di risultati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] applicazione di esempio viene illustrato come recuperare un set di dati da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database e quindi visualizzare i dati.  
  
 Il file di codice per questo esempio è denominato retrieveRS.java e si trova nella seguente posizione:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\resultsets  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario impostare il classpath per includere il file sqljdbc.jar o sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc.jar o sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Sarà inoltre necessario l'accesso per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce sqljdbc.jar e sqljdbc4.jar file della libreria di classe da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE). Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il codice di esempio stabilisce una connessione per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. Quindi, usando un'istruzione SQL con il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) dell'oggetto, che esegue l'istruzione SQL e inserisce i dati restituiti vengono posizionati in un [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
 Successivamente, il codice di esempio chiama il metodo displayRow personalizzato per scorrere le righe di dati contenuti nel set di risultati e utilizza il [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) metodo per visualizzare alcuni dei dati in esso contenuti.  
  
```java
import java.sql.*;  
  
public class retrieveRS {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
            "databaseName=AdventureWorks;integratedSecurity=true;";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement that returns a  
         // set of data and then display it.  
         String SQL = "SELECT * FROM Production.Product;";  
         stmt = con.createStatement();  
         rs = stmt.executeQuery(SQL);  
         displayRow("PRODUCTS", rs);  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
  
      finally {  
         if (rs != null) try { rs.close(); } catch(Exception e) {}  
         if (stmt != null) try { stmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
      }  
   }  
  
   private static void displayRow(String title, ResultSet rs) {  
      try {  
         System.out.println(title);  
         while (rs.next()) {  
            System.out.println(rs.getString("ProductNumber") + " : " + rs.getString("Name"));  
         }  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei set di risultati](../../connect/jdbc/working-with-result-sets.md)  
  
  

