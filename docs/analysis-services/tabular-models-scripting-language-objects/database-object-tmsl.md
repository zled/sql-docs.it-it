---
title: Oggetto di database (TMSL) | Documenti Microsoft
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
ms.assetid: ae5c046b-8242-4046-ae76-2c070503fd93
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c8506cdf1917fb803c701ca0acd9f1bf1f25b141
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="database-object-tmsl"></a>Oggetto di database (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Definisce un database tabulare con livello di compatibilità 1200 o superiore, in base a un modello dello stesso livello. Questo argomento viene illustrata la definizione dell'oggetto di un database, fornendo il payload per le richieste di creare, modificano, eliminano ed eseguono attività di gestione di database.  
  
> [!NOTE]  
>  In qualsiasi script, è possibile fare riferimento un solo database al momento. Per qualsiasi oggetto diverso dal database stesso, la proprietà del Database è facoltativa se si specifica il modello. È presente un mapping uno a uno tra un modello e un Database che può essere usato per dedurre il nome del Database se viene fornito in modo non esplicito.   
> Analogamente, è possibile lasciare il modello, impostandone le proprietà nel Database.  
  
## <a name="object-definition"></a>Definizione dell'oggetto  
 Tutti gli oggetti hanno un set comune di proprietà, inclusi nome, tipo, descrizione, una raccolta di proprietà e le annotazioni. **Database** gli oggetti dispongono anche le proprietà seguenti.  
  
 livello di compatibilità  
 Attualmente, i valori validi sono 1200, 1400. Livelli di compatibilità inferiori utilizzano un motore di metadati diversi.  
  
 readwritemode  
 Enumera la modalità del database. È comune per creare un database di sola lettura nelle configurazioni di disponibilità o della scalabilità elevate. I valori validi includono readWrite,  
                sola lettura,  
                o readOnlyExclusive. Vedere [la disponibilità elevata e scalabilità in Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md) e [passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) per ulteriori informazioni su quando questa proprietà viene utilizzata.  
  
## <a name="usage"></a>Utilizzo  
 **Database** gli oggetti vengono utilizzati in quasi tutti i comandi. Vedere [del modello tabulare comandi Scripting Language &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) per un elenco. Oggetto **Database** oggetto è un figlio di un oggetto Server.  
  
 Durante la creazione, la sostituzione o modifica di un oggetto di database, specificare tutte le proprietà di sola lettura della definizione dell'oggetto. Omissione di una proprietà di lettura / scrittura è considerata un'operazione di eliminazione.  
  
## <a name="partial-syntax"></a>Sintassi parziale  
 Poiché questa definizione di oggetto è elevata, sono elencate solo le proprietà dirette. Il **modello** oggetto fornisce la maggior parte della definizione del database. Vedere [del modello oggetto &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md) per la modalità con cui l'oggetto è definito.  
  
```  
    "database": {  
      "type": "object",  
      "properties": {  
        "name": {  
          "type": "string"  
        },  
        "id": {  
          "type": "string"  
        },  
        "description": {  
          "type": "string"  
        },  
        "compatibilityLevel": {  
          "type": "integer"  
        },  
        "readWriteMode": {  
          "enum": [  
            "readWrite",  
            "readOnly",  
            "readOnlyExclusive"  
          ]  
        },  
        "model": {  
          "type": "object",  
          ...  
        }  
    }  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Disponibilità elevata e scalabilità in Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)  
  
  
