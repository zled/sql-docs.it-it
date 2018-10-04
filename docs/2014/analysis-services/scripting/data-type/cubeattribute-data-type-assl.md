---
title: Tipo di dati CubeAttribute (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d64224c1b7489895ff0d9dca00a3841be0ed0bbc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203301"
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
  
## <a name="remarks"></a>Note  
 Il *AttributeHierarchyOptimizedState* elemento non è supportato quando si esegue il servizio di configurazione DeploymentMode valori delle proprietà di 1 o 2 (modalità SharePoint o tabulare, usata per eseguire PowerPivot e database modello tabulare).  
  
 Non è possibile aggiungere un attributo come livello di una gerarchia quando la proprietà *AtttributeHierarchyEnabled*, è impostato su FALSE e l'istanza viene utilizzata in DeploymentMode 1 o 2 (modalità server SharePoint o tabulare).  
  
 Attributi inclusi nel [CubeDimension](dimension-data-type-assl.md) elemento che non sono inclusi in modo esplicito nel [attributi](../collections/attributes-element-assl.md) parte raccolta diventano della raccolta con i valori predefiniti assegnati. Dopo che gli attributi vengono aggiunti alla raccolta, gli attributi possono essere restituiti tramite il [Discover](../../xmla/xml-elements-methods-discover.md) (metodo).  
  
 Il [AggregationUsage](../properties/aggregationusage-element-assl.md) controlli elemento modo [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] automaticamente progettare aggregazioni per l'attributo. L'elemento `AggregationUsage` non vincola alcuna aggregazione creata manualmente per il cubo.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
