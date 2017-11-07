---
title: Il comando MergePartitions (TMSL) | Documenti Microsoft
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
ms.assetid: dd568426-a415-41bf-b1e9-ea2261babf81
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 290e5e99219a37a1ff1f6793d640756ba21f7467
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mergepartitions-command-tmsl"></a>Comando MergePartitions (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Unisce i dati di uno o più partizioni di origine in una partizione di destinazione e quindi elimina la partizione di origine. La Query SQL della partizione di destinazione non verrà aggiornata come parte dell'unione. Per garantire che l'elaborazione successiva della partizione recupera tutti i dati, è necessario modificare la query in modo che vengono selezionati tutti i dati nella partizione unita.  
  
## <a name="request"></a>Richiesta  
 È necessario specificare il database, tabella e le partizioni di origine e di destinazione. È possibile unire solo le partizioni della stessa tabella.  
  
```  
{   
  "mergePartitions": {   
    "object": {   
      "database": "salesdatabase",   
      "table": "sales",   
      "partition": "may2015"   
    },   
    "sources": [   
      {   
        "database": "salesdatabase",   
        "table": "Sales",   
        "partition": "partition1"   
      },   
      {   
        "database": "salesdatabase",   
        "table": "Sales",   
        "partition": "partition2"   
      }   
    ]   
  }   
}  
  
```  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione di XMLA.  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene utilizzato in un'istruzione del [metodo Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 È possibile generare uno script già pronto per questo comando da SSMS.  Ad esempio, è possibile scegliere di **Script** nella finestra di dialogo Gestione partizioni.  
  
 Il [ \[SSAS-MS-T\]: QL Server tabulare di Analysis Services (SQL Server tecniche Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON. Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento [tabulare Model Scripting Language &#40; TMSL &#41; Riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) per chiarimenti sui quali è supportata  

## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Creare e gestire partizioni di modelli tabulari &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  

