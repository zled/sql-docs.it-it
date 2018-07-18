---
title: Elemento hierarchies (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 33348335eef71547f58e0e8d45a85bd2eab6c827
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34034802"
---
# <a name="hierarchies-element-assl"></a>Elemento Hierarchies (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di elementi [Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) associati all'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension> <!-- or CubeDimension, PerspectiveDimension -->  
   ...  
   <Hierarchies>  
            <Hierarchy>...</Hierarchy> <!-- parent: Dimension -->  
      <!-- or -->  
      <Hierarchy xsi:type="CubeHierarchy">...</Hierarchy> <!-- parent: CubeDimension -->  
     <!-- or -->  
      <Hierarchy xsi:type="PerspectiveHierarchy">...</Hierarchy> <!-- parent: PerspectiveDimension -->  
   <Hierarchies>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Elemento figlio|  
|------------------------|-------------------|  
|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|[Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) di tipo [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)|  
|[Dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[Gerarchia](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|  
|[PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|[Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) di tipo [CubeHierarchy](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.HierarchyCollection>, <xref:Microsoft.AnalysisServices.CubeHierarchyCollection> e <xref:Microsoft.AnalysisServices.PerspectiveHierarchyCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
