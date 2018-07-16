---
title: Elemento AggregationInstanceSource (ASSL) | Microsoft Docs
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
- AggregationInstanceSource Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstanceSource element
ms.assetid: ab58c817-eb2b-4974-8470-2946ca5affea
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cd2001d304d951f4eeb2ac737e3cfe6e8526c1af
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312411"
---
# <a name="aggregationinstancesource-element-assl"></a>Elemento AggregationInstanceSource (ASSL)
  Identifica l'origine dei dati per le istanze di aggregazione definite dall'utente associate a un [partizione](../objects/partition-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Partition>  
   ...  
   <AggregationInstanceSource xsi:type="DataSourceViewBinding">...</AggregationInstanceSource>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataSourceViewBinding](../data-type/binding-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Se questo elemento è mancante o impostato su una stringa vuota, viene utilizzata per impostazione predefinita la vista origine dati del cubo che possiede la partizione.  
  
 Per altre informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL&#41;](../data-type/binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
