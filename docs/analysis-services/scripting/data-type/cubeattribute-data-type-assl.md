---
title: Il tipo di dati CubeAttribute (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CubeAttribute Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c04b5602de94ac46b736ebfc878760174ced5a8d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cubeattribute-data-type-assl"></a>Tipo di dati CubeAttribute (ASSL)
  Definisce un tipo di dati primitivo che rappresenta un attributo associato a un [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) elemento.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md), [AttributeHierarchyOptimizedState](../../../analysis-services/scripting/properties/attributehierarchyoptimizedstate-element-assl.md), [AttributeHierarchyVisible](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md), [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)|  
|Elementi derivati|[Attributo](../../../analysis-services/scripting/objects/attribute-element-assl.md) ([attributi](../../../analysis-services/scripting/collections/attributes-element-assl.md) insieme di [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 Il *AttributeHierarchyOptimizedState* elemento non è supportato quando si esegue il servizio, i valori di proprietà di configurazione DeploymentMode di 1 o 2 (modalità SharePoint o tabulare utilizzate per eseguire [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] e modello tabulare database).  
  
 Un attributo non può essere aggiunto come un livello di una gerarchia quando la proprietà, *AtttributeHierarchyEnabled*, è impostato su FALSE e l'istanza viene utilizzata in DeploymentMode 1 o 2 (modalità server SharePoint o tabulare).  
  
 Gli attributi nel [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md) elemento che non sono inclusi in modo esplicito nel [attributi](../../../analysis-services/scripting/collections/attributes-element-assl.md) parte raccolta diventano della raccolta con i valori predefiniti assegnati. Dopo aver aggiunto alla raccolta di attributi, gli attributi possono essere restituiti dal [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo.  
  
 Il [AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md) controlli elemento come [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] automaticamente progettare aggregazioni per l'attributo. Il **AggregationUsage** elemento vincola alcuna aggregazione creata manualmente per il cubo.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

