---
title: Oggetto di database (TMSL) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9da6d97236811aaa0ef8ee757c7b2773bdda496a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34045935"
---
# <a name="database-object-tmsl"></a>Oggetto di database (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce un database tabulare con livello di compatibilità 1200 o superiore, in base a un modello dello stesso livello. Questo argomento viene illustrata la definizione dell'oggetto di un database, fornendo il payload per le richieste di creare, modificano, eliminano ed eseguono attività di gestione di database.  
  
> [!NOTE]  
>  In qualsiasi script, è possibile fare riferimento un solo database al momento. Per qualsiasi oggetto diverso dal database stesso, la proprietà del Database è facoltativa se si specifica il modello. È presente un mapping uno a uno tra un modello e un Database che può essere usato per dedurre il nome del Database se viene fornito in modo non esplicito.   
> Analogamente, è possibile lasciare il modello, impostandone le proprietà nel Database.  
  
## <a name="object-definition"></a>Definizione dell'oggetto  
 Tutti gli oggetti hanno un set comune di proprietà, inclusi nome, tipo, descrizione, una raccolta di proprietà e le annotazioni. **Database** oggetti hanno anche le proprietà seguenti.  
  
 livello di compatibilità  
 Attualmente, i valori validi sono 1200, 1400. Livelli di compatibilità inferiori utilizzano un motore di metadati diversi.  
  
 readwritemode  
 Enumera la modalità del database. È comune per creare un database di sola lettura nelle configurazioni di disponibilità o della scalabilità elevate. I valori validi includono readWrite,  
                sola lettura,  
                o readOnlyExclusive. Vedere [la disponibilità elevata e scalabilità in Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md) e [passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) per ulteriori informazioni su quando questa proprietà viene utilizzata.  
  
## <a name="usage"></a>Utilizzo  
 **Database** gli oggetti vengono utilizzati in quasi tutti i comandi. Vedere [comandi Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) per un elenco. Oggetto **Database** oggetto è un figlio di un oggetto Server.  
  
 Durante la creazione, la sostituzione o modifica di un oggetto di database, specificare tutte le proprietà di sola lettura della definizione dell'oggetto. Omissione di una proprietà di lettura / scrittura è considerata un'operazione di eliminazione.  
  
## <a name="partial-syntax"></a>Sintassi parziale  
 Poiché questa definizione di oggetto è elevata, sono elencate solo le proprietà dirette. Il **modello** oggetto fornisce la maggior parte della definizione del database. Vedere [oggetto modello &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md) al modo in cui l'oggetto è definito.  
  
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
  
  
