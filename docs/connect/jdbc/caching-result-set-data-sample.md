---
title: La memorizzazione nella cache risultato impostare dati di esempio | Documenti Microsoft
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
ms.assetid: 13a95ebb-996c-4713-a1bd-5834fe22a334
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 131bf443f88c0071dcb158fb67c997d6b0c57de2
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="caching-result-set-data-sample"></a>Esempio di memorizzazione nella cache dei dati dei set di risultati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] applicazione di esempio viene illustrato come recuperare un ampio set di dati da un database e quindi controllare il numero di righe di dati che vengono memorizzati nella cache sul client utilizzando il [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) metodo il [ SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
> [!NOTE]  
>  La limitazione del numero di righe inserite nella cache del client è un'operazione diversa dalla limitazione del numero totale di righe contenute in un set di risultati. Per controllare il numero totale di righe contenute in un set di risultati, utilizzare il [setMaxRows](../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto, che viene ereditata da entrambi i [ SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetti.  
  
 Per impostare un limite al numero di righe nella cache del client, è innanzitutto necessario utilizzare un cursore sul lato server quando si crea un oggetto istruzione specificando esplicitamente il tipo di cursore da utilizzare durante la creazione dell'oggetto istruzione. Ad esempio, il driver JDBC fornisce il tipo di cursore TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, ovvero un fast forward only, sola lettura cursore sul lato server per l'utilizzo con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
> [!NOTE]  
>  Un'alternativa all'utilizzo del tipo di cursore specifico per SQL Server è l'utilizzo della proprietà della stringa di connessione selectMethod, impostandone il valore su "cursor". Per ulteriori informazioni sui tipi di cursore supportati dal driver JDBC, vedere [informazioni sui tipi di cursore](../../connect/jdbc/understanding-cursor-types.md).  
  
 Dopo aver eseguito la query contenuta nell'oggetto Statement e i dati vengano restituiti al client come set di risultati, è possibile chiamare il metodo setFetchSize per controllare la quantità di dati vengono recuperati dal database in una sola volta. Ad esempio, se si dispone di una tabella che contiene 100 righe di dati e si imposta su 10 la dimensione del recupero, verranno inserite nella cache del client solo 10 righe di dati in qualsiasi momento. In questo modo verrà ridotta la velocità di elaborazione dei dati, ma si otterrà il vantaggio di utilizzare una quantità inferiore di memoria nel client, il che può risultare particolarmente utile quando si elaborano grandi quantità di dati.  
  
 Il file di codice per questo esempio è cacheRS.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\resultsets  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario impostare il classpath per includere il file sqljdbc.jar o sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc.jar o sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Sarà inoltre necessario l'accesso per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce sqljdbc.jar e sqljdbc4.jar file della libreria di classe da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE). Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il codice di esempio stabilisce una connessione per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. Quindi, viene utilizzata un'istruzione SQL con il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto, specifica il tipo di cursore sul lato server, quindi esegue l'istruzione SQL e inserisce i dati restituiti in un oggetto SQLServerResultSet.  
  
 Successivamente, il codice di esempio chiama il metodo di timerTest personalizzato, passando come argomenti la dimensione di recupero da utilizzare e il set di risultati. Il metodo timerTest quindi imposta la dimensione di recupero del gruppo di risultati utilizzando il metodo setFetchSize, imposta l'ora di inizio del test e quindi scorre il set di risultati con una `While` ciclo. Non appena il `While` si esce dal ciclo, il codice imposta l'ora di arresto del test, viene visualizzato il risultato del test con la dimensione di recupero, il numero di righe elaborate, e il tempo impiegato per eseguire il test.  
  
```java
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;  
  
public class cacheRS {  
  
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
  
         // Create and execute an SQL statement that returns a large  
         // set of data and then display it.  
         String SQL = "SELECT * FROM Sales.SalesOrderDetail;";  
         stmt = con.createStatement(SQLServerResultSet.TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, +  
               SQLServerResultSet.CONCUR_READ_ONLY);  
  
         // Perform a fetch for every row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(1, rs);  
         rs.close();  
  
         // Perform a fetch for every tenth row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(10, rs);  
         rs.close();  
  
         // Perform a fetch for every 100th row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(100, rs);  
         rs.close();  
  
         // Perform a fetch for every 1000th row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(1000, rs);  
         rs.close();  
  
         // Perform a fetch for every 128th row (the default) in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(0, rs);  
         rs.close();  
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
  
   private static void timerTest(int fetchSize, ResultSet rs) {  
      try {  
  
         // Declare the variables for tracking the row count and elapsed time.  
         int rowCount = 0;  
         long startTime = 0;  
         long stopTime = 0;  
         long runTime = 0;  
  
         // Set the fetch size then iterate through the result set to  
         // cache the data locally.  
         rs.setFetchSize(fetchSize);  
         startTime = System.currentTimeMillis();  
         while (rs.next()) {  
            rowCount++;  
         }  
         stopTime = System.currentTimeMillis();  
         runTime = stopTime - startTime;  
  
         // Display the results of the timer test.  
         System.out.println("FETCH SIZE: " + rs.getFetchSize());  
         System.out.println("ROWS PROCESSED: " + rowCount);  
         System.out.println("TIME TO EXECUTE: " + runTime);  
         System.out.println();  
  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei set di risultati](../../connect/jdbc/working-with-result-sets.md)  
  
  
