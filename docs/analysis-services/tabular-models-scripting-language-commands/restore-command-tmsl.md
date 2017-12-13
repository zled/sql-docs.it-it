---
title: Restore-comando (TMSL) | Documenti Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 360a1567-67ae-459d-8865-9a2bef8d4186
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 45e4461956c78278d367715e8ef665821d487e3f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="restore-command-tmsl"></a>Restore-comando (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Ripristina un database di Analysis Services da un file di backup.  
  
## <a name="request"></a>Richiesta  
  
```  
    {  
"restore": {  
            "description": "Parameters of Restore command of Analysis Services JSON API",  
            "properties": {  
            "database": {  
                "type": "string"  
            },  
            "file": {  
                "type": "string"  
            },  
            "password": {  
                "type": "string"  
            },  
            "dbStorageLocation": {  
                "type": "string"  
            },  
            "allowOverwrite": {  
                "type":boolean  
            },  
            "readWriteMode": {  
                "enum": [  
                "readWrite",  
                "readOnly",  
                "readOnlyExclusive"  
                ]  
. . .   
```  
  
 **Ripristinare** dispone di diverse proprietà.  
  
||||  
|-|-|-|  
|**Proprietà**|**Default**|**Description**|  
|database|[Obbligatorio]|Il nome dell'oggetto di database da ripristinare.|  
|file|[Obbligatorio]|Il nome o percorso file di backup.|  
|password|Vuoto|La password da usare per decrittografare il file di backup.|  
|allowOverwrite|False|Valore booleano che, se è true, indica che un file di backup esistente verrà sovrascritto; in caso contrario false.|  
|readWriteMode|Lettura/scrittura|Valore di enumerazione che indica le modalità di accesso consentite al database.<br /><br /> **Come indicato di seguito sono riportati i valori di enumerazione:**<br /><br /> readWrite: è consentito l'accesso in lettura / scrittura.<br /><br /> readOnly: è consentito l'accesso di sola lettura.<br /><br /> readOnlyExclusive: è consentito l'accesso esclusivo in sola lettura.|  
|dbStorageLocation|Vuoto|Percorso di archiviazione per il database ripristinato.|  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione di XMLA.  
  
## <a name="example"></a>Esempio  
 **Esempio 1** -ripristinare un database da una cartella locale.  
  
```  
{   
   "restore": {   
      "database":"AdventureWorksDW2014",  
      "file":"c:\\awdbdwfile.abf",  
      "security":"...",  
      "allowOverwrite":"true",  
      "password":"..",  
      "locations":"d:\\SQL Server Analysis Services\\data\\",  
      "storageLocation":".."  
   }  
}  
```  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene utilizzato in un'istruzione del [metodo Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 È possibile generare uno script già pronto per questo comando da SQL Server Management Studio facendo clic sul pulsante di Script nella finestra di dialogo ripristino.  
  
 Il [ \[SSAS-MS-T\]: QL Server tabulare di Analysis Services (SQL Server tecniche Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON. Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento [tabulare Model Scripting Language &#40; TMSL &#41; Riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) per chiarimenti sui quali è supportata  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Backup e ripristino di database di Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
