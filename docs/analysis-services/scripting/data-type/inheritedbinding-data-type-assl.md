---
title: Tipo di dati InheritedBinding (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
apiname: InheritedBinding Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: InheritedBinding
helpviewer_keywords: InheritedBinding data type
ms.assetid: a61f58c5-62d6-44e8-a02f-db2b17d1f256
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae69c7b5fed1c22ce5f3a271286756fe97880e6f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="inheritedbinding-data-type-assl"></a>Tipo di dati InheritedBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce un tipo di dati derivato che indica che un [MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md) elemento eredita le associazioni dall'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<InheritedBinding>...</InheritedBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[Associazione](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|Nessuno|  
|Elementi derivati|Vedere [associazione](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sul **associazione** tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del **associazione** tipo e la gerarchia di ereditarietà dei  **Associazione** tipi, vedere [associazione tipo di dati &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md) elemento.  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e associazioni &#40; SSAS multidimensionale &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.InheritedBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Origini dati e associazioni &#40; SSAS multidimensionale &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
