---
title: Elemento ClassifiedColumns (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3708b343da514bfddd5fddbdf3d32b4c394b7e63
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031302"
---
# <a name="classifiedcolumns-element-assl"></a>Elemento ClassifiedColumns (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di colonne correlate classificate dal [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructureColumn xsi:type="ScalarMiningStructureColumn">  
   ...  
   <ClassifiedColumns>  
      <ClassifiedColumnID>...</ClassifiedColumnID>  
   </ClassifiedColumns>  
   ...  
</MiningStructureColumn>  
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
|Elementi padre|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) di tipo[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Elementi figlio|[ClassifiedColumnID](../../../analysis-services/scripting/properties/classifiedcolumnid-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento che corrisponde all'elemento padre **ClassifiedColumns** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati MiningStructureColumn &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)   
 [Elemento MiningStructure &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
