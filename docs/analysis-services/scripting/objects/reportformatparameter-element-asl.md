---
title: Elemento ReportFormatParameter (ASSL) | Documenti Microsoft
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
- ReportFormatParameter Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ReportFormatParameter
helpviewer_keywords:
- ReportFormatParameter element
ms.assetid: 064a8683-c44b-4261-be4d-32226d3d3119
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0c5717a4f1896e42c35d035a6b91438bed998ae3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="reportformatparameter-element---asl"></a>Elemento ReportFormatParameter - ASL
  Contiene il nome e il valore di un parametro che specifica come un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report formattato in fase di esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ReportFormatParameters>  
   <ReportFormatParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportFormatParameter>  
</ReportFormatParameters>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Reportformatparameter](../../../analysis-services/scripting/collections/reportformatparameters-element-assl.md)|  
|Elementi figlio|[Nome](../../../analysis-services/scripting/properties/name-element-assl.md), [valore](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento che corrisponde all'elemento padre **ReportFormatParameter** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ReportAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Elemento Action &#40; ASSL &#41;](../../../analysis-services/scripting/objects/action-element-assl.md)   
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
