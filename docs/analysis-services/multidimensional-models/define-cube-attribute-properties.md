---
title: "Definire le proprietà di attributo del cubo | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
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
helpviewer_keywords: cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f051a3372b965e2652dfd6ea4c57826212509c1d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="define-cube-attribute-properties"></a>Definire le proprietà degli attributi dei cubi
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Le proprietà di attributo del cubo consentono di specificare impostazioni univoche per gli attributi della dimensione in dimensioni del cubo basate sulla stessa dimensione del database. Nella tabella seguente vengono descritte le proprietà di un attributo del cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**AggregationUsage**|Specifica come verranno progettate le aggregazioni per l'attributo tramite la Progettazione guidata aggregazioni. Il valore predefinito è **Default**. I possibili valori della proprietà sono i seguenti:<br /><br /> **Default**:<br />                    Nella Progettazione guidata aggregazioni viene applicata una regola predefinita in base al tipo di attributo (Full per le chiavi, Unrestricted negli altri casi).<br /><br /> **Nessuno**:<br />                    Nessuna aggregazione del cubo deve includere l'attributo.<br /><br /> **Unrestricted**:<br />                    non vengono applicate restrizioni alla Progettazione guidata aggregazioni<br /><br /> **Full**:<br />                    Ogni aggregazione del cubo deve includere l'attributo.|  
|**AttributeHierarchyEnabled**|Identifica se la gerarchia dell'attributo è abilitata in questa dimensione del cubo. Questa proprietà consente di disabilitare le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante è disabilitata. Il valore predefinito è **True**.|  
|**OptimizedState**|Indica se la gerarchia dell'attributo è ottimizzata in questa dimensione del cubo. Questa proprietà consente di ottimizzare le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante non è ottimizzata. Il valore predefinito è **FullyOptimized**. I possibili valori della proprietà sono i seguenti:<br /><br /> **FullyOptimized**: l'istanza compila indici per la gerarchia allo scopo di migliorare le prestazioni delle query. Si tratta del valore predefinito.<br /><br /> **NotOptimized**:<br />                    L'istanza non compila indici aggiuntivi.|  
|**AttributeHierarchyVisible**|Indica se la gerarchia dell'attributo è visibile in questa dimensione del cubo. Questa proprietà consente di rendere visibili le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante non è visibile. Il valore predefinito è **True**.|  
|**AttributeID**|Contiene l'identificatore univoco (ID) dell'attributo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Definire le proprietà delle dimensioni del cubo](../../analysis-services/multidimensional-models/define-cube-dimension-properties.md)   
 [Definire le proprietà della gerarchia del cubo](../../analysis-services/multidimensional-models/define-cube-hierarchy-properties.md)  
  
  
