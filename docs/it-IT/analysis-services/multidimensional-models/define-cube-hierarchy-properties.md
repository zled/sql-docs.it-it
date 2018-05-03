---
title: Definire le proprietà di gerarchia del cubo | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e91bbb6bdc5ef6e84653d69fc26e4caa18c9f37
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="define-cube-hierarchy-properties"></a>Definire le proprietà della gerarchia del cubo
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Le proprietà delle gerarchie dei cubi consentono di specificare impostazioni univoche per gerarchie definite dall'utente in dimensioni del cubo basate sulla stessa dimensione del database. Nella tabella seguente vengono descritte le proprietà della gerarchia di un cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Abilitata**|Determina l'eventuale abilitazione della gerarchia per la dimensione del cubo.|  
|**HierarchyID**|Contiene l'identificatore univoco (ID) della gerarchia.|  
|**OptimizedState**|Determina il livello di ottimizzazione applicato alla gerarchia. I possibili valori della proprietà sono i seguenti:<br /><br /> **FullyOptimized**:<br />                    L'istanza compila indici per la gerarchia allo scopo di migliorare le prestazioni di esecuzione delle query. Si tratta del valore predefinito.<br /><br /> **NotOptimized**:<br />                    L'istanza non compila indici aggiuntivi.|  
|**Visible**|Determina la visibilità della gerarchia del cubo. Il valore predefinito è **True**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
