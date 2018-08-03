---
title: Esempio di URL di connessione | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 96fabc42-59d1-4cc0-93c5-db00cbe55e95
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31a3a492c9c6405e4d7f3c8d629adca38c2a3199
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278762"
---
# <a name="connection-url-sample"></a>Esempio di URL della connessione
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Con questa applicazione di esempio [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] viene illustrato come connettersi a un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tramite un URL di connessione. Viene inoltre illustrato come recuperare i dati da un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] usando un'istruzione SQL.  
  
 Il file di codice per questo esempio è ConnectURL.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*linguaggio*> \samples\connections  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario impostare il classpath in modo da includere il file con estensione jar mssql-jdbc. È anche necessario accedere al database di esempio di [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Per altre informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Con [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] sono inclusi file di libreria di classi mssql-jdbc da usare a seconda delle impostazioni Java Runtime Environment (JRE) preferite. Per altre informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il codice di esempio imposta le varie proprietà di connessione nell'URL della connessione, quindi esegue una chiamata al metodo getConnection della classe DriverManager per restituire un oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Il codice di esempio usa quindi il metodo [createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) dell'oggetto SQLServerConnection per creare un oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) e viene eseguita la chiamata al metodo [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) per l'esecuzione dell'istruzione SQL.  
  
 Infine, viene usato l'oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) restituito dal metodo executeQuery per scorrere i risultati restituiti dall'istruzione SQL.  
  
```java  
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class ConnectURL {
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT TOP 10 * FROM Person.Contact";
            ResultSet rs = stmt.executeQuery(SQL);

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println(rs.getString("FirstName") + " " + rs.getString("LastName"));
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione e recupero dei dati](../../../connect/jdbc/connecting-and-retrieving-data.md)
