---
title: Elemento AggregationID (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregationID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AggregationID element
ms.assetid: 6056da1d-b6b4-4074-84db-45be719df49a
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f6558e3709315b8dc775f76610e207d923641466
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="aggregationid-element-assl"></a>Elemento AggregationID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifica la definizione di aggregazione dal [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) elemento utilizzato per creare l'istanza di aggregazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationInstance>  
   ...  
   <AggregationID>...</AggregationID>  
   ...  
</AggregationInstance>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Se questo elemento non è presente o è impostato su una stringa vuota, **AggregationInstance** rappresenta un'aggregazione definita dall'utente.  
  
 L'elemento che corrisponde all'elemento padre **AggregationID** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
