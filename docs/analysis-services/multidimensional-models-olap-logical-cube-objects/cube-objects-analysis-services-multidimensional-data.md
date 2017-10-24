---
title: Oggetti (Analysis Services - dati multidimensionali) cubo | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 018739c4f8da237c1a90a101b96888a8583349be
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Oggetti cubo (Analysis Services - Dati multidimensionali)
    
## <a name="introducing-cube-objects"></a>Introduzione agli oggetti cubo  
 Un oggetto <xref:Microsoft.AnalysisServices.Cube> semplice è composto da informazioni di base, dimensioni e gruppi di misure. Le informazioni di base includono il nome e la misura predefinita del cubo, l'origine dati, la modalità di archiviazione e altro.  
  
 La raccolta Dimensions contiene il set effettivo di dimensioni utilizzate nel cubo dalla raccolta di dimensioni del database. È necessario definire tutte le dimensioni nella raccolta di dimensioni del database prima di potervi fare riferimento nel cubo. Le dimensioni private non sono disponibili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 I gruppi di misure sono set di misure nel cubo. Un gruppo di misure è una raccolta di misure con una vista origine dati comune e un set di dimensioni comune. Un gruppo di misure è l'unità di elaborazione delle misure. I gruppi di misure possono essere elaborati singolarmente, per poi essere visualizzati.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|||  
|-|-|  
|Argomento||  
|[Azioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Aggregazioni e progettazione di aggregazioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)||  
|[Calcoli](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)||  
|[Le celle del cubo &#40; Analysis Services - dati multidimensionali &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-cells-analysis-services-multidimensional-data.md)||  
|[Programmazione del modello di cubo proprietà - multidimensionale](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-properties-multidimensional-model-programming.md)||  
|[Archiviazione dei cubi &#40; Analysis Services - dati multidimensionali &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)||  
|[Traduzioni di cubi](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)||  
|[Relazioni tra dimensioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)||  
|[Indicatori KPI nei modelli multidimensionali](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Le misure e gruppi di misure](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)||  
|[Partizioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)||  
|[Prospettive](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)||  
  
  

