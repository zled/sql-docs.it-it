---
title: Elemento NamingTemplateTranslation (ASSL) | Documenti Microsoft
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
- NamingTemplateTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dc6c6689f4028c0983267a38435c76e7258768a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157238"
---
# <a name="namingtemplatetranslation-element-assl"></a>Elemento NamingTemplateTranslation (ASSL)
  Fornisce una versione localizzata del [NamingTemplate](../properties/namingtemplate-element-assl.md) elemento per un elemento padre [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Conversione](translation-element-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[NamingTemplateTranslations](../collections/translations-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore della `NamingTemplateTranslation` elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore del [utilizzo](../properties/usage-element-dimensionattribute-assl.md) elemento del `DimensionAttribute` padre è impostato su *padre*) per archiviare versione localizzata conversione del `NamingTemplate` valore per una determinata lingua.  
  
 L'elemento che corrisponde al padre di `NamingTemplateTranslations` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento NamingTemplate &#40;ASSL&#41;](../properties/namingtemplate-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  