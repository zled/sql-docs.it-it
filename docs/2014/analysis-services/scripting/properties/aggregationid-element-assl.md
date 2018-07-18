---
title: Elemento AggregationID (ASSL) | Microsoft Docs
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
- AggregationID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationID element
ms.assetid: 6056da1d-b6b4-4074-84db-45be719df49a
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fadf9884d769402e962c64ec00d86338a71328a0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277817"
---
# <a name="aggregationid-element-assl"></a>Elemento AggregationID (ASSL)
  Identifica la definizione di aggregazione dal [AggregationDesign](../objects/aggregationdesign-element-assl.md) elemento utilizzato per creare l'istanza di aggregazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationInstance>  
   ...  
   <AggregationID>...</AggregationID>  
   ...  
</AggregationInstance>  
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
|Elementi padre|[Elemento AggregationInstance](../objects/aggregationinstance-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Se questo elemento non è presente o è impostato su una stringa vuota, `AggregationInstance` rappresenta un'aggregazione definita dall'utente.  
  
 L'elemento che corrisponde al padre di `AggregationID` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
