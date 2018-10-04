---
title: Elemento MiningStructures (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningStructures Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructures
helpviewer_keywords:
- MiningStructures element
ms.assetid: d8144b85-c836-4dcf-96b4-36b9dfd4211d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 082b192ff0a59bf1b8739403acdf35f49698709d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048061"
---
# <a name="miningstructures-element-assl"></a>Elemento MiningStructures (ASSL)
  Contiene la raccolta di [MiningStructure](../objects/miningstructure-element-assl.md) elementi in un [Database](../objects/database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database>  
   ...  
   <MiningStructures>  
      <MiningStructure>...</MiningStructure>  
   </MiningStructures>  
   ...  
</Database>  
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
|Elementi padre|[Database](../objects/database-element-assl.md)|  
|Elementi figlio|[Elemento MiningStructure](../objects/miningstructure-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningStructureCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
