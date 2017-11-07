---
title: Il comando (TMSL) Synchronize | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a32ff053-f38f-49d7-afdc-e19f59c88135
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2904954269f32dc80d603c3c0b045685d58bc2d5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="synchronize-command-tmsl"></a>Comando (TMSL) di sincronizzazione

[!INCLUDE[ssas-appliesto-sql2016-later](../../includes/ssas-appliesto-sql2016-later.md)]

  Sincronizza un database Analysis Services con un altro database esistente.  
  
## <a name="request"></a>Richiesta  
 Le proprietà accettate da JSON per il comando synchronize sono i seguenti.  
  
```  
{   
   "synchronize":{   
      "database":"AdventureWorksDW_Production",  
      "source":"Provider=MSOLAP.7;Data Source=localhost;Integrated Security=SSPI;Initial Catalog=AdventureWorksDW_Dev",  
      "synchronizeSecurity":"copyAll",  
      "applyCompression":true  
   }  
}  
```  
  
 Le proprietà accettate da JSON per il comando synchronize sono i seguenti.  
  
||||  
|-|-|-|  
|**Proprietà**|**Default**|**Description**|  
|database||Il nome dell'oggetto di database da sincronizzare.|  
|origine||La stringa di connessione da utilizzare per connettersi al server di origine.|  
|synchronizeSecurity|skipMembership|Valore di enumerazione che specifica la modalità di ripristino delle definizioni di sicurezza, inclusi i ruoli e autorizzazioni. I valori validi includono skipMembership, copyAll, ignoreSecurity.|  
|applyCompression|True|Valore booleano che, se è true, indica che verrà applicata la compressione durante l'operazione di sincronizzazione. in caso contrario false.|  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione di XMLA.  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene utilizzato in un'istruzione del [metodo Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 È possibile generare uno script già pronto per questo comando da SQL Server Management Studio fare clic sul pulsante di Script nella finestra di dialogo di sincronizzazione del Database.  
  
 Il [ \[SSAS-MS-T\]: QL Server tabulare di Analysis Services (SQL Server tecniche Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON. Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento [tabulare Model Scripting Language &#40; TMSL &#41; Riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) per chiarimenti sui quali è supportata  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

