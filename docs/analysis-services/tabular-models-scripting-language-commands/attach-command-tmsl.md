---
title: Attach-comando (TMSL) | Documenti Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7a12d148-eac9-4e6c-a222-1439e0817c64
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 995e77345c2770f59db620afb1ced2085eaeefa2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="attach-command-tmsl"></a>Attach-comando (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Collega un file di Analysis Services in un server.  
  
  
## <a name="request"></a>Richiesta  
  
```  
{   
   "attach":{   
      "folder":"C:\\Program Files\\Microsoft SQL Server\\MSAS13.Tabular\\OLAP\\Data\\",  
      "readWriteMode":"readOnly",  
      "password":"secret"  
   }  
}  
```  
  
 Le proprietà accettate da JSON attach-comando sono i seguenti.  
  
||||  
|-|-|-|  
|**Proprietà**|**Default**|**Description**|  
|database|[Obbligatorio]|Il nome dell'oggetto di database da collegare.|  
|folder|[Obbligatorio]|La cartella che contiene il database collegato.|  
|password|Vuoto|La password da utilizzare per crittografare i segreti nel database collegato.|  
|readWriteMode|Lettura/scrittura|Valore di enumerazione che indica le modalità di accesso consentite al database.<br /><br /> **Come indicato di seguito sono riportati i valori di enumerazione:**<br /><br /> readWrite: è consentito l'accesso in lettura / scrittura.<br /><br /> readOnly: è consentito l'accesso di sola lettura.<br /><br /> readOnlyExclusive: è consentito l'accesso esclusivo in sola lettura.|  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione di XMLA.  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene utilizzato in un'istruzione del [metodo Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 È possibile generare uno script già pronto per questo comando da SQL Server Management Studio facendo clic sul pulsante di Script nella finestra di dialogo Collega Database.  
  
 Il [ \[SSAS-MS-T\]: QL Server tabulare di Analysis Services (SQL Server tecniche Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON. Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento [tabulare Model Scripting Language &#40; TMSL &#41; Riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) per chiarimenti sui quali è supportata  

## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
