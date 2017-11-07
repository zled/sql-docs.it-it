---
title: Elemento MembersWithData (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MembersWithData Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e699a61dafb6f7bf9274fdf76dda5cdc0694c3dd
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="memberswithdata-element-assl"></a>Elemento MembersWithData (ASSL)
  Determina se visualizzare i membri dei dati per i membri non foglia nell'attributo padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <MembersWithData>...</MembersWithData>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*NonLeafDataVisible*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore della **MembersWithData** elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore del [utilizzo](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) elemento del **DimensionAttribute** elemento padre è impostato su *padre*) per determinare se visualizzare i membri di dati per membri non foglia nell'attributo padre. Per altre informazioni sui membri dei dati, vedere [Attributi nelle gerarchie padre-figlio](../../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md).  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*NonLeafDataHidden*|I dati non foglia sono nascosti.|  
|*NonLeafDataVisible*|I dati non foglia sono visibili.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **MembersWithData** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MembersWithData>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MembersWithDataCaption &#40; ASSL &#41;](../../../analysis-services/scripting/properties/memberswithdatacaption-element-assl.md)   
 [Tipo di dati DimensionAttribute &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

