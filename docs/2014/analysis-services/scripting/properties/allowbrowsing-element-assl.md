---
title: Elemento AllowBrowsing (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AllowBrowsing Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllowBrowsing
helpviewer_keywords:
- AllowBrowsing element
ms.assetid: e5d09f8c-080b-4013-8c6a-0c9775e6ab25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 35e5c4450e250db41a6f09ce76ebb6f088e70f86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096421"
---
# <a name="allowbrowsing-element-assl"></a>Elemento AllowBrowsing (ASSL)
  Definisce se i membri di un [ruolo](../objects/role-element-assl.md) elemento dispone di autorizzazione per visualizzare un [MiningModel](../objects/miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModelPermission>  
      ...  
   <AllowBrowsing>...</AllowBrowsing>  
   ...  
</MiningModelPermission>  
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
|Elemento padre|[Elemento MiningModelPermission](../objects/miningmodelpermission-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `AllowBrowsing` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
