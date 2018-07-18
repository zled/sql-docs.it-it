---
title: Comando Synchronize (TMSL) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4265e6fa1e2214fae53cacdb084e152005eb3647
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033274"
---
# <a name="synchronize-command-tmsl"></a>Comando Synchronize (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Sincronizza un database Analysis Services con un altro database esistente.  
  
## <a name="request"></a>Richiesta  
 Comando synchronize le proprietà accettate dal file JSON sono i seguenti.  
  
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
  
 Comando synchronize le proprietà accettate dal file JSON sono i seguenti.  
  
||||  
|-|-|-|  
|**Proprietà**|**Default**|**Descrizione**|  
|Database||Il nome dell'oggetto di database da sincronizzare.|  
|origine||La stringa di connessione da utilizzare per connettersi al server di origine.|  
|synchronizeSecurity|skipMembership|Valore di enumerazione che specifica la modalità di ripristino delle definizioni di sicurezza, inclusi i ruoli e autorizzazioni. I valori validi includono skipMembership, copyAll, ignoreSecurity.|  
|applyCompression|True|Valore booleano che, se è true, indica che verrà applicata la compressione durante l'operazione di sincronizzazione. in caso contrario, false.|  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione XMLA.  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene usato in un'istruzione del [metodo Execute &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 È possibile generare uno script già pronte per questo comando da SSMS facendo clic sul pulsante Script nella finestra di dialogo sincronizzazione guidata Database.  
  
 Il [ \[MS-SSAS-T\]: QL Server tabulare di Analysis Services (SQL Server tecnico Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include sezione 3.1.5.2.2 che descrive la struttura dei comandi di metadati tabulari JSON e gli oggetti. Attualmente, tale documento viene illustrata la funzionalità non ancora implementata nello script TMSL e comandi. Vedere l'argomento [Tabular Model Scripting Language &#40;TMSL&#41; riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) per chiarimenti sui quali è supportato  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
