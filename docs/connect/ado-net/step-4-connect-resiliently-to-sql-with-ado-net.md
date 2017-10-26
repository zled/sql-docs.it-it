---
title: 'Passaggio 4: Connettere in modo resiliente a SQL con ADO.NET | Documenti Microsoft'
ms.custom: 
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8985e162d0a1d72d2ca655be26b6c5c1a1607358
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Passaggio 4: Connettere in modo resiliente a SQL con ADO.NET

- Articolo precedente:&nbsp;&nbsp;&nbsp;[passaggio 3: modello di verifica la connessione a SQL mediante ADO.NET](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
In questo argomento fornisce un esempio di codice c# che illustra la logica di tentativi personalizzati. La logica di riesecuzione offre affidabilità. La logica di tentativi è progettata per elaborare correttamente gli errori temporanei o *errori temporanei* che tendono a risolversi se il programma diversi secondi e i tentativi.  
  
Origini di errori temporanei sono inclusi:  
  
- Un errore breve di una rete che supporta Internet.  
- Il sistema cloud potrebbe essere il bilanciamento del carico delle relative risorse al momento che si esegue una query inviato.  
  
  
Le classi ADO.NET per la connessione a Microsoft SQL Server locale possono inoltre connettersi al Database SQL Azure. Classi, tuttavia, autonomamente ADO.NET non è possibile fornire tutti solidità e affidabilità necessarie in uso in produzione. Il programma client può verificarsi errori temporanei da cui deve automaticamente e normalmente ripristinare e continuare il proprio.  
  
## <a name="step-1-identify-transient-errors"></a>Passaggio 1: Identificare gli errori temporanei  
  
Il programma deve distinguere tra gli errori temporanei e gli errori persistenti. Gli errori temporanei sono condizioni di errore che potrebbero cancellare entro un breve periodo di tempo, ad esempio problemi di rete temporanei.  Un esempio di un errore permanente sarebbe, se il programma presenta un errore di ortografia del nome del database di destinazione: in questo caso, l'errore "Database non trovato" sarebbe ancora valide e non dispone di alcuna possibilità di cancellazione dei entro un breve periodo di tempo.  
  
L'elenco di numeri di errore sono classificati come errori temporanei è disponibile nel [messaggi di errore per le applicazioni client di Database SQL](http://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>Passaggio 2: Creare ed eseguire l'applicazione di esempio  
  
In questo esempio si presuppone di .NET Framework 4.5.1 o versione successiva è installato.  L'esempio di codice c# è costituito da un file denominato Program.cs. Il codice viene fornito nella sezione successiva.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Passaggio 2: acquisizione e compilare l'esempio di codice  
  
È possibile compilare l'esempio con i passaggi seguenti:  
  
1. Nel [edizione gratuita di Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs), creare un nuovo progetto dal modello di applicazione Console c#.  
    - File > Nuovo > progetto > installato > Modelli > Visual c# > Windows > Desktop classico > applicazione Console  
    - Denominare il progetto **RetryAdo2**.  
2. Aprire il riquadro Esplora soluzioni.  
    - Visualizzare il nome del progetto.  
    - Visualizzare il nome del file Program.cs.  
3. Aprire il file Program.cs.  
4. Sostituire completamente il contenuto del file Program.cs con il codice nel blocco di codice seguente.  
5. Fare clic sul menu compilazione > Compila soluzione.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Passaggio 2: codice di esempio copia e Incolla  
  
Incollare questo codice nel **Program.cs** file.  
  
È quindi necessario modificare le stringhe per nome del server, password e così via. È possibile trovare queste stringhe nel metodo denominato **GetSqlConnectionStringBuilder**.  
  
Nota: La stringa di connessione per nome del server è destinata il Database SQL di Azure, perché include il prefisso di quattro caratteri del **tcp:**. Ma è possibile modificare la stringa di server per connettersi a Microsoft SQL Server.  
  
  
```CSharp  
    using System;  // C#  
    using CG = System.Collections.Generic;  
    using QC = System.Data.SqlClient;  
    using TD = System.Threading;  
        
    namespace RetryAdo2  
    {  
      public class Program  
      {  
        static public int Main(string[] args)  
        {  
          bool succeeded = false;  
          int totalNumberOfTimesToTry = 4;  
          int retryIntervalSeconds = 10;  
        
          for (int tries = 1;  
            tries <= totalNumberOfTimesToTry;  
            tries++)  
          {  
            try  
            {  
              if (tries > 1)  
              {  
                Console.WriteLine  
                  ("Transient error encountered. Will begin attempt number {0} of {1} max...",  
                  tries, totalNumberOfTimesToTry  
                  );  
                TD.Thread.Sleep(1000 * retryIntervalSeconds);  
                retryIntervalSeconds = Convert.ToInt32  
                  (retryIntervalSeconds * 1.5);  
              }  
              AccessDatabase();  
              succeeded = true;  
              break;  
            }  
        
            catch (QC.SqlException sqlExc)  
            {  
              if (TransientErrorNumbers.Contains  
                (sqlExc.Number) == true)  
              {  
                Console.WriteLine("{0}: transient occurred.", sqlExc.Number);  
                continue;  
              }  
              else  
              {  
                Console.WriteLine(sqlExc);  
                succeeded = false;  
                break;  
              }  
            }  
        
            catch (TestSqlException sqlExc)  
            {  
              if (TransientErrorNumbers.Contains  
                (sqlExc.Number) == true)  
              {  
                Console.WriteLine("{0}: transient occurred. (TESTING.)", sqlExc.Number);  
                continue;  
              }  
              else  
              {  
                Console.WriteLine(sqlExc);  
                succeeded = false;  
                break;  
              }  
            }  
        
            catch (Exception Exc)  
            {  
              Console.WriteLine(Exc);  
              succeeded = false;  
              break;  
            }  
          }  
        
          if (succeeded == true)  
          {  
            return 0;  
          }  
          else  
          {  
            Console.WriteLine("ERROR: Unable to access the database!");  
            return 1;  
          }  
        }  
        
        /// <summary>  
        /// Connects to the database, reads,  
        /// prints results to the console.  
        /// </summary>  
        static public void AccessDatabase()  
        {  
          //throw new TestSqlException(4060); //(7654321);  // Uncomment for testing.  
        
          using (var sqlConnection = new QC.SqlConnection  
              (GetSqlConnectionString()))  
          {  
            using (var dbCommand = sqlConnection.CreateCommand())  
            {  
              dbCommand.CommandText = @"  
    SELECT TOP 3  
        ob.name,  
        CAST(ob.object_id as nvarchar(32)) as [object_id]  
      FROM sys.objects as ob  
      WHERE ob.type='IT'  
      ORDER BY ob.name;";  
        
              sqlConnection.Open();  
              var dataReader = dbCommand.ExecuteReader();  
        
              while (dataReader.Read())  
              {  
                Console.WriteLine("{0}\t{1}",  
                  dataReader.GetString(0),  
                  dataReader.GetString(1));  
              }  
            }  
          }  
        }  
        
        /// <summary>  
        /// You must edit the four 'my' string values.  
        /// </summary>  
        /// <returns>An ADO.NET connection string.</returns>  
        static private string GetSqlConnectionString()  
        {  
          // Prepare the connection string to Azure SQL Database.  
          var sqlConnectionSB = new QC.SqlConnectionStringBuilder();  
        
          // Change these values to your values.  
          sqlConnectionSB.DataSource = "tcp:myazuresqldbserver.database.windows.net,1433"; //["Server"]  
          sqlConnectionSB.InitialCatalog = "MyDatabase"; //["Database"]  
        
          sqlConnectionSB.UserID = "MyLogin";  // "@yourservername"  as suffix sometimes.  
          sqlConnectionSB.Password = "MyPassword";  
          sqlConnectionSB.IntegratedSecurity = false;  
        
          // Adjust these values if you like. (ADO.NET 4.5.1 or later.)  
          sqlConnectionSB.ConnectRetryCount = 3;  
          sqlConnectionSB.ConnectRetryInterval = 10;  // Seconds.  
        
          // Leave these values as they are.  
          sqlConnectionSB.IntegratedSecurity = false;  
          sqlConnectionSB.Encrypt = true;  
          sqlConnectionSB.ConnectTimeout = 30;  
        
          return sqlConnectionSB.ToString();  
        }  
        
        static public CG.List<int> TransientErrorNumbers =  
          new CG.List<int> { 4060, 40197, 40501, 40613,  
          49918, 49919, 49920, 11001 };  
      }  
        
      /// <summary>  
      /// For testing retry logic, you can have method  
      /// AccessDatabase start by throwing a new  
      /// TestSqlException with a Number that does  
      /// or does not match a transient error number  
      /// present in TransientErrorNumbers.  
      /// </summary>  
      internal class TestSqlException : ApplicationException  
      {  
        internal TestSqlException(int testErrorNumber)  
        { this.Number = testErrorNumber; }  
        
        internal int Number  
        { get; set; }  
      }  
    }  
```  
  
###  <a name="step-2c-run-the-program"></a>Passaggio 2.c: eseguire il programma  
  
  
Il **RetryAdo2.exe** eseguibile senza parametri di input. Per eseguire il .exe:  
  
1. Aprire una finestra della console in cui è stato compilato il file binario RetryAdo2.exe.  
2. Eseguire RetryAdo2.exe, senza parametri di input.  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Passaggio 3: Modalità testare la logica dei tentativi  
  
Esistono diversi modi per simulare un errore temporaneo per testare la logica di ripetizione.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Passaggio 3.a: generare un'eccezione di test  
  
Include il codice di esempio:  
  
- Una classe secondo denominata **TestSqlException**, che una proprietà denominata **numero**.  
- `//throw new TestSqlException(4060);`, che è possibile rimuovere il commento.  
  
Se si rimuove il commento, l'istruzione throw e ricompilare, la successiva esecuzione di **RetryAdo2.exe** genera un messaggio simile al seguente.  
  
```  
    [C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
    >> RetryAdo2.exe  
    4060: transient occurred. (TESTING.)  
    Transient error encountered. Will begin attempt number 2 of 4 max...  
    4060: transient occurred. (TESTING.)  
    Transient error encountered. Will begin attempt number 3 of 4 max...  
    4060: transient occurred. (TESTING.)  
    Transient error encountered. Will begin attempt number 4 of 4 max...  
    4060: transient occurred. (TESTING.)  
    ERROR: Unable to access the database!  
      
    [C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
    >>  
```  
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Passaggio 3.b: testare nuovamente con un errore permanente  
  
Per dimostrare il codice gestisce gli errori persistenti correttamente, eseguire di nuovo il test precedente, ad eccezione di non utilizzano il numero di un errore temporaneo reale come 4060. Utilizzare invece il numero di serie 7654321. Il programma deve trattare come un errore permanente e deve ignorare eventuali tentativi.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Passaggio 3.c: disconnesso dalla rete  
  
1. Disconnettere il computer client dalla rete.  
    - Per un computer desktop, scollegare il cavo di rete.  
    - Per un computer portatile, premere la combinazione della funzione di chiavi per disattivare la scheda di rete.  
2. Avviare RetryAdo2.exe e attendere che la console per visualizzare il primo errore temporaneo, probabilmente 11001.  
3. Ristabilire la connessione alla rete, mentre RetryAdo2.exe ancora in esecuzione.  
4. Controllare l'esito positivo report della console in una ripetizione successivi.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Passaggio 2.d: temporaneamente in modo errato il nome del server  
  
1. Aggiungere temporaneamente 40615 come un altro numero di errore **TransientErrorNumbers**e ricompilare.  
2. Impostare un punto di interruzione sulla riga: `new QC.SqlConnectionStringBuilder()`.  
3. Utilizzare il *modifica e continuazione* intenzionalmente in modo errato il nome del server, due righe seguenti della funzionalità.  
    - Il programma in modo eseguire e tornare al punto di interruzione.  
    - Si verifica l'errore 40615.  
4. Correggere l'errore di ortografia.  
5. Consente di eseguire e completare correttamente il programma.  
6. Rimuovere 40615 e ricompilare.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
Per esplorare altri migliore practicies e linee guida di progettazione, visitare [connessione al Database SQL: i collegamenti, procedure consigliate e linee guida di progettazione](http://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  

