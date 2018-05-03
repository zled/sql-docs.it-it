---
title: Oggetti (Analysis Services - dati multidimensionali) cubo | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f5e670318a298cd49c8c03538093f8739c5f601c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Oggetti cubo (Analysis Services - Dati multidimensionali)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
    
## <a name="introducing-cube-objects"></a>Introduzione agli oggetti cubo  
 Un oggetto <xref:Microsoft.AnalysisServices.Cube> semplice è composto da informazioni di base, dimensioni e gruppi di misure. Le informazioni di base includono il nome e la misura predefinita del cubo, l'origine dati, la modalità di archiviazione e altro.  
  
 La raccolta Dimensions contiene il set effettivo di dimensioni utilizzate nel cubo dalla raccolta di dimensioni del database. È necessario definire tutte le dimensioni nella raccolta di dimensioni del database prima di potervi fare riferimento nel cubo. Le dimensioni private non sono disponibili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 I gruppi di misure sono set di misure nel cubo. Un gruppo di misure è una raccolta di misure con una vista origine dati comune e un set di dimensioni comune. Un gruppo di misure è l'unità di elaborazione delle misure. I gruppi di misure possono essere elaborati singolarmente, per poi essere visualizzati.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|||  
|-|-|  
|Argomento||  
|[Azioni & #40; Analysis Services - dati multidimensionali & #41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Le aggregazioni e progettazione di aggregazioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)||  
|[Calcoli](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)||  
|[Le celle del cubo & #40; Analysis Services - dati multidimensionali & #41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-cells-analysis-services-multidimensional-data.md)||  
|[Oggetti cubo: programmazione del modello multidimensionale](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-properties-multidimensional-model-programming.md)||  
|[Archiviazione dei cubi & #40; Analysis Services - dati multidimensionali & #41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)||  
|[Traduzioni di cubi](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)||  
|[Relazioni tra dimensioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)||  
|[Indicatori di prestazioni chiave & #40; Gli indicatori KPI & #41; nei modelli multidimensionali](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Le misure e gruppi di misure](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)||  
|[Le partizioni & #40; Analysis Services - dati multidimensionali & #41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)||  
|[Prospettive](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)||  
  
  
