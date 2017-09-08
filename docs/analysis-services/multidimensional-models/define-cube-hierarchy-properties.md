---
title: "Definire le proprietà di gerarchia del cubo | Documenti Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 69781dd1476cd0396e748be0ddf91fd4dd0bb0dc
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="define-cube-hierarchy-properties"></a>Definire le proprietà della gerarchia del cubo
  Le proprietà delle gerarchie dei cubi consentono di specificare impostazioni univoche per gerarchie definite dall'utente in dimensioni del cubo basate sulla stessa dimensione del database. Nella tabella seguente vengono descritte le proprietà della gerarchia di un cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Abilitata**|Determina l'eventuale abilitazione della gerarchia per la dimensione del cubo.|  
|**HierarchyID**|Contiene l'identificatore univoco (ID) della gerarchia.|  
|**OptimizedState**|Determina il livello di ottimizzazione applicato alla gerarchia. I possibili valori della proprietà sono i seguenti:<br /><br /> **FullyOptimized**:<br />                    L'istanza compila indici per la gerarchia allo scopo di migliorare le prestazioni di esecuzione delle query. Si tratta del valore predefinito.<br /><br /> **NotOptimized**:<br />                    L'istanza non compila indici aggiuntivi.|  
|**Visible**|Determina la visibilità della gerarchia del cubo. Il valore predefinito è **True**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie definite dall'utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
