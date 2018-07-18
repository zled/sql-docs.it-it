---
title: Elemento ProcessingMode (ASSL) | Microsoft Docs
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
- ProcessingMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ProcessingMode
helpviewer_keywords:
- ProcessingMode element
ms.assetid: dff6eeba-f09c-4d8c-ad81-caef76254af0
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a966a1d800107b18316e875bd8c9552df613cfe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273787"
---
# <a name="processingmode-element-assl"></a>Elemento ProcessingMode (ASSL)
  Indica se l'istanza deve essere indicizzata e aggregata durante o dopo l'elaborazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <ProcessingMode>...</ProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Regolare*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](../objects/cube-element-assl.md), [dimensione](../objects/dimension-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di `ProcessingMode` su `Cube` fornisce l'impostazione predefinita per il cubo e può essere ignorato impostando `ProcessingMode` per ogni partizione.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Regolare*|L'istanza indicizza ed esegue le aggregazioni durante l'elaborazione.|  
|*LazyOptimizations*|L'istanza indicizza ed esegue le aggregazioni durante l'elaborazione.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `ProcessingMode` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ProcessingMode>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
