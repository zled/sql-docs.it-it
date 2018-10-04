---
title: Tipo di dati AttributeTranslation (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeTranslation Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeTranslation
helpviewer_keywords:
- AttributeTranslation data type
ms.assetid: a0e29941-ef08-42ad-ab9c-b2efd7910895
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c291316b335cfeca258f9cb7373e2ec4029b551d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068771"
---
# <a name="attributetranslation-data-type-assl"></a>Tipo di dati AttributeTranslation (ASSL)
  Definisce un tipo di dati derivato che rappresenta una traduzione associata a un [attributo](../objects/attribute-element-assl.md) elemento  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeTranslation>  
   <!-- The following elements extend Translation -->  
   <CaptionColumn>...</CaptionColumn>  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
</AttributeTranslation>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Traduzione](translation-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[CaptionColumn](../objects/column-element-assl.md), [MembersWithDataCaption](../properties/caption-element-assl.md)|  
|Elementi derivati|Visualizzare [Translation](../objects/translation-element-assl.md) ([traduzioni](../collections/translations-element-assl.md) raccolta di [DimensionAttribute](dimensionattribute-data-type-assl.md) oppure [ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AttributeTranslation>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
