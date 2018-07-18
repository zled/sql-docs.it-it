---
title: Elemento LastProcessed (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- LastProcessed Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LastProcessed
helpviewer_keywords:
- LastProcessed element
ms.assetid: df3d1f6f-705c-4408-9eb3-c550a1dec450
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d5fd5e94c8a92ee21b1cb04e5f9ef62eddae91f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206191"
---
# <a name="lastprocessed-element-assl"></a>Elemento LastProcessed (ASSL)
  Contiene il timestamp di sola lettura che indica quando il database che contiene l'elemento padre viene elaborato per ultimo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
      <LastProcessed>...</LastProcessed>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|DateTime|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](../objects/cube-element-assl.md), [Database](../objects/database-element-assl.md), [dimensione](../objects/dimension-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [Partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gestisce il valore della `LastProcessed` elemento. Il valore modifica solo se viene elaborato il database che contiene l'elemento padre. Elaborare individualmente l'elemento padre non modifica il valore dell'elemento `LastProcessed`.  
  
 Gli elementi che corrispondono agli elementi padre di `LastProcessed` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure> e <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
