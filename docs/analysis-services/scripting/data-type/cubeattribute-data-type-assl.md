---
title: Il tipo di dati CubeAttribute (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8724246e8c6b8a45669e28ee7671faf4e7dade74
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="cubeattribute-data-type-assl"></a>Tipo di dati CubeAttribute (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
