---
title: Modifica risultato serie di dati di esempio | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b5ae54dc-2a79-4664-bb21-cacdb7d745e1
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47b2f8566607ec119aaa61a29468c7fca6388b5e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32831946"
---
# <a name="modifying-result-set-data-sample"></a>Esempio di modifica dei dati dei set di risultati
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] applicazione di esempio viene illustrato come recuperare un set aggiornabile di dati da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database. Quindi, usando metodi di [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) dell'oggetto, che inserisce, modifica e infine eliminata una riga di dati dal set di dati.  
  
 Il file di codice per questo esempio è updateRS.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\resultsets  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario impostare il classpath per includere il file sqljdbc.jar o sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc.jar o sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Sarà inoltre necessario l'accesso per il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fornisce sqljdbc.jar e sqljdbc4.jar file della libreria di classe da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE). Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il codice di esempio stabilisce una connessione per il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio. Quindi, usando un'istruzione SQL con il [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) dell'oggetto, che esegue l'istruzione SQL e inserisce i dati restituiti in un oggetto SQLServerResultSet aggiornabile.  
  
 Successivamente, il codice di esempio utilizza il [moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md) per spostare il set di risultati del cursore nella riga di inserimento, utilizza una serie di [updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) metodi per inserire dati nella nuova riga e quindi chiama il [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) metodo in modo permanente la nuova riga di dati nel database.  
  
 Dopo aver inserito la nuova riga di dati, il codice di esempio utilizza un'istruzione SQL per recuperare la riga precedentemente inserita e quindi utilizza la combinazione di updateString e [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) eseguire metodi per aggiornare la riga di dati e renderla di nuovo permanente il database.  
  
 Infine, il codice di esempio recupera la riga di dati precedentemente aggiornata e quindi eliminarlo dal database utilizzando il [deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md) metodo.  
  
```java
import java.sql.*;  
  
public class updateRS {  
  
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
  
         // Create and execute an SQL statement, retrieving an updateable result set.  
         String SQL = "SELECT * FROM HumanResources.Department;";  
         stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);  
         rs = stmt.executeQuery(SQL);  
  
         // Insert a row of data.  
         rs.moveToInsertRow();  
         rs.updateString("Name", "Accounting");  
         rs.updateString("GroupName", "Executive General and Administration");  
         rs.updateString("ModifiedDate", "08/01/2006");  
         rs.insertRow();  
  
         // Retrieve the inserted row of data and display it.  
         SQL = "SELECT * FROM HumanResources.Department WHERE Name = 'Accounting';";  
         rs = stmt.executeQuery(SQL);  
         displayRow("ADDED ROW", rs);  
  
         // Update the row of data.  
         rs.first();  
         rs.updateString("GroupName", "Finance");  
         rs.updateRow();  
  
         // Retrieve the updated row of data and display it.  
         rs = stmt.executeQuery(SQL);  
         displayRow("UPDATED ROW", rs);  
  
         // Delete the row of data.  
         rs.first();  
         rs.deleteRow();  
         System.out.println("ROW DELETED");  
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
            System.out.println(rs.getString("Name") + " : " + rs.getString("GroupName"));  
            System.out.println();  
         }  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei set di risultati](../../../connect/jdbc/working-with-result-sets.md)  
  
  
