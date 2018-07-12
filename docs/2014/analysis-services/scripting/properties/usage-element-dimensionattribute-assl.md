---
title: Elemento Usage (DimensionAttribute) (ASSL) | Microsoft Docs
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
- Usage Element (DimensionAttribute)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: c5e38d2e-5a8e-4157-84e9-285e78c84e74
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce7dea2cb3c0e928b5a1b0c80aa0ca526f5f8329
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183240"
---
# <a name="usage-element-dimensionattribute-assl"></a>Elemento Usage (DimensionAttribute) (ASSL)
  Descrive la modalità di utilizzo di un attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
      ...  
   <Usage>...</Usage>  
   ...  
</DimensionAttribute>  
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
|Elemento padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Regolare*|L’attributo è un attributo regolare.|  
|*Key*|L’attributo è un attributo chiave.|  
|*Parent*|L’attributo è un attributo padre.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Usage` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.AttributeUsage>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi e gerarchie di attributi](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
