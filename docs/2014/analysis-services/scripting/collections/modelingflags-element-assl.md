---
title: Elemento ModelingFlags (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ModelingFlags Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ModelingFlags
helpviewer_keywords:
- ModelingFlags element
ms.assetid: 83968c1e-aae8-4657-aa53-d971de0dc834
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 369af68b69c25d70ea80096947a0ecda4488418a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063261"
---
# <a name="modelingflags-element-assl"></a>Elemento ModelingFlags (ASSL)
  Contiene la raccolta di [ModelingFlag](../objects/modelingflag-element-assl.md) gli elementi per una colonna in un [MiningStructure](../objects/miningstructure-element-assl.md) o un [MiningModel](../objects/miningmodel-element-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModelColumn> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <ModelingFlags>  
      <ModelingFlag xsi:type="MiningModelingFlag">...</ModelingFlag>  
   </ModelingFlags>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|[ModelingFlag](../objects/modelingflag-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
