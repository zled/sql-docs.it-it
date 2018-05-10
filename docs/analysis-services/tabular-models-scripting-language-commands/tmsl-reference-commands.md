---
title: Il linguaggio di Scripting (TMSL) del modello tabulare comandi | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 915e394805dc49ad761da3b5459b6525776ff9e3
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="tmsl-reference---commands"></a>Riferimento TMSL - comandi
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  È possibile eseguire comandi su un endpoint XMLA, la formulazione delle definizioni degli oggetti in JSON mediante la Tabular Model Scripting Language (TMSL), nei database modello tabulare.   Vedere [le definizioni degli oggetti in Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) per un elenco di oggetti utilizzati con i comandi seguenti.  
  
## <a name="object-operations"></a>Operazioni di oggetto  
  
|||  
|-|-|  
|[Comando ALTER &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)|Apportare modifiche inline a un oggetto senza dover specificare la definizione completa.|  
|[Creare un comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)|Crea un nuovo oggetto, inclusi i relativi discendenti.|  
|[Comando CreateOrReplace &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)|Creare o sostituire le parti di una definizione di oggetto. È necessario fornire la definizione completa.|  
|[Comando Delete &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)|Elimina un oggetto, inclusi i relativi discendenti.|  
  
## <a name="data-refresh-operations"></a>Operazioni di aggiornamento dati  
  
|||  
|-|-|  
|[Comando MergePartitions &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md)|Unire una partizione di destinazione in un'origine e di eliminare la destinazione.|  
|[Comando Refresh &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)|Elaborare un database, tabella o partizione.|  
  
## <a name="scripting"></a>Generazione di script  
  
|||  
|-|-|  
|[Sequenza di comandi &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)|Operazioni batch in sequenza o in parallelo|  
  
## <a name="database-management-operations"></a>Operazioni di gestione di database  
  
|||  
|-|-|  
|[Attach-comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)|Aggiunge un file al server.|  
|[Detach-comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)|Rimuove un file dal server.|  
|[Comando di backup &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)|Crea un file di backup di un database.|  
|[Il comando RESTORE &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)|Ripristina database nel server.|  
|[Il comando Synchronize &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/synchronize-command-tmsl.md)|Sincronizza un database Analysis Services con un altro database esistente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Installare il provider di dati di Analysis Services &#40;AMO, ADOMD.NET, MSOLAP&#41;](../../analysis-services/instances/install-windows/install-analysis-services-data-providers-amo-adomd-net-msolap.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
