---
title: Tipo di dati MeasureGroupAttributeBinding (out-of-line) (ASSL) | Documenti Microsoft
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
- MeasureGroupAttributeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MeasureGroupAttributeBinding data type
ms.assetid: bfe09a95-4e04-4f93-9389-7dd0b4c8f5e4
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5bb43dfc9dc6cb0ac578c36a24b470d444630d01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168885"
---
# <a name="measuregroupattributebinding-data-type-out-of-line-assl"></a>Tipo di dati MeasureGroupAttributeBinding (out-of-line) (ASSL)
  Definisce un tipo di dati derivato che rappresenta un'associazione out-of-line per un attributo in una dimensione incluso in un gruppo di misure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroupAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <GranularityAttributeID>...</GranularityAttributeID>  
   <Source>...</Source>  
</MeasureGroupAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Associazione](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[CubeID](../properties/id-element-assl.md), [DatabaseID](../../xmla/xml-elements-properties/id-element-xmla.md), [MeasureGroupID](../properties/measuregroupid-element-assl.md), [GranularityAttributeID](../properties/attributeid-element-assl.md), [origine](../properties/source-element-binding-assl.md)|  
|Elementi derivati|[Binding](../../xmla/xml-elements-properties/binding-element-xmla.md) ([associazioni](../collections/attributes-element-assl.md) raccolta di XML for Analysis (XMLA) [Batch](../../xmla/xml-elements-commands/batch-element-xmla.md) e [processo](../../xmla/xml-elements-commands/process-element-xmla.md) comandi)|  
  
## <a name="remarks"></a>Remarks  
 Per ulteriori informazioni sulle associazioni out-of-line, vedere [origini dati e le associazioni &#40;multidimensionali SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  