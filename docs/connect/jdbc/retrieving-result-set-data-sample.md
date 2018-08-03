---
title: Recupero dei risultati Set di dati di esempio | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1b190c36-3d38-49a2-8599-612329675851
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8fe0d97c8a8ec0f29e8a6b85542ea0627a5c6fb
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279142"
---
# <a name="retrieving-result-set-data-sample"></a>Esempio di recupero dei dati del set di risultati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Con questa applicazione [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] di esempio viene illustrato come recuperare un set di dati da un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e quindi visualizzare i dati.  
  
 Il file di codice per questo esempio è denominato retrieveRS.java e si trova nella seguente posizione:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*linguaggio*> \samples\resultsets  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario impostare il classpath in modo da includere il file con estensione jar mssql-jdbc. È anche necessario accedere al database di esempio di [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Per altre informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Con [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sono inclusi file di libreria di classi mssql-jdbc da usare a seconda delle impostazioni Java Runtime Environment (JRE) preferite. Per altre informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, mediante il codice di esempio viene eseguita una connessione al database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] di esempio. Quindi, utilizzando un'istruzione SQL con l'oggetto [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), viene eseguita l'istruzione SQL e i dati restituiti vengono posizionati in un oggetto [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 Successivamente il codice di esempio chiama il metodo personalizzato displayRow per ripetere le righe di dati incluse nel set di risultati e usa il metodo [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) per visualizzare alcuni di questi dati.  
  
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class RetrieveRS {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT * FROM Production.Product;";
            ResultSet rs = stmt.executeQuery(SQL);
            displayRow("PRODUCTS", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        while (rs.next()) {
            System.out.println(rs.getString("ProductNumber") + " : " + rs.getString("Name"));
        }
    }
}
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei set di risultati](../../connect/jdbc/working-with-result-sets.md)  
  
  
