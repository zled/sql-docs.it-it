---
title: Cubi nei modelli multidimensionali | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: a7a63cc3ce5a86701a20bb4083b7eb88ef1d4b66
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="cubes-in-multidimensional-models"></a>Cubi nei modelli multidimensionali
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Un cubo è una struttura multidimensionale che contiene informazioni per scopi analitici. Un cubo è principalmente costituito da dimensioni e misure. Le dimensioni definiscono la struttura del cubo utilizzata per effettuare delle sezioni, mentre le misure forniscono valori numerici aggregati di interesse per l'utente finale. Come struttura logica, un cubo consente a un'applicazione client di recuperare i valori delle misure, come se si trovassero nelle celle del cubo. Le celle vengono definite per ogni possibile valore riepilogato. Una cella del cubo è definita dall'intersezione dei membri della dimensione e contiene i valori aggregati delle misure a quell'intersezione specifica.  
  
## <a name="benefits-of-using-cubes"></a>Vantaggi derivanti dall'utilizzo dei cubi  
 Un cubo rappresenta un contenitore in cui vengono archiviati tutti i dati correlati a scopo di analisi.  
  
## <a name="components-of-cubes"></a>Componenti dei cubi  
 Un cubo è composto dagli elementi seguenti:  
  
|Elemento|Description|  
|-------------|-----------------|  
|Dimensioni|[Dimensioni nei modelli multidimensionali](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)|  
|Misure e gruppi di misure|[Creare misure e gruppi di misure nei modelli multidimensionali](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|  
|Partizioni|[Partizioni nei modelli multidimensionali](../../analysis-services/multidimensional-models/partitions-in-multidimensional-models.md)|  
|Prospettive|[Prospettive nei modelli multidimensionali](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|  
|Gerarchie|[Creare gerarchie definite dall'utente](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)|  
|Azioni|[Azioni nei modelli multidimensionali](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|  
|Indicatori KPI|[Indicatori di prestazioni chiave & #40; Gli indicatori KPI & #41; nei modelli multidimensionali](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|  
|Calcoli|[Calcoli nei modelli multidimensionali](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|  
|Traduzioni|[Traduzioni nei modelli multidimensionali &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Creare un cubo tramite la creazione guidata cubo](../../analysis-services/multidimensional-models/create-a-cube-using-the-cube-wizard.md)|Viene illustrato come utilizzare la Creazione guidata cubo per definire un cubo, le dimensioni, gli attributi delle dimensioni e le gerarchie definite dall'utente.|  
|[Creare misure e gruppi di misure nei modelli multidimensionali](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|Descrive come definire i gruppi di misure.|  
|[Calcoli nei modelli multidimensionali](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|Descrive come definire e configurare un calcolo in uno script MDX.|  
|[Azioni nei modelli multidimensionali](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|Descrive come definire e configurare un'azione.|  
|[Prospettive nei modelli multidimensionali](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|Descrive come definire e configurare una prospettiva.|  
|[Definizione delle Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|Descrive come utilizzare le stored procedure.|  
  
  
