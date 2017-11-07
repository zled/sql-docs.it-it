---
title: Sequenza di comandi (TMSL) | Documenti Microsoft
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
ms.assetid: 898d6ec2-9b40-441b-be2b-5728d1d2882e
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e7fc7f1541131ac6a8e7249940a31104e50f0b09
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="sequence-command-tmsl"></a>Comando Sequence (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Utilizzare il **sequenza** comando per eseguire un set di operazioni consecutivo in modalità batch in un'istanza di Analysis Services.  L'intero comando e tutti i relativi componenti deve essere completata in ordine per la transazione abbia esito positivo.  
  
 È possibile eseguire i comandi seguenti in sequenza, ad eccezione di **aggiornamento** comando che viene eseguito in parallelo di elaborare più oggetti contemporaneamente.  
  
-   [Creazione di comandi &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)  
  
-   [Comando CreateOrReplace &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)  
  
-   [ALTER comando &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)  
  
-   [Eliminare comandi &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)  
  
-   [Aggiornare comando &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)  
  
-   [Comando di backup &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)  
  
-   [Ripristinare comandi &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)  
  
-   [Collegare comando &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)  
  
-   [Scollegare comandi &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)  
  
## <a name="request"></a>Richiesta  
 **maxParallelism** è una proprietà facoltativa che determina se **aggiornamento** operazioni eseguono in sequenza o in parallelo.  
  
 L'impostazione predefinita prevede di utilizzare il parallelismo del maggior numero possibile. Incorporando **aggiornamento** all'interno di **sequenza**, è possibile controllare il numero esatto di thread utilizzati durante l'elaborazione, tra cui limitare l'operazione per un solo thread.  
  
> [!NOTE]  
>  Il valore integer assegnato a **maxParallelism** determina il numero massimo di thread utilizzati durante l'elaborazione. I valori validi sono qualsiasi numero intero positivo. Impostazione del valore su 1 è uguale a non parallela (utilizza un thread).  
  
 Solo **aggiornamento** viene eseguito in parallelo. Se si modifica **maxParallelism** per utilizzare un numero fisso di thread, assicurarsi di esaminare le proprietà nella [aggiornare comando &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md) a comprendere l'impatto potenziale. È possibile impostare le proprietà in modo che minano parallelismo anche quando sono state apportate disponibili più thread. La sequenza di tipi di aggiornamento seguente genererà il grado di parallelismo migliore:  
  
-   Specificare innanzitutto l'aggiornamento per tutti gli oggetti utilizzando ClearValues  
  
-   Successivamente, specificare l'aggiornamento per tutti gli oggetti utilizzando DataOnly  
  
-   Specificano l'ultimo aggiornamento per tutti gli oggetti utilizzando Full, Calculate, automatico o Aggiungi  
  
 Qualsiasi variante di questa interromperà il parallelismo.  
  
```  
{   
  "sequence":    
    {   
      "maxParallelism": 3,   
      "operations": [   
        {   
          "mergepartitions": {   
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
        },   
        {   
          "refresh": {   
            "type": "calculate",   
            "object": {   
             "database": "salesdatabase"   
            }   
          }   
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
  
 Non è possibile generare uno script già pronto per questo comando da SSMS. In alternativa, è possibile iniziare con un esempio o scriverne uno proprio.  
  
 Il [ \[SSAS-MS-T\]: SQL Server Analysis Services tabulare (protocollo tecnici di SQL Server)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON . Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento ([tabulare Model Scripting Language &#40; TMSL &#41; Fare riferimento a](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) per chiarimenti sui quali è supportata.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

