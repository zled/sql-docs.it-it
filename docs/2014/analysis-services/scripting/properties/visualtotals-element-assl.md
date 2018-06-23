---
title: Elemento VisualTotals (ASSL) | Documenti Microsoft
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
- VisualTotals Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- VisualTotals
helpviewer_keywords:
- VisualTotals element
ms.assetid: 352a05b1-846c-4d58-ac36-1f5ad418ba7d
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 73d5bb9579c078fab44a04d173edc2f606c856a1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169748"
---
# <a name="visualtotals-element-assl"></a>Elemento VisualTotals (ASSL)
  Contiene un'espressione MDX (Multidimensional Expressions) che determina se per i membri dell'attributo vengono visualizzati i totali visivi.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributePermission>  
      ...  
      <VisualTotals>...</VisualTotals>  
   ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|`0`|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Attributepermissions](../objects/attributepermission-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'elemento che corrisponde al padre di `VisualTotals` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  