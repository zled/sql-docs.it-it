---
title: ALTER-comando (TMSL) | Documenti Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8bdc49f1-209e-4055-be19-c83862b81efa
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 48567b03017e6ded0aba940b64ef1db52e7f78a1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-command-tmsl"></a>Comando ALTER (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Modifica di un oggetto esistente, ma non relativi elementi figlio, in un'istanza di Analysis Services in modalità tabulare.  Se l'oggetto non esiste, il comando genera un errore.  
  
 Utilizzare **Alter** comando per la destinazione degli aggiornamenti, come impostazione di una proprietà in una tabella senza dover specificare tutte le colonne nonché. Questo comando è simile a **CreateOrReplace**, ma senza la necessità di dover fornire una definizione completa dell'oggetto.  
  
 Per gli oggetti con le proprietà di lettura / scrittura, se si specifica una proprietà di lettura / scrittura, è necessario specificare tutti i loro, utilizzando il nuovo o i valori esistenti. Per ottenere un elenco di proprietà, è possibile utilizzare PowerShell per AMO. 
  
## <a name="request"></a>Richiesta  
 **ALTER** non avere alcun attributo. Includere l'oggetto da modificare, seguito dalla definizione oggetto modificato.  
  
 Nell'esempio seguente viene illustrata la sintassi per la modifica di una proprietà in un oggetto partition. Il percorso dell'oggetto stabilisce quale partizione è di oggetto da modificare tramite coppie nome-valore degli oggetti padre. Il secondo input è un oggetto di partizione che specifica il nuovo valore della proprietà.  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "\<database-name>",   
      "table": "\<table-name>",   
      "partition": "\<partition-name>"   
    },   
    "partition": {   
      "name": "\<new-partition-name>",   
       . . .  << other properties   
    }   
  }   
}   
```  
  
 La struttura della richiesta varia in base all'oggetto. **ALTER** può essere utilizzato con uno qualsiasi dei seguenti oggetti:  
  
 [Oggetto di database &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md) Rinominare un database.  
  
```  
"alter": {   
    "object": {   
      "database": "\<database-name>"  
    },   
    "database": {   
      "name": "\<new-database-name>",   
    }   
  }   
```  
  
 [Oggetto di origini dati &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) Rinominare una connessione, ovvero un oggetto figlio del database.  
  
```  
{   
   "alter":{   
      "object":{   
         "database":"AdventureWorksTabular1200",  
         "dataSource":"SqlServer localhost AdventureworksDW2016"  
      },  
      "dataSource":{   
         "name":"A new connection name"  
      }  
   }  
}  
```  
  
 [Oggetto tabelle &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) Vedere **esempio 1** sotto.  
  
 [Oggetto partizioni &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md) Vedere **esempio 2** sotto.  
  
 [Oggetto ruoli &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) Modificare una proprietà di un oggetto role.  
  
```  
{   
   "alter":{   
      "object":{   
         "database":"AdventureWorksTabular1200",  
         "role":"DataReader"  
      },  
      "role":{   
         "name":"New Name"  
      }  
   }  
}  
```  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione di XMLA.  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti illustrano script che è possibile eseguire in una finestra XMLA in Management Studio o utilizzare come input in [cmdlet Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md) in PowerShell per AMO.  
  
 **Esempio 1** -questo script imposta la proprietà name in una tabella.  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "AdventureWorksDW2016",   
      "table": "DimDate"  
    },   
    "table": {   
      "name": "DimDate2"  
    }   
  }   
}  
```  
  
 Supponendo che un'istanza denominata locale (nome dell'istanza è "tabulare") e un file JSON con lo script alter, questo comando viene modificato un nome di tabella da DimDate per DimDate2:  
  
 `invoke-ascmd -inputfile '\\my-computer\my-shared-folder\altertablename.json' -server 'localhost\Tabular'`  
  
 **Esempio 2** -questo script consente di rinominare una partizione, ad esempio alla fine dell'anno quando l'anno corrente diventa dell'anno precedente. Assicurarsi di specificare tutte le proprietà. Se si lascia **origine** non viene specificato, potrebbe interrompere tutte le definizioni di partizione esistente.  
  
 A meno che non si sta creando, sostituendo, o modificare l'oggetto di origine dati stessa, qualsiasi origine dati a cui fa riferimento nello script (ad esempio lo script di partizione seguente) deve essere un oggetto esistente **DataSource** oggetto nel modello. Se è necessario modificare l'origine dati, procedere come passaggio separato.  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "InternetSales",   
      "table": "DimDate",  
      "partition": "CurrentYear"  
    },   
    "partition": {   
      "name": "Year2009",  
       "source": {  
             "query":  "SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] WHERE [dbo].[DimDate].CalendarYear = 2009",  
              "dataSource": "SqlServer localhost AdventureworksDW2016"  
        }  
    }   
  }   
}  
```  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene utilizzato in un'istruzione del [metodo Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 Non è possibile generare uno script già pronto per questo comando da SSMS. In alternativa, è possibile iniziare con un esempio o scriverne uno proprio.  
  
 Il [ \[SSAS-MS-T\]: QL Server tabulare di Analysis Services (SQL Server tecniche Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON. Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento ([tabulare Model Scripting Language &#40; TMSL &#41; Fare riferimento a](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) per chiarimenti sui quali è supportata.  

## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

