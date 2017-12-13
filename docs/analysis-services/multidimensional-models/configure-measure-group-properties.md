---
title: "Configurare le proprietà del gruppo di misure | Documenti Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Analysis Services], measure groups
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2f650fd897c68e10044a02d55c08f9545a0e6046
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="configure-measure-group-properties"></a>Configurare le proprietà dei gruppi di misure
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Gruppi di misure dispongono di proprietà che consentono di definire gruppi di misure come funzione.  
  
## <a name="measure-group-properties"></a>Proprietà dei gruppi di misure  
 Le proprietà dei gruppi di misure determinano i comportamenti dell'intero gruppo di misure e impostano i comportamenti predefiniti per alcune proprietà delle misure all'interno di un gruppo di misure.  
  
|Proprietà|Definizione|  
|--------------|----------------|  
|**AggregationPrefix**|Si applica all'archiviazione ROLAP. Assegna un prefisso comune alle viste indicizzate in SQL Server, usato per archiviare le aggregazioni per le partizioni associate a questo gruppo di misure.|  
|**DataAggregation**|Questa proprietà è riservata per utilizzi futuri e attualmente non ha alcun effetto. Pertanto, è consigliabile non modificare questa impostazione.|  
|**Description**|È possibile usare questa proprietà per documentare il gruppo di misure.|  
|**ErrorConfiguration**|Impostazioni configurabili per la gestione degli errori, relative alla gestione di chiavi duplicate, chiavi sconosciute, chiavi Null, limiti di errore, azione da eseguire in caso di rilevamento di un errore e file di log degli errori. Vedere [Configurazione errori per l'elaborazione di cubi, partizioni e dimensioni &#40;SSAS - multidimensionale&#41;](../../analysis-services/multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md).|  
|**EstimatedRows**|Specifica il numero stimato di righe della tabella dei fatti.|  
|**EstimatedSize**|Specifica la dimensione stimata (in byte) del gruppo di misure.|  
|**ID**|Specifica l'identificatore dell'oggetto.|  
|**IgnoreUnrelatedDimensions**|Determina se le dimensioni non correlate devono essere forzate al livello principale in caso di inclusione in una query di membri di dimensioni non correlate al gruppo di misure. L'impostazione predefinita è **True**.|  
|**Nome**|Nome della misura. Questa proprietà è di sola lettura.|  
|**ProactiveCaching**|Impostazioni configurabili per la gestione degli errori, relative alla gestione di chiavi duplicate, chiavi sconosciute, chiavi Null, limiti di errore, azione da eseguire in caso di rilevamento di un errore e file di log degli errori.|  
|**ProcessingMode**|Indica se l'indicizzazione e l'aggregazione devono essere eseguite durante o dopo l'elaborazione. Le opzioni sono Regular e LazyAggregations. LazyAggregations consente di eseguire l'aggregazione come attività in background.|  
|**ProcessingPriority**|Determina la priorità di elaborazione del cubo durante operazioni in background, ad esempio indicizzazione e aggregazioni lente Il valore predefinito è **0**.|  
|**StorageLocation**|Percorso di archiviazione del file system per il gruppo di misure. Se non è specificato alcun valore, il percorso verrà ereditato dal cubo contenente il gruppo di misure.|  
|**StorageMode**|Modalità di archiviazione per il gruppo di misure. I valori disponibili sono MOLAP, ROLAP o HOLAP.|  
|**Tipo**|Specifica il tipo del gruppo di misure.|  
  
  
