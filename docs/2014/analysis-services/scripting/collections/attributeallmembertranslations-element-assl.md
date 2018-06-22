---
title: Elemento AttributeAllMemberTranslations (ASSL) | Documenti Microsoft
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
- AttributeAllMemberTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeAllMemberTranslations
helpviewer_keywords:
- AttributeAllMemberTranslations element
ms.assetid: 1a0d86ea-d95d-4d93-b321-acd35ed4ac26
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fa787c7c3731962690c1b8d25e736f061caf74e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062988"
---
# <a name="attributeallmembertranslations-element-assl"></a>Elemento AttributeAllMemberTranslations (ASSL)
  Contiene la raccolta di traduzioni per la didascalia del membro Totale della dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension>  
   ...  
   <AttributeAllMemberTranslations>  
      <AttributeAllMemberTranslation xsi:type="Translation">...</AttributeAllMemberTranslation>  
   </AttributeAllMemberTranslations>  
      ...  
</Dimension>  
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
|Elementi padre|[Dimension](../objects/dimension-element-assl.md)|  
|Elementi figlio|[AttributeAllMemberTranslation](../objects/translation-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 L'elemento che corrisponde al padre di `AttributeAllMemberTranslations` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Translation &#40;ASSL&#41;](translations-element-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  