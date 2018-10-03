---
title: Elemento ReportParameter (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportParameter
helpviewer_keywords:
- ReportParameter element
ms.assetid: 653a5c64-f1af-4796-bb7b-b44a40e52901
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fdc677b6aabd9d07275b977dd3d3af3145ea00a8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093461"
---
# <a name="reportparameter-element-assl"></a>Elemento ReportParameter (ASSL)
  Contiene il nome e il valore di un parametro che viene passato a un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report in fase di esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ReportParameters>  
      <ReportParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportParameter>  
</ReportParameters>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ReportParameters](../collections/reportparameters-element-assl.md)|  
|Elementi figlio|[Nome](../properties/name-element-assl.md), [valore](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento `Value` deve contenere un'espressione MDX (Multidimensional Expressions).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ReportParameter>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ReportAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Elemento Action &#40;ASSL&#41;](action-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
