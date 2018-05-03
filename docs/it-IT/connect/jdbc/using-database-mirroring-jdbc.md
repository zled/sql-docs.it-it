---
title: Utilizzo del mirroring (JDBC) | Documenti Microsoft
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
ms.assetid: 4ff59218-0d3b-4274-b647-9839c4955865
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b5786ed1d52cb8150b148f7407f80564851462a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-database-mirroring-jdbc"></a>Utilizzo del mirroring del database (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il mirroring del database è principalmente una soluzione software per l'aumento della disponibilità del database e della ridondanza dei dati. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce supporto implicito per il mirroring del database, in modo che lo sviluppatore non debba scrivere alcun codice o eseguire altre attività quando è stato configurato per il database.  
  
 Mirroring del database, implementato in una base per ogni database, mantiene una copia di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database di produzione su un server di standby. Tale server può essere warm standby o hot standby, a seconda della configurazione e dello stato della sessione di mirroring del database. Un server standby hot supporta il failover rapido senza perdita delle transazioni approvate, mentre un server standby warm supporta la forzatura del servizio (con possibile perdita di dati).  
  
 Nome del database di produzione di *principale* database e la copia di standby viene chiamato il *mirror* database. Il database principale e mirror devono risiedere in istanze separate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] (istanze del server), e devono risiedere in computer separati, se possibile.  
  
 L'istanza del server di produzione, denominata server principale, comunica con l'istanza del server di standby, denominata server mirror. I server principale e mirror sono partner all'interno di una sessione di mirroring del database. Se il server principale non riesce, il server mirror può rendere il database nel database principale tramite un processo denominato *failover*. Partner_A e Partner_B, ad esempio, sono due server partner, con il database principale inizialmente su Partner_A come server principale e il database mirror che risiede in Partner_B come server mirror. Se Partner_A passa alla modalità offline, il database su Partner_B può eseguire il failover per diventare il database principale corrente. Quando Partner_A si unisce alla sessione di mirroring, diventa il server mirror e il database diventa il database mirror.  
  
 Nel caso in cui il server Partner_A è irrimediabilmente danneggiato, è possibile portare online un server Partner_C affinché funga da server mirror per Partner_B, che è ora il server principale. Tuttavia, in questo scenario l'applicazione client deve includere la logica di programmazione per assicurare che le proprietà della stringa di connessione siano aggiornate con i nuovi nomi server utilizzati nella configurazione di mirroring del database. In caso contrario, la connessione ai server non riesce.  
  
 Le configurazioni del mirroring del database alternative offrono livelli diversi di prestazioni e sicurezza dei dati e supportano forme diverse di failover. Per ulteriori informazioni, vedere "Panoramica del mirroring del Database" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="programming-considerations"></a>Considerazioni sulla programmazione  
 Quando si verifica un errore nel server di database principale, l'applicazione client riceve errori in risposta a chiamate API che indicano che la connessione al database è stata persa. Se ciò si verifica, le modifiche al database non salvate vanno perse e si verifica il rollback della transazione. Se ciò avviene, è necessario chiudere la connessione (o rilasciare l'oggetto origine dati) e tentare di riaprirla. La nuova connessione viene reindirizzata in maniera trasparente al database mirror, che funge ora da server principale, senza che il client debba modificare la stringa di connessione o l'oggetto origine dati.  
  
 Quando viene inizialmente stabilita una connessione, il server principale invia l'identità del partner di failover al client che verrà utilizzando quando si verifica il failover. Se un'applicazione tenta di stabilire una connessione iniziale con un server principale con errori, il client non riconosce l'identità del partner di failover. Per consentire ai client la possibilità di affrontare questo scenario, la proprietà di stringa di connessione failoverPartner e facoltativamente la [setFailoverPartner](../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) (metodo), dell'origine dati consente al client di specificare l'identità del failover partner autonomamente. La proprietà client viene utilizzata solo in questo scenario. Se il server principale è disponibile, non viene utilizzata.  
  
> [!NOTE]  
>  Se la proprietà failoverPartner viene specificata nella stringa di connessione o nell'oggetto origine dati, è necessario impostare anche la proprietà databaseName. In caso contrario, verrà generata un'eccezione. Se le proprietà failoverPartner e databaseName non sono specificate in modo esplicito, l'applicazione non tenterà di eseguire il failover in caso di errore del server di database principale. In altri termini, il reindirizzamento trasparente funziona solo per connessioni che specificano in modo esplicito le proprietà failoverPartner e databaseName. Per ulteriori informazioni su failoverPartner e su altre proprietà della stringa di connessione, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Se il server del partner di failover fornito dal client non fa riferimento a un server che funge da partner di failover per il database specificato e se il server o il database a cui viene fatto riferimento si trova in una disposizione di mirroring, la connessione viene rifiutata dal server. Sebbene il [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) classe fornisce il [getFailoverPartner](../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md) (metodo), questo metodo restituisce solo il nome del partner di failover specificato nella stringa di connessione o metodo setFailoverPartner. Per recuperare il nome del partner di failover effettivo che è attualmente in uso, utilizzare la seguente [!INCLUDE[tsql](../../includes/tsql_md.md)] istruzione:  
  
```  
SELECT m.mirroring_role_DESC, m.mirroring_state_DESC,  
m.mirroring_partner_instance FROM sys.databases as db,  
sys.database_mirroring AS m WHERE db.name = 'MirroringDBName'  
AND db.database_id = m.database_id  
```  
  
> [!NOTE]  
>  Per utilizzare il nome del database di mirroring, è necessario modificare questa istruzione.  
  
 Si consiglia di memorizzare nella cache le informazioni sul partner per aggiornare la stringa di connessione oppure progettare una strategia di riesecuzione dei tentativi nel caso in cui si verifichi un errore nel primo tentativo di connessione.  
  
## <a name="example"></a>Esempio  
 Nel seguente esempio, viene eseguito un primo tentativo di connessione al server principale. Se il tentativo non riesce e viene generata un'eccezione, viene eseguito un tentativo di connessione al server mirror, che potrebbe essere stato promosso a nuovo server principale. Notare l'utilizzo della proprietà failoverPartner nella stringa di connessione.  
  
```  
import java.sql.*;  
  
public class clientFailover {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://serverA:1433;" +  
         "databaseName=AdventureWorks;integratedSecurity=true;" +  
         "failoverPartner=serverB";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
  
      try {  
         // Establish the connection to the principal server.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
         System.out.println("Connected to the principal server.");  
  
         // Note that if a failover of serverA occurs here, then an  
         // exception will be thrown and the failover partner will  
         // be used in the first catch block below.  
  
         // Create and execute an SQL statement that inserts some data.  
         stmt = con.createStatement();  
  
         // Note that the following statement assumes that the   
         // TestTable table has been created in the AdventureWorks  
         // sample database.  
         stmt.executeUpdate("INSERT INTO TestTable (Col2, Col3) VALUES ('a', 10)");  
      }  
  
      // Handle any errors that may have occurred.  
      catch (SQLException se) {  
         try {  
            // The connection to the principal server failed,  
            // try the mirror server which may now be the new  
            // principal server.  
            System.out.println("Connection to principal server failed, " +  
            "trying the mirror server.");  
            con = DriverManager.getConnection(connectionUrl);  
            System.out.println("Connected to the new principal server.");  
            stmt = con.createStatement();  
            stmt.executeUpdate("INSERT INTO TestTable (Col2, Col3) VALUES ('a', 10)");  
         }  
         catch (Exception e) {  
            e.printStackTrace();  
         }  
      }  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      // Close the JDBC objects.  
      finally {  
         if (stmt != null) try { stmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
