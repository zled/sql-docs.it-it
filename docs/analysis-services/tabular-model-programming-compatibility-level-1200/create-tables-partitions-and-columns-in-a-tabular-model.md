---
title: Creare tabelle, le partizioni e le colonne in un modello tabulare | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cf0e4791-ad3b-41a8-81ce-509d4cf223f8
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3246c04b8aa995442a71ddc49a2282945c829fa6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="create-tables-partitions-and-columns-in-a-tabular-model"></a>Creare tabelle, le partizioni e le colonne in un modello tabulare
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In un modello tabulare, una tabella è costituita da righe e colonne. Le righe sono organizzate in partizioni per supportare l'aggiornamento dei dati incrementali. Una soluzione tabulare può supportare diversi tipi di tabelle, a seconda di dove i dati provenienti da:  

* Tabelle normali, in cui i dati provengano da un'origine dati relazionale, tramite il provider di dati. 

* Push di tabelle, in cui dati sono "push" per la tabella a livello di codice. 

* Tabelle calcolate, in cui i dati provengono da un'espressione DAX che fa riferimento a un altro oggetto all'interno del modello per i propri dati.  

Nell'esempio di codice riportato di seguito è sarà possibile definire una normale tabella. 

## <a name="required-elements"></a>Elementi necessari 

Una tabella deve includere almeno una partizione. Una normale tabella deve inoltre avere almeno una colonna definita. 

Ogni partizione deve avere un'origine specifica l'origine dei dati, ma l'origine può essere impostata su null. In genere, l'origine è un'espressione di query che definisce una sezione di dati nel linguaggio di query database pertinente. 

## <a name="code-example-create-a-table-column-parition"></a>Esempio di codice: creare una tabella, colonna, partizione

Le tabelle sono rappresentate dalla classe di tabella (nello spazio dei nomi Microsoft.AnalysisServices.Tabular). 

Nell'esempio seguente, è sarà possibile definire una normale tabella con una partizione collegata a un'origine dati relazionale e alcune colonne regolare. Verrà inoltre inviare le modifiche al server e attivare un aggiornamento di dati che visualizza i dati nel modello. Rappresenta lo scenario più comune quando si desidera caricare i dati da un database relazionale di SQL Server in una soluzione tabulare. 


```
using System; 
using Microsoft.AnalysisServices; 
using Microsoft.AnalysisServices.Tabular; 
 
namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 
 
            // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 
 
                // 
                // Generate a new database name and use GetNewName 
                // to ensure the database name is unique. 
                // 
                string newDatabaseName = 
                    server.Databases.GetNewName("Database with a Table Definition"); 
 
                // 
                // Instantiate a new  
                // Microsoft.AnalysisServices.Tabular.Database object. 
                // 
                var dbWithTable = new Database() 
                { 
                    Name = newDatabaseName, 
                    ID = newDatabaseName, 
                    CompatibilityLevel = 1200, 
                    StorageEngineUsed = StorageEngineUsed.TabularMetadata, 
                }; 
 
                // 
                // Add a Microsoft.AnalysisServices.Tabular.Model object to the 
                // database, which acts as a root for all other Tabular metadata objects. 
                // 
                dbWithTable.Model = new Model() 
                { 
                    Name = "Tabular Data Model", 
                    Description = "A Tabular data model at the 1200 compatibility level." 
                }; 
 
                // 
                // Add a Microsoft.AnalysisServices.Tabular.ProviderDataSource object 
                // to the data Model object created in the previous step. The connection 
                // string of the data source object in this example  
                // points to an instance of the AdventureWorks2014 SQL Server database. 
                // 
                string dataSourceName = "SQL Server Data Source Example"; 
                dbWithTable.Model.DataSources.Add(new ProviderDataSource() 
                { 
                    Name = dataSourceName, 
                    Description = "A data source definition that uses explicit Windows credentials for authentication against SQL Server.", 
                    ConnectionString = "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureWorks2014;Integrated Security=SSPI;Persist Security Info=false", 
                    ImpersonationMode = Microsoft.AnalysisServices.Tabular.ImpersonationMode.ImpersonateAccount, 
                    Account = @".\Administrator", 
                    Password = "P@ssw0rd", 
                }); 
 
                //  
                // Add a table called Individual Customers to the data model 
                // with a partition that points to a [Sales].[vIndividualCustomer] view 
                // in the underlying data source. 
                // 
                dbWithTable.Model.Tables.Add(new Table() 
                { 
                    Name = dbWithTable.Model.Tables.GetNewName("Individual Customers"), 
                    Description = "Individual customers (names and email addresses) that purchase Adventure Works Cycles products online.", 
                    Partitions = { 
                        // 
                        // Create a single partition with a QueryPartitionSource for a query 
                        // that imports all customer rows from the underlying data source. 
                        // 
                        new Partition() { 
                            Name = "All Customers", 
                            Source = new QueryPartitionSource() { 
                                DataSource = dbWithTable.Model.DataSources[dataSourceName], 
                                Query = @"SELECT   [FirstName] 
                                                    ,[MiddleName] 
                                                    ,[LastName] 
                                                    ,[PhoneNumber]  
                                                    ,[EmailAddress] 
                                                    ,[City] 
                                        FROM [Sales].[vIndividualCustomer]", 
                            } 
                        } 
                    }, 
                    Columns = 
                    { 
                        // 
                       // DataColumn objects refer to regular table columns.  
                        // Each DataColumn object corresponds to a column in the underlying data source query. 
                        // 
                        new DataColumn() { 
                            Name = "FirstName", 
                            DataType = DataType.String, 
                            SourceColumn = "FirstName", 
                        }, 
                        new DataColumn() { 
                            Name = "MiddleName", 
                            DataType = DataType.String, 
                            SourceColumn = "MiddleName", 
                        }, 
                        new DataColumn() { 
                            Name = "LastName", 
                            DataType = DataType.String, 
                            SourceColumn = "LastName", 
                        }, 
                        new DataColumn() { 
                            Name = "PhoneNumber", 
                            DataType = DataType.String, 
                            SourceColumn = "PhoneNumber", 
                        }, 
                        new DataColumn() { 
                            Name = "EmailAddress", 
                            DataType = DataType.String, 
                            SourceColumn = "EmailAddress", 
                        }, 
                        new DataColumn() { 
                            Name = "City", 
                            DataType = DataType.String, 
                            SourceColumn = "City", 
                        }, 
                    } 
                }); 
 
                // 
                // Add the new database object to the server's  
                // Databases connection and submit the changes 
                // with full expansion to the server. 
                // 
                server.Databases.Add(dbWithTable); 
 
                //  
                // Request a full refresh to import the data from the data source and 
                // and perform any necessary recalculations. 
                // The refresh operation will be performed with the next 
                // invocation of Model.SaveChanges() or Database.Update(UpdateOptions.ExpandFull). 
                dbWithTable.Model.RequestRefresh(Microsoft.AnalysisServices.Tabular.RefreshType.Full); 
                dbWithTable.Update(UpdateOptions.ExpandFull); 
 
 
                Console.Write("Database "); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.Write(dbWithTable.Name); 
                Console.ResetColor(); 
                Console.WriteLine(" created successfully."); 
 
                Console.WriteLine("The data model includes the following table definitions:"); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                foreach (Table tbl in dbWithTable.Model.Tables) 
                { 
                    Console.WriteLine("\tTable name:\t\t{0}", tbl.Name); 
                    Console.WriteLine("\ttbl description:\t{0}", tbl.Description); 
                } 
                Console.ResetColor(); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="partitions-in-a-table"></a>Partizioni in una tabella 

Le partizioni sono rappresentate da un **partizione** classe (Microsoft.AnalysisServices.Tabular spazio dei nomi). Il **partizione** classe espone un **origine** proprietà di P**artitionSource** tipo, che fornisce un'astrazione su diversi approcci per l'inserimento di dati in partizione. Oggetto **partizione** istanza può avere un **origine** proprietà come null, che indica dati verranno inseriti nella partizione mediante l'invio di blocchi di dati al Server come parte di push di dati API esposta da Analysis Services . In SQL Server 2016, **PartitionSource** classe dispone di due classi derivate che rappresentano i modi per associare dati a una partizione: **QueryPartitionSource** e **CalculatedPartitionSource**. 

## <a name="columns-in-a-table"></a>Colonne in una tabella 

Le colonne sono rappresentate da diverse classi derivate da base **colonna** classe (Microsoft.AnalysisServices.Tabular spazio dei nomi): 

* **DataColumn** (per le normali colonne nelle tabelle normali)
* **CalculatedColumn** (per le colonne supportate da espressione DAX)
* **CalculatedTableColumn** (per le normali colonne in tabelle calcolate)
* **RowNumberColumn** (tipo speciale di colonna creata da SSAS per ogni tabella). 

## <a name="row-numbers-in-a-table"></a>Numeri di riga in una tabella 

Ogni **tabella** oggetto in un server ha un **RowNumberColumn** usato ai fini dell'indicizzazione. È possibile creare o aggiungerlo in modo esplicito. La colonna viene creata automaticamente quando si salva o aggiornare l'oggetto: 

* **DB. SaveChanges** 

* **DB. Update(ExpandFull)** 

Quando si chiama dei metodi, il server creerà colonna dei numeri di riga automaticamente, che sarà visibile come **RowNumberColumn** Raccolta colonne della tabella. 

## <a name="calculated-tables"></a>Tabelle calcolate 

Le tabelle calcolate vengono originate da un'espressione DAX che repurposes dati da strutture di dati esistenti nel modello o da associazioni out-of-line. Per creare una tabella calcolata a livello di codice, eseguire le operazioni seguenti: 

* Creare un oggetto generico **tabella**. 

* Aggiungere una partizione con origine di tipo **CalculatedPartitionSource**, in cui l'origine è un'espressione DAX. L'origine della partizione è ciò che distingue una normale tabella da una tabella calcolata. 

Quando si salvano le modifiche al server, il server restituirà l'elenco di derivato **CalculatedTableColumns** (calcolato tabelle sono costituite da colonne di tabella calcolata), visibili tramite l'insieme di colonne della tabella. 

## <a name="next-steps"></a>Passaggi successivi

Esaminare le classi utilizzate per la gestione delle eccezioni in TOM: [gestione degli errori in TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/handling-errors-in-the-tom-api-analysis-services-amo-tom.md)
  
