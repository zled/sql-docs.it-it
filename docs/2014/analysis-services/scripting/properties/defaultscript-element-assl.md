---
title: Elemento DefaultScript (ASSL) | Documenti Microsoft
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
- DefaultScript Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultScript
helpviewer_keywords:
- DefaultScript element
ms.assetid: 60716e63-2d64-4774-9ac9-253efe612fa5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b0a26b8b703636aebb6d3701c5c7c99d24a25ade
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171103"
---
# <a name="defaultscript-element-assl"></a>Elemento DefaultScript (ASSL)
  Identifica il valore predefinito [MdxScript](../objects/mdxscript-element-assl.md) elemento il [MdxScripts](../collections/mdxscripts-element-assl.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MdxScript>  
   ...  
   <DefaultScript>...</DefaultScript>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|`True`|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MdxScript](../objects/mdxscript-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'impostazione del valore di `DefaultScript` su `True` per uno script comporta l'impostazione del valore di `DefaultScript` su `False` per tutti gli altri elementi `MdxScript` nella raccolta `MdxScripts`.  
  
 L'elemento che corrisponde al padre di `DefaultScript` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  