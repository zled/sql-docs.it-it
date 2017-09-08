---
title: Cubi nei modelli multidimensionali | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1a555a25c41b4860aa16d5a2cfd43749a0ccd65d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cubes-in-multidimensional-models"></a>Cubi nei modelli multidimensionali
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
|Indicatori KPI|[Indicatori KPI nei modelli multidimensionali](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|  
|Calcoli|[Calcoli nei modelli multidimensionali](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|  
|Traduzioni|[Traduzioni nei modelli multidimensionali &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Creare un cubo mediante la Creazione guidata cubo](../../analysis-services/multidimensional-models/create-a-cube-using-the-cube-wizard.md)|Viene illustrato come utilizzare la Creazione guidata cubo per definire un cubo, le dimensioni, gli attributi delle dimensioni e le gerarchie definite dall'utente.|  
|[Creare misure e gruppi di misure nei modelli multidimensionali](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|Descrive come definire i gruppi di misure.|  
|[Calcoli nei modelli multidimensionali](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|Descrive come definire e configurare un calcolo in uno script MDX.|  
|[Azioni nei modelli multidimensionali](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|Descrive come definire e configurare un'azione.|  
|[Prospettive nei modelli multidimensionali](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|Descrive come definire e configurare una prospettiva.|  
|[Definizione delle stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|Descrive come utilizzare le stored procedure.|  
  
  
