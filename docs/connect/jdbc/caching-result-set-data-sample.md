---
title: Risultato di memorizzazione nella cache Set di dati di esempio | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 13a95ebb-996c-4713-a1bd-5834fe22a334
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a0c7f60de8680229fdc3fc3ed3a95c26ad5ef5f
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278572"
---
# <a name="caching-result-set-data-sample"></a>Esempio di memorizzazione nella cache dei dati dei set di risultati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questa applicazione di esempio [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] illustra come recuperare un set di dati di grandi dimensioni da un database e quindi come controllare il numero di righe di dati memorizzate nella cache del client usando il metodo [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) dell'oggetto [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  La limitazione del numero di righe inserite nella cache del client è un'operazione diversa dalla limitazione del numero totale di righe contenute in un set di risultati. Per controllare il numero totale di righe all'interno di un set di risultati, usare il metodo [setMaxRows](../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) dell'oggetto [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), ereditato da entrambi gli oggetti [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
 Per impostare un limite per il numero di righe memorizzate nella cache del client, è prima necessario usare un cursore lato server quando si crea uno degli oggetti Statement specificando esplicitamente il tipo di cursore da usare durante la creazione dell'oggetto Statement. Ad esempio, il driver JDBC mette a disposizione il tipo di cursore TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, un cursore lato server di sola lettura, fast forward-only, da usare con i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!NOTE]  
>  Un'alternativa all'utilizzo del tipo di cursore specifico per SQL Server è l'utilizzo della proprietà della stringa di connessione selectMethod, impostandone il valore su "cursor". Per altre informazioni sui tipi di cursore supportati dal driver JDBC, vedere [informazioni sui tipi di cursore](../../connect/jdbc/understanding-cursor-types.md).  
  
 Dopo che è stata eseguita la query contenuta nell'oggetto Statement e dopo che al client sono stati restituiti i dati come set di risultati, è possibile chiamare il metodo setFetchSize per controllare la quantità dei dati recuperati contemporaneamente dal database. Ad esempio, se si dispone di una tabella che contiene 100 righe di dati e si imposta su 10 la dimensione del recupero, verranno inserite nella cache del client solo 10 righe di dati in qualsiasi momento. In questo modo verrà ridotta la velocità di elaborazione dei dati, ma si otterrà il vantaggio di utilizzare una quantità inferiore di memoria nel client, il che può risultare particolarmente utile quando si elaborano grandi quantità di dati.  
  
 Il file di codice per questo esempio, CacheRS.java, è disponibile nel percorso seguente:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*linguaggio*> \samples\resultsets  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio è necessario impostare il classpath in modo da includere il file con estensione jar mssql-jdbc. Sarà inoltre necessario accedere al database di esempio di [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Per altre informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Con [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sono inclusi file di libreria di classi mssql-jdbc da usare a seconda delle impostazioni Java Runtime Environment (JRE) preferite. Per altre informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, mediante il codice di esempio viene eseguita una connessione al database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] di esempio. Viene quindi usata un'istruzione SQL con l'oggetto [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), viene specificato il tipo di cursore lato server e quindi viene eseguita l'istruzione SQL e i dati restituiti vengono inseriti in un oggetto SQLServerResultSet.  
  
 Il codice di esempio esegue quindi una chiamata al metodo timerTest personalizzato, passando come argomenti la dimensione di recupero da usare e il set di risultati. Il metodo timerTest imposta quindi la dimensione di recupero del set di risultati tramite il metodo setFetchSize, imposta l'ora di inizio del test e quindi scorre il set di risultati con un ciclo `While`. Non appena terminato il ciclo `While`, viene impostata l'ora di fine del test e quindi viene visualizzato il risultato del test stesso con le dimensioni di recupero, il numero di righe elaborate e il tempo impiegato per l'esecuzione.  
  
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

public class CacheRS {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(SQLServerResultSet.TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, SQLServerResultSet.CONCUR_READ_ONLY);) {

            String SQL = "SELECT * FROM Sales.SalesOrderDetail;";

            // Perform a fetch for every row in the result set.
            ResultSet rs = stmt.executeQuery(SQL);
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
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void timerTest(int fetchSize,
            ResultSet rs) throws SQLException {

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
    }
}
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei set di risultati](../../connect/jdbc/working-with-result-sets.md)  
  
  
