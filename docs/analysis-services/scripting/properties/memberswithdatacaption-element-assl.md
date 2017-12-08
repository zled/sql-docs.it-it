---
title: Elemento MembersWithDataCaption (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MembersWithDataCaption Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MembersWithDataCaption
helpviewer_keywords: MembersWithDataCaption element
ms.assetid: a5d59efd-5d67-485b-a360-67d54a1fe394
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 07e44daf6556a357e9d84b997ecb4a476b85f5aa
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="memberswithdatacaption-element-assl"></a>Elemento MembersWithDataCaption (ASSL)
  Fornisce una stringa modello usata per la creazione di didascalie per i membri dei dati generati dal sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeTranslation> <!-- or DimensionAttribute -->  
   ...  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   ...  
</AttributeTranslation>  
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
|Elementi padre|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore della **MembersWithDataCaption** elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore del [utilizzo](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) elemento del **DimensionAttribute** padre elemento è impostato su *padre*) per determinare la didascalia di membri di dati nell'attributo padre. Per altre informazioni sui membri dei dati, vedere [Attributi nelle gerarchie padre-figlio](../../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md).  
  
 Gli elementi che corrispondono ai padri di **MembersWithDataCaption** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.AttributeTranslation> e <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MembersWithData &#40; ASSL &#41;](../../../analysis-services/scripting/properties/memberswithdata-element-assl.md)   
 [Tipo di dati AttributeTranslation &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
