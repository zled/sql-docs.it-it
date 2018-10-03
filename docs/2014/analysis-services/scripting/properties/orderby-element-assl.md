---
title: Elemento OrderBy (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- OrderBy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OrderBy
helpviewer_keywords:
- OrderBy element
ms.assetid: d7a0564b-430e-44eb-913a-fe1f98917d0f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95ed1ce8e5b9df8340b41b8ec24e713dae9739ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168731"
---
# <a name="orderby-element-assl"></a>Elemento OrderBy (ASSL)
  Descrive in che modo ordinare i membri contenuti nell'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderBy>...</OrderBy>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nome*|  
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
|*Nome*|Ordina per nome del membro.|  
|*Key*|Ordina per chiave del membro.|  
|*AttributeKey*|Ordinare per chiave del membro dell'attributo specificato nel [OrderByAttributeID](id-element-assl.md) elemento `DimensionAttribute`.|  
|*AttributeName*|Ordina per nome del membro dell'attributo specificato nell'elemento `OrderByAttributeID` di `DimensionAttribute`.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `OrderBy` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.OrderBy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
