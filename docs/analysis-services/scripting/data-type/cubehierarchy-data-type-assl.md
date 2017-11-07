---
title: Il tipo di dati CubeHierarchy (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CubeHierarchy Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeHierarchy
helpviewer_keywords:
- CubeHierarchy data type
ms.assetid: cd633409-0c14-4dd9-97cc-3d30e25df24f
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd9a671ff65eae1be83be7b21b7230f37a09dde2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cubehierarchy-data-type-assl"></a>Tipo di dati CubeHierarchy (ASSL)
  Definisce un tipo di dati primitivo che rappresenta le informazioni su un [gerarchia](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) elemento in un [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CubeHierarchy>   <HierarchyID>...</HierarchyID>   <Name>...</Name>   <OptimizedState>...</OptimizedState>   <Visible>...</Visible>   <Enabled>...</Enabled>   <Annotations>...</Annotations></CubeHierarchy>  
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
|Elementi figlio|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [abilitato](../../../analysis-services/scripting/properties/enabled-element-assl.md), [HierarchyID](../../../analysis-services/scripting/properties/hierarchyid-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [OptimizedState](../../../analysis-services/scripting/properties/optimizedstate-element-assl.md), [visibile](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
|Elementi derivati|[Gerarchia](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) ([gerarchie](../../../analysis-services/scripting/collections/hierarchies-element-assl.md) insieme di [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 Questo tipo di dati non presenta alcuna restrizione e può essere utilizzato in qualsiasi modalità di distribuzione: 0-Multidimensionale e Data Mining, 1-SharePoint e 2-Tabulare.  
  
 In SQL Server 2016 Analysis Services e versioni successive, il *abilitato* proprietà non può essere impostata su **False** per *CubeHierarchy*.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeHierarchy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Individuare metodo &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

