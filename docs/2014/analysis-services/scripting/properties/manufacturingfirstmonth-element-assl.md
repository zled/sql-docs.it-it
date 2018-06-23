---
title: Elemento ManufacturingFirstMonth (ASSL) | Documenti Microsoft
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
- ManufacturingFirstMonth Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ManufacturingFirstMonth
helpviewer_keywords:
- ManufacturingFirstMonth element
ms.assetid: 3b2fb440-662b-4d88-a133-1e098b9c8169
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c14ca57b15ee4c3a80bf415ca6646f1818bf1a4c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171151"
---
# <a name="manufacturingfirstmonth-element-assl"></a>Elemento ManufacturingFirstMonth (ASSL)
  Definisce il primo mese di produzione per un [TimeBinding](../data-type/binding-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TimeBinding>  
   ...  
   <ManufacturingFirstMonth>...</ManufacturingFirstMonth>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Integer (da 1 a 12, dove 1 = gennaio e 12 = dicembre)|  
|Valore predefinito|`1`|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'elemento che corrisponde al padre di `ManufacturingFirstMonth` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  