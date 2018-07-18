---
title: Definire le proprietà di attributo del cubo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af8e4c54aac81e4f6decdd6533a052fce751b627
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299221"
---
# <a name="define-cube-attribute-properties"></a>Definire le proprietà degli attributi dei cubi
  Le proprietà degli attributi dei cubi consentono di specificare impostazioni univoche per gli attributi delle dimensioni dei cubi basate sulla stessa dimensione di database. Nella tabella seguente vengono descritte le proprietà di un attributo del cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|`AggregationUsage`|Specifica come verranno progettate le aggregazioni per l'attributo tramite la Progettazione guidata aggregazioni. I possibili valori della proprietà sono i seguenti:<br /><br /> `Default`: Per impostazione predefinita. Nella Progettazione guidata aggregazioni viene applicata una regola predefinita in base al tipo di attributo (Full per le chiavi, Unrestricted negli altri casi).<br /><br /> `None`: Nessuna aggregazione del cubo deve includere l'attributo.<br /><br /> `Unrestricted`: Non esistono restrizioni nella progettazione guidata aggregazioni.<br /><br /> `Full`: Ogni aggregazione del cubo deve includere l'attributo.|  
|`AttributeHierarchyEnabled`|Identifica se la gerarchia dell'attributo è abilitata in questa dimensione del cubo. Questa proprietà consente di disabilitare le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante è disabilitata. Valore predefinito è `True`.|  
|`OptimizedState`|Indica se la gerarchia dell'attributo è ottimizzata in questa dimensione del cubo. Questa proprietà consente di ottimizzare le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante non è ottimizzata. I possibili valori della proprietà sono i seguenti:<br /><br /> `FullyOptimized`: Per impostazione predefinita. L'istanza compila indici per la gerarchia allo scopo di migliorare le prestazioni di esecuzione delle query. Si tratta del valore predefinito.<br /><br /> `NotOptimized`: L'istanza non compila indici aggiuntivi.|  
|`AttributeHierarchyVisible`|Indica se la gerarchia dell'attributo è visibile in questa dimensione del cubo. Questa proprietà consente di rendere visibili le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante non è visibile. Il valore predefinito è `True`.|  
|`AttributeID`|Contiene l'identificatore univoco (ID) dell'attributo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Definire le proprietà di dimensione cubo](define-cube-dimension-properties.md)   
 [Definire le proprietà della gerarchia del cubo](define-cube-hierarchy-properties.md)  
  
  
