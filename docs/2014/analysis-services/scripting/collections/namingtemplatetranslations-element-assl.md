---
title: Elemento NamingTemplateTranslations (ASSL) | Microsoft Docs
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
- NamingTemplateTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2965971734625c4d0c553f652160e1044eb48546
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204401"
---
# <a name="namingtemplatetranslations-element-assl"></a>Elemento NamingTemplateTranslations (ASSL)
  Fornisce una raccolta di conversioni localizzate per le [NamingTemplate](../properties/namingtemplate-element-assl.md) dell'elemento padre, [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <NamingTemplateTranslations>  
            <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
...</NamingTemplateTranslations>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributo](../objects/attribute-element-assl.md) di tipo [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|[NamingTemplateTranslation](../objects/translation-element-assl.md) di tipo [traduzione](translations-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 Il valore dei `NamingTemplateTranslation` elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore della [utilizzo](../properties/usage-element-dimensionattribute-assl.md) dell'elemento padre `DimensionAttribute` è impostata su *padre*.)  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
