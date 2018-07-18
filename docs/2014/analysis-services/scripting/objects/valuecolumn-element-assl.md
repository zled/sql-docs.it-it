---
title: Elemento ValueColumn (ASSL) | Microsoft Docs
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
- ValueColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ValueColumn element
ms.assetid: 6c2d6822-8ecc-46df-9fa9-bb92ac716c36
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7279cb1f8f9bc5a7dc8c9e564081a227edc32f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231901"
---
# <a name="valuecolumn-element-assl"></a>Elemento ValueColumn (ASSL)
  Identifica la colonna che fornisce il valore dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <ValueColumn xsi:type="DataItem">...</ValueColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valore predefinito|Varies (see Remarks)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Se il [NameColumn](namecolumn-element-assl.md) elemento del `DimensionAttribute` viene specificato, lo stesso `DataItem` vengono utilizzati come valori predefiniti per il `ValueColumn` elemento. Se il `NameColumn` elemento della `DimensionAttribute` non viene specificato e il [KeyColumns](../collections/keycolumns-element-assl.md) raccolta di `DimensionAttribute` contiene una singola [KeyColumn](keycolumn-element-assl.md) elemento che rappresenta una colonna chiave con una stringa tipo di dati, lo stesso `DataItem` vengono utilizzati come valori predefiniti per il `ValueColumn` elemento.  
  
 Per altre informazioni sul `DataItem` tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà del `DataItem` del tipo, vedere [tipo di dati DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Gli elementi che corrispondono ai padri di `NameColumn` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.DimensionAttribute> e <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
