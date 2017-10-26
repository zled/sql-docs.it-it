---
title: Esempio di tipi di dati di base | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 424b1442a554cc2e4e52b0bf11c50c276d2a32cf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="basic-data-types-sample"></a>Esempio di tipi di dati di base
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] applicazione di esempio viene illustrato come utilizzare i metodi di richiamo del set di risultati per recuperare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] del tipo di dati, valori e come utilizzare i metodi di aggiornamento di set di risultati per aggiornare tali valori.  
  
 Il file di codice per questo esempio è basicDT.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\datatypes  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario impostare il classpath per includere il file sqljdbc.jar o sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc.jar o sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Sarà inoltre necessario l'accesso per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
 È inoltre necessario creare i seguenti dati di esempio e di tabella nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio:  
  
```  
use AdventureWorks  
CREATE TABLE DataTypesTable   
   (Col1 int IDENTITY,   
    Col2 char,  
    Col3 varchar(50),   
    Col4 bit,  
    Col5 decimal(18, 2),  
    Col6 money,  
    Col7 datetime,  
    Col8 date,  
    Col9 time,  
    Col10 datetime2,  
    Col11 datetimeoffset  
    );  
  
INSERT INTO DataTypesTable   
VALUES ('A', 'Some text.', 0, 15.25, 10.00, '01/01/2006 23:59:59.991', '01/01/2006', '23:59:59', '01/01/2006 23:59:59.12345', '01/01/2006 23:59:59.12345 -1:00')  
```  
  
> [!NOTE]  
>  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce sqljdbc.jar e sqljdbc4.jar file della libreria di classe da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE). Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il codice di esempio stabilisce una connessione per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] del database e quindi recupera una singola riga di dati dalla tabella di prova DataTypesTable. Viene quindi chiamato il metodo di displayRow personalizzato per visualizzare tutti i dati contenuti nell'insieme di risultati utilizzando diversi get\<tipo > metodi di [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
 Successivamente, nell'esempio vengono utilizzati vari aggiornamento\<tipo > metodi di SQLServerResultSet classe per aggiornare i dati contenuti nel set di risultati e quindi chiama il [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) metodo per inviare nuovamente i dati al database.  
  
 Impostare infine vengono aggiornati i dati contenuti nel risultato, impostare e quindi chiama il metodo displayRow personalizzato per visualizzare i dati contenuti nel risultato.  
  
```java
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;  
import microsoft.sql.DateTimeOffset;  
  
public class basicDT {  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedSecurity=true;";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement that returns some data  
         // and display it.  
         String SQL = "SELECT * FROM DataTypesTable";  
         stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);  
         rs = stmt.executeQuery(SQL);           
         rs.next();  
         displayRow("ORIGINAL DATA", rs);  
  
         // Update the data in the result set.  
         rs.updateString(2, "B");  
         rs.updateString(3, "Some updated text.");  
         rs.updateBoolean(4, true);  
         rs.updateDouble(5, 77.89);  
         rs.updateDouble(6, 1000.01);  
         long timeInMillis = System.currentTimeMillis();  
         Timestamp ts = new Timestamp(timeInMillis);  
         rs.updateTimestamp(7, ts);  
         rs.updateDate(8, new Date(timeInMillis));  
         rs.updateTime(9, new Time(timeInMillis));  
         rs.updateTimestamp(10, ts);  
  
         //-480 indicates GMT - 8:00 hrs  
         ((SQLServerResultSet)rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));  
  
         rs.updateRow();  
  
         // Get the updated data from the database and display it.  
         rs = stmt.executeQuery(SQL);  
         rs.next();  
         displayRow("UPDATED DATA", rs);  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
  
      finally {  
         if (rs != null)   
         try {   
         rs.close();   
         }   
         catch(Exception e) {}  
  
         if (stmt != null)   
         try { stmt.close();   
         }   
         catch(Exception e) {}  
  
         if (con != null)   
         try {   
         con.close();   
         }   
         catch(Exception e) {}  
      }  
   }  
  
   private static void displayRow(String title, ResultSet rs) {  
      try {  
         System.out.println(title);  
         System.out.println(rs.getInt(1) + " , " +  // SQL integer type.  
               rs.getString(2) + " , " +            // SQL char type.  
               rs.getString(3) + " , " +            // SQL varchar type.  
               rs.getBoolean(4) + " , " +           // SQL bit type.  
               rs.getDouble(5) + " , " +            // SQL decimal type.  
               rs.getDouble(6) + " , " +            // SQL money type.  
               rs.getTimestamp(7) + " , " +            // SQL datetime type.  
               rs.getDate(8) + " , " +              // SQL date type.  
               rs.getTime(9) + " , " +              // SQL time type.  
               rs.getTimestamp(10) + " , " +            // SQL datetime2 type.  
               ((SQLServerResultSet)rs).getDateTimeOffset(11)); // SQL datetimeoffset type.   
  
         System.out.println();  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di tipi di dati &#40; JDBC &#41;](../../connect/jdbc/working-with-data-types-jdbc.md)  
  
  

