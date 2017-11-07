---
title: Elemento ReportParameter (ASSL) | Documenti Microsoft
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
- ReportParameter Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ReportParameter
helpviewer_keywords:
- ReportParameter element
ms.assetid: 653a5c64-f1af-4796-bb7b-b44a40e52901
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fd3c4b4bd2224c928bcd7864bd797bea36a3d420
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="reportparameter-element---assl"></a>Elemento ReportParameter - ASSL
  Contiene il nome e il valore di un parametro passato a un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report in fase di esecuzione.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ReportParameters](../../../analysis-services/scripting/collections/reportparameters-element-assl.md)|  
|Elementi figlio|[Nome](../../../analysis-services/scripting/properties/name-element-assl.md), [valore](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **valore** elemento deve contenere un'espressione MDX (Multidimensional Expressions).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ReportParameter>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ReportAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Elemento Action &#40; ASSL &#41;](../../../analysis-services/scripting/objects/action-element-assl.md)   
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

