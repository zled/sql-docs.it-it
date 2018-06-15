---
title: Aggiornamento di comando (TMSL) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db07b1a5b4dc98b516e2f15e29aced3c74a57a16
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34043695"
---
# <a name="refresh-command-tmsl"></a>Aggiornamento di comando (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Elabora oggetti nel database corrente.   
**Aggiornare** viene sempre eseguito in parallelo a meno che non si limita a [sequenza comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md).  
  
 È possibile eseguire l'override di alcune proprietà di alcuni oggetti durante un'operazione di aggiornamento dati:  
  
-   Modifica il **QueryDefinition** proprietà di un **partizione** per importare dati utilizzando un'espressione di filtro in tempo reale.  
  
-   Fornire le credenziali dell'origine dati come parte di un **aggiornamento** comando, il **ConnectionString** proprietà di un **DataSource** oggetto. Questo approccio può essere considerato più sicuro, come le credenziali vengono fornite e utilizzate temporaneamente per la durata dell'operazione, anziché archiviato.  
  
 Vedere gli esempi in questo argomento per un'illustrazione di questi override di proprietà.  
  
> [!NOTE]  
>  A differenza di elaborazione multidimensionale, non è presente alcuna gestione speciale di elaborazione degli errori per l'elaborazione tabulare.  

  
## <a name="request"></a>Richiesta  
 **Aggiorna** accetta una definizione di parametro e oggetto tipo.  
  
```  
    {  
        "refresh": {  
            "description": "Parameters of Refresh command of Analysis Services JSON API",  
            "properties": {  
            "type": {  
                "enum": [  
                "full",  
                "clearValues",  
                "calculate",  
                "dataOnly",  
                "automatic",  
                "add",  
                "defragment"  
                ]  
            },  
            "objects": {  
. . .   
```  
  
 Il **tipo** parametro consente di impostare un ambito dell'operazione di elaborazione.  
  
||||  
|-|-|-|  
|**Tipo di aggiornamento**|**Si applica a**|**Description**|  
|completi|Database,<br />tavolo<br />Partition|Per tutte le partizioni della partizione, della tabella o del database specificati, aggiornare i dati e ricalcolare tutti i dipendenti. Per una partizione di calcolo, ricalcolare la partizione e tutti i relativi dipendenti.|  
|clearValues|Database,<br />tavolo<br />Partition|Cancellare i valori in questo oggetto e tutti i relativi dipendenti.|  
|calcolare|Database,<br />tavolo<br />Partition|Ricalcolare questo oggetto e tutti i relativi dipendenti, ma solo se necessario. Questo valore non forza il ricalcolo, se non per le formule volatili.|  
|dataOnly|Database,<br />tavolo<br />Partition|Aggiornare i dati in questo oggetto e cancellare tutti i dipendenti.|  
|automatic|Database,<br />tavolo<br />Partition|Se l'oggetto deve essere aggiornato e ricalcolato, eseguire l'operazione richiesta sia per l'oggetto che per tutti i dipendenti. Si applica se la partizione è in uno stato diverso da pronta.|  
|add|Partition|Aggiungere i dati alla partizione e ricalcolare tutti i dipendenti. Questo comando è valido solo per le partizioni regolari e non per le partizioni di calcolo.|  
|deframmentare|Database,<br />Tabella|Deframmentare i dati nella tabella specificata. Man mano che vengono aggiunti o rimossi dati in una tabella, i dizionari di ogni colonna possono risultare contaminati da valori che non esistono più tra i valori di colonna effettivi. L'opzione defragment consentirà di pulire i valori non più usati nei dizionari.|  
  
 È possibile aggiornare gli oggetti seguenti:  
  
 [Oggetto di database &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md) elaborare un database.  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200"  
      }  
    ]  
  }  
}  
```  
  
 [Oggetto tabelle &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) elaborare una singola tabella.  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "Date"  
      }  
    ]  
  }  
}  
```  
  
 [Oggetto di partizioni &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md) elaborare una singola partizione all'interno di una tabella.  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "FactSalesQuota",  
        "partition": "FactSalesQuota"  
      },  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "FactSalesQuota",  
        "partition": "FactSalesQuota - 2011"  
      }  
    ]  
  }  
}  
```  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione di XMLA.  
  
## <a name="examples"></a>Esempi  
 Eseguire l'override di entrambi i **ConnectionString** ed eseguire query di definizione di una partizione.  
  
```  
{   
    "refresh": {   
        "type": "data",   
        "objects": [   
            {   
                "database": "tmtestdb",   
                "table": "sales"   
            },   
            {   
                "database": "tmtestdb",   
                "table": "customer"   
            }   
        ],   
        "overrides": [   
            {   
                "dataSources": [ // Bindings for Data Sources   
                    {   
                        "object": {   
                            "database": "tmtestdb",   
                            "dataSource": "contoso"   
                        },   
                        "dataSource": {   
                        "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=contoso;Integrated Security=SSPI;Persist Security Info=false"   
"   
                        }   
                    }   
                ],   
                "partitions": [ // Bindings for Partitions   
                    {   
                        "object": {   
                            "database": "tmtestdb",   
                            "table": "sales",   
                            "partition": "2015"   
                        },   
                        "partition": {   
                            "source": {   
                                "query": [  
                                     "SELECT sales.salesamount, customer.customername FROM sales",  
                                     "JOIN customer on custKey = sales.custkey",  
                                     "JOIN date on date.DateKey = customer.OrderDate",  
                                     "WHERE date.CalendarYear='2015'"  
                                  ],  
                            }   
                        }   
                    }   
                ]   
            }   
        ]   
    }   
}   
```  
  
 Esegue l'override di ambito specifico impostando il parametro di tipo un **dataOnly** metadati di aggiornamento, rimangono intatto.  
  
```  
{   
        "refresh" : {   
            "type" : "dataOnly",   
            "objects" : [   
                {   
                    "database" : "TMTestDB",   
                    "table" : "Customer"   
                },   
                {   
                    "database" : "TMTestDB",   
                    "table" : "Sales"   
                }   
            ],   
            "overrides" : [{   
                "scope" : {   
                    "database" : "TMTestDB",   
                    "table" : "Sales"   
                },   
                "dataSources" : [{   
                    "originalObject" : {   
                        "dataSource" : "SqlServer sqlcldb2 AS_foodmart_2000"   
                    },   
                    "connectionString" : "Provider=SQLNCLI11;Data Source=sqlcldb2;Initial Catalog=AS_foodmart_2000;Integrated Security=SSPI;Persist Security Info=false"   
                }]   
            }]   
        }   
    }   
```  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene utilizzato in un'istruzione del [metodo Execute &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 È possibile generare uno script già pronto per questo comando da SSMS.  Ad esempio, è possibile scegliere di **Script** in una finestra di dialogo di elaborazione.  
  
 Il [ \[SSAS-MS-T\]: QL Server tabulare di Analysis Services (SQL Server tecniche Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON. Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento ([linguaggio di Scripting del modello tabulare &#40;TMSL&#41; riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) per chiarimenti sui quali è supportata.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Opzioni di elaborazione e le impostazioni di &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)  
  
  
