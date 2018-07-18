---
title: Stato elemento (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- State Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- State
helpviewer_keywords:
- State element
ms.assetid: b6ee1144-89f7-4ced-bc87-c2e33ca25f73
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 507dab440db095f844b4fad9dcdd96e29d18d487
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206031"
---
# <a name="state-element-assl"></a>Elemento State (ASSL)
  Contiene un valore di sola lettura che descrive lo stato dell'elaborazione corrente dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, MiningModel, MiningStructure, Partition -->  
      ...  
   <State>...</State>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](../objects/cube-element-assl.md), [dimensione](../objects/dimension-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Elaborati*|L'elemento è stato elaborato interamente.|  
|*PartiallyProcessed*|L'elemento è stato elaborato parzialmente. ([Cubo](../objects/cube-element-assl.md) e [MeasureGroup](../objects/group-element-assl.md) solo.)|  
|*Non elaborati*|L'elemento non è stato elaborato.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `State` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.AnalysisState>.  
  
 Gli elementi che corrispondono ai padri di `State` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure> e <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
