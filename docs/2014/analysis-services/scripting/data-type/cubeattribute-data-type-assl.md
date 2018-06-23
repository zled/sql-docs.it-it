---
title: Tipo di dati CubeAttribute (ASSL) | Documenti Microsoft
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
- CubeAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dce594145db99d7edfa991c2e975f62e55d3ef34
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067276"
---
# <a name="cubeattribute-data-type-assl"></a>Tipo di dati CubeAttribute (ASSL)
  Definisce un tipo di dati primitivo che rappresenta un attributo associato a un [cubo](../objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeAttribute>  
   <AttributeID>...</AttributeID>  
   <AggregationUsage>...</AggregationUsage>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <Annotations>...</Annotations>  
</CubeAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[AggregationUsage](../properties/aggregationusage-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../properties/enabled-element-assl.md), [AttributeHierarchyOptimizedState](../properties/state-element-assl.md), [ AttributeHierarchyVisible](../properties/visible-element-assl.md), [AttributeID](../properties/id-element-assl.md)|  
|Elementi derivati|[Attributo](../objects/attribute-element-assl.md) ([attributi](../collections/attributes-element-assl.md) insieme [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 Il *AttributeHierarchyOptimizedState* elemento non è supportato quando si esegue il servizio di configurazione DeploymentMode valori delle proprietà di 1 o 2 (modalità SharePoint o tabulare, utilizzata per eseguire PowerPivot e database modello tabulare).  
  
 Un attributo non può essere aggiunto come un livello di una gerarchia quando la proprietà *AtttributeHierarchyEnabled*, è impostato su FALSE e l'istanza in cui opera DeploymentMode 1 o 2 (modalità server SharePoint o tabulare).  
  
 Gli attributi nel [CubeDimension](dimension-data-type-assl.md) elemento che non sono inclusi in modo esplicito nel [attributi](../collections/attributes-element-assl.md) parte raccolta diventano della raccolta con i valori predefiniti assegnati. Dopo gli attributi vengono aggiunti alla raccolta, gli attributi possono essere restituiti tramite il [Discover](../../xmla/xml-elements-methods-discover.md) metodo.  
  
 Il [AggregationUsage](../properties/aggregationusage-element-assl.md) controlli elemento come [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] automaticamente progettare aggregazioni per l'attributo. L'elemento `AggregationUsage` non vincola alcuna aggregazione creata manualmente per il cubo.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  