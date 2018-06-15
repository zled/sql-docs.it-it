---
title: Programmazione del modello di cubo proprietà - multidimensionale | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85453133ab9facd9f3ed56ad98fa2761ac527e40
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022198"
---
# <a name="cube-properties---multidimensional-model-programming"></a>Programmazione del modello di cubo proprietà - multidimensionale
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  I cubi dispongono di proprietà che è possibile impostare per influire sul funzionamento a livello di cubo. Nella tabella seguente è disponibile un riepilogo di tali proprietà.  
  
> [!NOTE]  
>  Alcune proprietà vengono impostate automaticamente quando si crea il cubo e non possono essere modificate.  
  
 Per ulteriori informazioni su come impostare le proprietà dei cubi, vedere [Progettazione cubi &#40;Analysis Services - dati multidimensionali&#41;](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96).  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**AggregationPrefix**|Specifica il prefisso comune utilizzato per i nomi di aggregazioni.|  
|**Confronto**|Specifica l'identificatore delle impostazioni locali (LCID) e il flag di confronto, separati da un carattere di sottolineatura, ad esempio Latin1_General_C1_AS.|  
|**DefaultMeasure**|Contiene un'espressione MDX (Multidimensional Expression) che definisce la misura predefinita per il cubo.|  
|**Description**|Fornisce una descrizione del cubo, che può essere esposta in applicazioni client.|  
|**ErrorConfiguration**|Contiene le impostazioni configurabili per la gestione degli errori, relative alla gestione di chiavi duplicate, chiavi sconosciute, limiti di errore, azione da intraprendere in caso di rilevamento di un errore, file di log degli errori e gestione della chiave Null.|  
|**EstimatedRows**|Specifica il numero di righe stimate nel cubo.|  
|**ID**|Contiene l'identificatore univoco (ID) del cubo.|  
|**Lingua**|Specifica l'identificatore della lingua predefinita del cubo.|  
|**Nome**|Specifica il nome descrittivo del cubo.|  
|**ProactiveCaching**|Definisce le impostazioni di memorizzazione nella cache attiva per il cubo.|  
|**ProcessingMode**|Indica se l'indicizzazione e l'aggregazione devono essere eseguite durante o dopo l'elaborazione. Le opzioni sono **regolare** o **lazy**.|  
|**ProcessingPriority**|Determina la priorità di elaborazione del cubo durante operazioni in background, ad esempio indicizzazione e aggregazioni lente Il valore predefinito è **0**.|  
|**ScriptCacheProcessingMode**|Indica se la cache script deve essere compilata durante o dopo l'elaborazione. Le opzioni sono **regolare** e **lazy**.|  
|**ScriptErrorHandlingMode**|Determina la gestione degli errori. Le opzioni sono **IgnoreNone** o **IgnoreAll**|  
|**Origine**|Visualizza la vista origine dati utilizzata per il cubo.|  
|**StorageLocation**|Specifica il percorso di archiviazione nel file system per il cubo. Se non viene specificato alcun valore, il percorso viene ereditato dal database contenente l'oggetto del cubo.|  
|**StorageMode**|Specifica la modalità di archiviazione per il cubo. I valori sono **MOLAP**, **ROLAP**, o **HOLAP**.|  
|**Visible**|Determina la visibilità del cubo.|  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'impostazione dei valori per la proprietà ErrorConfiguration quando si lavora con i valori null e altri problemi di integrità dei dati, vedere [la gestione di problemi di integrità dei dati in Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Vedere anche  
 [La memorizzazione nella cache & #40; Le partizioni & #41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  
