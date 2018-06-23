---
title: Tempo elemento (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Time Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.time
- urn:schemas-microsoft-com:xml-analysis#Time
- http://schemas.microsoft.com/analysisservices/2003/engine#Time
helpviewer_keywords:
- Time element
ms.assetid: b74ba333-19e5-407d-92ab-3c429d4b3f45
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 9d8fc7f996f3c44fe0b890955d6a402038e08d2f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157809"
---
# <a name="time-element-xmla"></a>Elemento Time (XMLA)
  Specifica il limite di tempo utilizzato per il [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md) comando per progettare aggregazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DesignAggregations>  
   ...  
   <Time>...</Time>  
   ...  
</DesignAggregations>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Duration|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  