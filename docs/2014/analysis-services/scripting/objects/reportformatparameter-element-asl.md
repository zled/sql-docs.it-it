---
title: Elemento ReportFormatParameter (ASSL) | Microsoft Docs
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
- ReportFormatParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportFormatParameter
helpviewer_keywords:
- ReportFormatParameter element
ms.assetid: 064a8683-c44b-4261-be4d-32226d3d3119
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dfcc98e3abe60296e7ee28b57bc54fe89f5c2abe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245581"
---
# <a name="reportformatparameter-element-assl"></a>Elemento ReportFormatParameter (ASSL)
  Contiene il nome e il valore di un parametro che specifica come un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report viene formattato in fase di esecuzione.  
  
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ReportFormatParameters](../collections/reportformatparameters-element-assl.md)|  
|Elementi figlio|[Nome](../properties/name-element-assl.md), [valore](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `ReportFormatParameter` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ReportAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Elemento Action &#40;ASSL&#41;](action-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
