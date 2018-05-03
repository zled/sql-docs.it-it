---
title: Abilitato elemento (ASSL) | Documenti Microsoft
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
- Enabled Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Enabled
helpviewer_keywords:
- Enabled element
ms.assetid: dbe57903-75c0-4060-a2b3-eab241d7469f
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 30ae979d5c3a003fe0d3c2e566bf4cc116ea7386
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="enabled-element-assl"></a>Elemento Enabled (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indica se l'elemento padre è abilitato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeHierarchy> <!-- or ProactiveCaching -->  
   ...  
   <Enabled>...</Enabled>  
   ...  
</CubeHierarchy>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|True|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md), [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi che corrispondono ai padri di **abilitato** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.CubeHierarchy> e <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
