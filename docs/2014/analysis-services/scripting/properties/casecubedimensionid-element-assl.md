---
title: Elemento CaseCubeDimensionID (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CaseCubeDimensionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CaseCubeDimensionID
helpviewer_keywords:
- CaseCubeDimensionID element
ms.assetid: 96720e13-7f9b-4768-ad4b-4def40758707
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d18fb24a3e2f30dbbc0f8b085bd89096baede81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082651"
---
# <a name="casecubedimensionid-element-assl"></a>Elemento CaseCubeDimensionID (ASSL)
  Contiene l'identificatore (ID) della dimensione del cubo che correla la dimensione di data mining al gruppo di misure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataMiningMeasureGroupDimension>  
   ...  
   <CaseCubeDimensionID>...</CaseCubeDimensionID>  
   ...  
</DataMiningMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataMiningMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `CaseCubeDimensionID` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DataMiningMeasureGroupDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
