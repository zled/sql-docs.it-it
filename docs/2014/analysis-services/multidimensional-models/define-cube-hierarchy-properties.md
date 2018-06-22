---
title: Definire le proprietà di gerarchia del cubo | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 199e00331e26cea5c84242582f9c6382215ad411
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055390"
---
# <a name="define-cube-hierarchy-properties"></a>Definire le proprietà della gerarchia del cubo
  Le proprietà delle gerarchie dei cubi consentono di specificare impostazioni univoche per gerarchie definite dall'utente in dimensioni del cubo basate sulla stessa dimensione del database. Nella tabella seguente vengono descritte le proprietà della gerarchia di un cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|`Enabled`|Determina l'eventuale abilitazione della gerarchia per la dimensione del cubo.|  
|`HierarchyID`|Contiene l'identificatore univoco (ID) della gerarchia.|  
|`OptimizedState`|Determina il livello di ottimizzazione applicato alla gerarchia. I possibili valori della proprietà sono i seguenti:<br /><br /> `FullyOptimized`: L'istanza compila indici per la gerarchia migliorare le prestazioni delle query. Si tratta del valore predefinito.<br /><br /> `NotOptimized`: L'istanza non compila indici aggiuntivi.|  
|`Visible`|Determina la visibilità della gerarchia del cubo. Il valore predefinito è `True`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie utente](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  