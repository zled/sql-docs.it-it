---
title: Elenco dei database esistenti in un server tabulare (Analysis Services AMO-TOM) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db8ab4fac3f86c40f78ede78b365707745e79fe7
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="list-existing-databases-on-a-tabular-server-analysis-services-amo-tom"></a>Elenco dei database esistenti in un server tabulare (Analysis Services AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Quando si dispone di un **Server** oggetto che è connesso a un'istanza di Analysis Services, è possibile scorrere **Server.Databases** insieme per elencare tutti i database ospitati dall'istanza di servizi di analisi. 

Il **Server.Databases** raccolta contiene un **Database** oggetto per ogni database ospitato nel server, indipendentemente dalla modalità del server (multidimensionale o tabulare) o il tipo di database (multidimensionale, Pre-modello tabulare 1200 o tabulare 1200 e versioni successive). 

È possibile controllare il tipo di database tramite **Database.StorageEngineUsed** proprietà.  

I database tabulari 1200 e superiore verranno restituito un valore non null **Database.Model** proprietà che fornisce accesso a tutti gli oggetti di metadati tabulari: tabelle, colonne, relazioni e così via.  

Per multidimensionale o tabulare 1103 e nelle versioni precedenti di Database.Model proprietà sarà null. In questo caso, i metadati non tabulari saranno disponibili nella proprietà multidimensionali (ad esempio Database.Cubes e Database.Dimensions), ma tali proprietà sono visibili solo dalla classe Microsoft.AnalysisServices.Database (da AMO), non da Microsoft.AnalysisServices.Tabular.Database (per TOM). Per ulteriori informazioni sulle classi di Database da utilizzare, vedere [installare, distribuire e fare riferimento alla libreria client di TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md).

A meno che non Database.StorageEngineUsed è impostata su TabularMetadata, non sarà in grado di utilizzare altre classi nello spazio dei nomi tabulare per accedere o modificare l'albero del modello. 

Nella tabella seguente sono riepilogati i comportamenti previsti quando ci si connette a un server o di un database utilizzando una classe Microsoft.AnalysisServices.Tabular in un server o database. 

mode | Database.Model | Database.StorageEngineUsed
-----|----------------|---------------------------
Tabulari 1200, 1400 | Restituisce il nome del modello| StorageEngineUsed.TabularMetadata 
Tabulare 1103, 1050, 1100 | Restituisce null | StorageEngineUsed.InMemory 
Multidimensionale | Restituisce null | StorageEngineUsed.Traditional 

## <a name="code-example-list-existing-databases"></a>Esempio di codice: elenco dei database esistenti

Il codice riportato di seguito viene illustrato come connettersi ai server database e di elenco ospitati dal server. 

```
using System; using Microsoft.AnalysisServices; 
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
                // List common properties for the databases on the server. 
                // 
                foreach (Database db in server.Databases) 
                { 
                    Console.WriteLine("Properties for database {0}:", db.Name); 
                    Console.ForegroundColor = ConsoleColor.Yellow; 
                    Console.WriteLine("Database ID:\t\t\t{0}", db.ID); 
                    Console.WriteLine("Database compatibility level:\t{0}", db.CompatibilityLevel); 
                    Console.WriteLine("Database collation:\t\t{0}", db.Collation); 
                    Console.WriteLine("Database created timestamp:\t{0}", db.CreatedTimestamp); 
                    Console.WriteLine("Database language ID:\t\t{0}", db.Language); 
                    Console.WriteLine("Database model type:\t\t{0}", db.ModelType); 
                    Console.WriteLine("Database state:\t\t\t{0}", db.State); 
                    Console.ResetColor(); 
                    Console.WriteLine(); 
                } 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```


## <a name="get-an-item-from-a-database"></a>Ottenere un elemento da un database 

Frammento di codice seguente viene illustrato come ottenere una tabella o una colonna da un database. 


```
var db = srv.Databases.GetByName("abc"); 

Column c1 = db.Model.Tables["foo"].Columns["bar"]; 
if (c1.ObjectType == ObjectType.Column) // always true 

MetadataObject obj; 

switch(obj.ObjectType) 
{ 
 case ObjectType.Table: 
  var t1 = (Table)obj; 
  break; 
} 
```

## <a name="next-steps"></a>Passaggi successivi

Comprendere come [creare e distribuire un database vuoto](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md) tramite l'API di TOM.

