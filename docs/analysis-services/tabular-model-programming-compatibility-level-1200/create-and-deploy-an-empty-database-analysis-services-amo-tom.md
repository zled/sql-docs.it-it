---
title: Creare e distribuire un database vuoto (Analysis Services AMO-TOM) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: afacae6ab8fc6f5a4f592e87758cca3142579c0a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="create-and-deploy-an-empty-database-analysis-services-amo-tom"></a>Creare e distribuire un database vuoto (Analysis Services AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Uno scenario di programmazione comune per gli oggetti AMO TOM consiste nel generare modelli in tempo reale e database. Questo articolo illustra i passaggi della creazione di un database. 

Per le soluzioni tabulari, è disponibile una corrispondenza tra un database e un modello, con un modello per ogni database. È possibile specificare in genere uno o l'altro e il motore dedurrà oggetto mancante. 

Creazione e distribuzione di un nuovo database è un'attività di tre parti: 

* Creare un'istanza di un **Database** dell'oggetto e impostarne le proprietà, incluso un nome. 

* Aggiungere il **Database** l'oggetto in un **Server.Databases** insieme. 

* Chiamare il **aggiornamento** metodo il **Database** salvarlo in un oggetto di **Server**. 

## <a name="code-example-create-empty-database"></a>Esempio di codice: creare un database vuoto 

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
                    server.Databases.GetNewName("New Empty Database"); 
 
                // 
                // Instantiate a new  
                // Microsoft.AnalysisServices.Tabular.Database object. 
                // 
                var blankDatabase = new Database() 
                { 
                    Name = newDatabaseName, 
                    ID = newDatabaseName, 
                    CompatibilityLevel = 1200, 
                    StorageEngineUsed = StorageEngineUsed.TabularMetadata, 
                }; 
                // 
                // Add the new database object to the server's  
                // Databases connection and submit the changes 
                // with full expansion to the server. 
                // 
                server.Databases.Add(blankDatabase); 
                blankDatabase.Update(UpdateOptions.ExpandFull); 

                Console.Write("Database "); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.Write(blankDatabase.Name); 
                Console.ResetColor(); 
                Console.WriteLine(" created successfully."); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="next-steps"></a>Passaggi successivi 

Dopo aver creato un database, è possibile aggiungere gli oggetti del modello: 

- [Aggiungere un'origine dati a un modello tabulare](../../analysis-services/tabular-model-programming-compatibility-level-1200/add-a-data-source-to-tabular-model-analysis-services-amo-tom.md)
- [Creare tabelle, le partizioni e le colonne in un modello tabulare](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-tables-partitions-and-columns-in-a-tabular-model.md)
 
