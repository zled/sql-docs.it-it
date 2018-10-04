---
title: Elemento Reportformatparameter (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportFormatParameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportFormatParameters
helpviewer_keywords:
- ReportFormatParameters element
ms.assetid: f2e677bf-7b6b-4ce4-b0ec-75a4999306c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 298357fffbbf2fed441a86d7d0e1ad211eef1c3c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171611"
---
# <a name="reportformatparameters-element-assl"></a>Elemento ReportFormatParameter (ASSL)
  Contiene la raccolta di elementi [ReportFormatParameter](../objects/reportformatparameter-element-asl.md) per un elemento [ReportAction](../data-type/action-data-type-assl.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action xsi:type="ReportAction">  
   ...  
   <ReportFormatParameters>  
      <ReportFormatParameter>...</ReportFormatParameter>  
   </ReportFormatParameters>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Action](../objects/action-element-assl.md) di tipo [ReportAction](../data-type/action-data-type-assl.md)|  
|Elementi figlio|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `ReportFormatParameters` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
