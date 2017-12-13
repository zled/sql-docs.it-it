---
title: Il tipo di dati DataMiningMeasureGroupDimension (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataMiningMeasureGroupDimension Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DataMiningMeasureGroupDimension
helpviewer_keywords: DataMiningMeasureGroupDimension data type
ms.assetid: 56d5c2ec-7e03-4dc7-a668-c8d598d59e55
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7b321671e2527a74eca42c4607caea3b07e849f0
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="dataminingmeasuregroupdimension-data-type-assl"></a>Tipo di dati DataMiningMeasureGroupDimension (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce un tipo di dati derivato che rappresenta la relazione tra un gruppo di misure e una dimensione di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataMiningMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
      <CaseCubeDimensionID>...</CaseCubeDimensionID>  
</DataMiningMeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[MeasureGroupDimension](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[CaseCubeDimensionID](../../../analysis-services/scripting/properties/casecubedimensionid-element-assl.md)|  
|Elementi derivati|Vedere [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md) ([dimensioni](../../../analysis-services/scripting/collections/dimensions-element-assl.md) insieme di [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DataMiningMeasureGroupDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
