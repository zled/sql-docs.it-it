---
title: Elemento Application (ASSL) | Microsoft Docs
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
- Application Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Application
helpviewer_keywords:
- Application element
ms.assetid: dfd780ad-f643-4a1c-b58b-34271ae91240
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e04ce46a9fc2797885e3c8dff0acd697a782b95a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279497"
---
# <a name="application-element-assl"></a>Elemento Application (ASSL)
  Identifica l'applicazione associata a un [azione](../objects/action-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <Application>...</Application>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../objects/action-element-assl.md) o uno degli elementi derivati: [DrillThroughAction](../data-type/action-data-type-assl.md), [ReportAction](../data-type/reportaction-data-type-assl.md), [StandardAction](../data-type/standardaction-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `Application` può essere utilizzato dalle applicazioni client per determinare quali azioni sono applicabili a un'applicazione client specificata. L'applicazione client è responsabile per la valutazione del valore di questo elemento.  
  
 L'elemento che corrisponde al padre di `Application` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Actions &#40;ASSL&#41;](../collections/actions-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
