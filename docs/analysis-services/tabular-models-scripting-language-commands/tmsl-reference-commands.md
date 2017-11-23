---
title: Il linguaggio di Scripting (TMSL) del modello tabulare comandi | Documenti Microsoft
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4eb07192-6f53-4426-830a-d63a945dbcab
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 71b44ae1e5f8e5db2859bb4d3b2457c752de4dc6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="tmsl-reference---commands"></a>Riferimento TMSL - comandi

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  È possibile eseguire comandi su un endpoint XMLA, la formulazione delle definizioni degli oggetti in JSON mediante la Tabular Model Scripting Language (TMSL), nei database modello tabulare.   Vedere [le definizioni degli oggetti nella tabella del modello Scripting Language &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) per un elenco di oggetti utilizzati con i comandi seguenti.  
  
## <a name="object-operations"></a>Operazioni di oggetto  
  
|||  
|-|-|  
|[ALTER comando &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)|Apportare modifiche inline a un oggetto senza dover specificare la definizione completa.|  
|[Creazione di comandi &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)|Crea un nuovo oggetto, inclusi i relativi discendenti.|  
|[Comando CreateOrReplace &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)|Creare o sostituire le parti di una definizione di oggetto. È necessario fornire la definizione completa.|  
|[Eliminare comandi &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)|Elimina un oggetto, inclusi i relativi discendenti.|  
  
## <a name="data-refresh-operations"></a>Operazioni di aggiornamento dati  
  
|||  
|-|-|  
|[Il comando MergePartitions &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md)|Unire una partizione di destinazione in un'origine e di eliminare la destinazione.|  
|[Aggiornare comando &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)|Elaborare un database, tabella o partizione.|  
  
## <a name="scripting"></a>Generazione di script  
  
|||  
|-|-|  
|[Il comando Sequence &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)|Operazioni batch in sequenza o in parallelo|  
  
## <a name="database-management-operations"></a>Operazioni di gestione di database  
  
|||  
|-|-|  
|[Collegare comando &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)|Aggiunge un file al server.|  
|[Scollegare comandi &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)|Rimuove un file dal server.|  
|[Comando di backup &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)|Crea un file di backup di un database.|  
|[Ripristinare comandi &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)|Ripristina database nel server.|  
|[Sincronizzare comando &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/synchronize-command-tmsl.md)|Sincronizza un database Analysis Services con un altro database esistente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Installare il provider di dati di Analysis Services &#40; AMO, ADOMD.NET, MSOLAP &#41;](../../analysis-services/instances/install-windows/install-analysis-services-data-providers-amo-adomd-net-msolap.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
