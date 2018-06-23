---
title: Elemento AttributeAllMemberTranslation (ASSL) | Documenti Microsoft
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
- AttributeAllMemberTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeAllMemberTranslation
helpviewer_keywords:
- AttributeAllMemberTranslation element
ms.assetid: 4b0c61dd-6666-4bf4-9b23-c9d8e315c414
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a93f67722e16034d256f4af16c582ef986b4b521
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169321"
---
# <a name="attributeallmembertranslation-element-assl"></a>Elemento AttributeAllMemberTranslation (ASSL)
  Contiene una traduzione per la didascalia del `All` membro di un [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeAllMemberTranslations>  
   <AttributeAllMemberTranslation xsi:type="Translation">...</AttributeAllMemberTranslation>  
</AttributeAllMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Conversione](../data-type/translation-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AttributeAllMemberTranslations](../collections/translations-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L’elemento che corrisponde al padre della raccolta `AttributeAllMemberTranslations` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Translation &#40;ASSL&#41;](translation-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  