---
title: "Definire le proprietà di gerarchia del cubo | Documenti Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 13934070e4121913b82a2604acf26581cf27796f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="define-cube-hierarchy-properties"></a>Definire le proprietà della gerarchia del cubo
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Proprietà della gerarchia del cubo consentono di specificare impostazioni univoche per gerarchie definite dall'utente in dimensioni del cubo basate sulla stessa dimensione del database. Nella tabella seguente vengono descritte le proprietà della gerarchia di un cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Abilitata**|Determina l'eventuale abilitazione della gerarchia per la dimensione del cubo.|  
|**HierarchyID**|Contiene l'identificatore univoco (ID) della gerarchia.|  
|**OptimizedState**|Determina il livello di ottimizzazione applicato alla gerarchia. I possibili valori della proprietà sono i seguenti:<br /><br /> **FullyOptimized**:<br />                    L'istanza compila indici per la gerarchia allo scopo di migliorare le prestazioni di esecuzione delle query. Si tratta del valore predefinito.<br /><br /> **NotOptimized**:<br />                    L'istanza non compila indici aggiuntivi.|  
|**Visible**|Determina la visibilità della gerarchia del cubo. Il valore predefinito è **True**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie definite dall'utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
