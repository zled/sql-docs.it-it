---
title: Elemento MeasureGroupID (ASSL) | Documenti Microsoft
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
- MeasureGroupID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MeasureGroupID
helpviewer_keywords:
- MeasureGroupID element
ms.assetid: 3b075f86-dbbc-4285-8d2d-61fa722181c7
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2f34c9680c28598177ef5c4eff75ae26cb121e41
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="measuregroupid-element-assl"></a>Elemento MeasureGroupID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Associa un [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) con l'elemento padre, associazione o associazione out-of-line.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ManyToManyMeasureGroupDimension> <!-- or MeasureGroupAttributeBinding, MeasureGroupBinding, PerspectiveMeasureGroup -->  
   ...  
   <MeasureGroupID>...</MeasureGroupID>  
   ...  
</ManyToManyMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Cardinalità|  
|------------------------|-----------------|  
|[ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md)|0-1: elemento facoltativo che può ricorrere una sola volta.|  
|[MeasureGroupAttributeBinding](../../../analysis-services/scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md) e [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md), [MeasureGroupAttributeBinding](../../../analysis-services/scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md), [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi che corrispondono ai padri di **MeasureGroupID** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding>, e <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
