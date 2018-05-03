---
title: Detach-comando (TMSL) | Documenti Microsoft
ms.custom: ''
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 413b49cb-ea8f-415c-a059-ce692b7771a1
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4421d4e82c1c26fd4f435322aec38445b59331f2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="detach-command-tmsl"></a>Detach-comando (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Scollega un database di Analysis Services da un server.  
  
## <a name="request"></a>Richiesta  
  
```  
{   
   "detach": {    
      "database":"AdventureWorksDW2014",  
      "password": "secret"  
   }  
}  
```  
  
 Le proprietà accettate da JSON detach-comando sono i seguenti.  
  
||||  
|-|-|-|  
|**Proprietà**|**Valore predefinito**|**Description**|  
|database|[Obbligatorio]|Il nome dell'oggetto di database da scollegare.|  
|password|Vuoto|La password da utilizzare per crittografare i segreti nel database scollegato.|  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione di XMLA.  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene utilizzato in un'istruzione del [metodo Execute &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 È possibile generare uno script già pronto per questo comando da SQL Server Management Studio facendo clic sul pulsante di Script nella finestra di dialogo Scollega.  
  
 Il [ \[SSAS-MS-T\]: QL Server tabulare di Analysis Services (SQL Server tecniche Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON. Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento ([linguaggio di Scripting del modello tabulare &#40;TMSL&#41; riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) per chiarimenti sui quali è supportata.  

## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
