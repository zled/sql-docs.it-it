---
title: Elemento AllMemberTranslation (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c46039bcf1d72014a12ee791484cacc205ed1f16
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031892"
---
# <a name="allmembertranslation-element-assl"></a>Elemento AllMemberTranslation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene una traduzione per la didascalia del membro totale di un [gerarchia](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AllMemberTranslations>  
   <AllMemberTranslation xsi:type="Translation">...  
   </AllMemberTranslation>  
</AllMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Conversione](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[AllMemberTranslations](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento che corrisponde all'elemento padre di **AllMemberTranslations** insieme nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Translation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [Elemento Hierarchy &#40;ASSL&#41;](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
