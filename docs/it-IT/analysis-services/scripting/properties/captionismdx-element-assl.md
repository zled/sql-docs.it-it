---
title: Elemento CaptionIsMdx (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- CaptionIsMdx Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CaptionIsMdx
helpviewer_keywords:
- CaptionIsMdx element
ms.assetid: 7569a75e-b3e0-4332-97d3-585abc546ada
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2fa9ec5b26d80ccfe7522edceaa1544d682e165b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="captionismdx-element-assl"></a>Elemento CaptionIsMdx (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce se la didascalia per il [azione](../../../analysis-services/scripting/objects/action-element-assl.md) elemento è un'espressione MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <CaptionIsMdx>...</CaptionIsMdx>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|**False**|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento che corrisponde all'elemento padre **CaptionIsMdx** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
