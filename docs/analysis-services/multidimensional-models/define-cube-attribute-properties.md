---
title: Definire le proprietà di attributo del cubo | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e2ab2374955710452f1ba1cba91e3a4d8ff8c1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34026868"
---
# <a name="define-cube-attribute-properties"></a>Definire le proprietà degli attributi dei cubi
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Le proprietà degli attributi dei cubi consentono di specificare impostazioni univoche per gli attributi delle dimensioni dei cubi basate sulla stessa dimensione di database. Nella tabella seguente vengono descritte le proprietà di un attributo del cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**AggregationUsage**|Specifica come verranno progettate le aggregazioni per l'attributo tramite la Progettazione guidata aggregazioni. Il valore predefinito è **Default**. I possibili valori della proprietà sono i seguenti:<br /><br /> **Default**:<br />                    Nella Progettazione guidata aggregazioni viene applicata una regola predefinita in base al tipo di attributo (Full per le chiavi, Unrestricted negli altri casi).<br /><br /> **Nessuno**:<br />                    Nessuna aggregazione del cubo deve includere l'attributo.<br /><br /> **Unrestricted**:<br />                    non vengono applicate restrizioni alla Progettazione guidata aggregazioni<br /><br /> **Full**:<br />                    Ogni aggregazione del cubo deve includere l'attributo.|  
|**AttributeHierarchyEnabled**|Identifica se la gerarchia dell'attributo è abilitata in questa dimensione del cubo. Questa proprietà consente di disabilitare le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante è disabilitata. Il valore predefinito è **True**.|  
|**OptimizedState**|Indica se la gerarchia dell'attributo è ottimizzata in questa dimensione del cubo. Questa proprietà consente di ottimizzare le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante non è ottimizzata. Il valore predefinito è **FullyOptimized**. I possibili valori della proprietà sono i seguenti:<br /><br /> **FullyOptimized**: l'istanza compila indici per la gerarchia allo scopo di migliorare le prestazioni delle query. Si tratta del valore predefinito.<br /><br /> **NotOptimized**:<br />                    L'istanza non compila indici aggiuntivi.|  
|**AttributeHierarchyVisible**|Indica se la gerarchia dell'attributo è visibile in questa dimensione del cubo. Questa proprietà consente di rendere visibili le gerarchie in cubi o ruoli di dimensione specifici. Questa impostazione non produce alcun effetto se la gerarchia dell'attributo sottostante non è visibile. Il valore predefinito è **True**.|  
|**AttributeID**|Contiene l'identificatore univoco (ID) dell'attributo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Definire le proprietà di dimensione del cubo](../../analysis-services/multidimensional-models/define-cube-dimension-properties.md)   
 [Definire le proprietà di gerarchia del cubo](../../analysis-services/multidimensional-models/define-cube-hierarchy-properties.md)  
  
  
