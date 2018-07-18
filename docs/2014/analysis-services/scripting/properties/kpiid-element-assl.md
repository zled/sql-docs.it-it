---
title: Elemento KpiID (ASSL) | Microsoft Docs
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
- KpiID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KpiID
helpviewer_keywords:
- KpiID element
ms.assetid: a76395bc-bc84-40f8-9770-6275842f93b5
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1f363564a74e9f64ed126ceda98ca387561c852
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151272"
---
# <a name="kpiid-element-assl"></a>Elemento KpiID (ASSL)
  Contiene un identificatore (ID) che associa un [Kpi](../objects/kpi-element-assl.md) elemento con un [prospettiva](../objects/perspective-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<PerspectiveKpi>  
      ...  
   <KpiID>...</KpiID>  
   ...  
</PerspectiveKpi>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Elemento PerspectiveKpi](../data-type/perspectivekpi-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `KpiID` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.PerspectiveKpi>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà (ASSL)](properties-assl.md)  
  
  
