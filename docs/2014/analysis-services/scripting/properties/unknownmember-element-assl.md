---
title: Elemento UnknownMember (ASSL) | Documenti Microsoft
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
- UnknownMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- UnknownMember
helpviewer_keywords:
- UnknownMember element
ms.assetid: 5558961e-e3c6-4f4e-817d-5b12b0734c03
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 85bc7a517642ccc5b4386f65e7b4a9c89d757ce6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063916"
---
# <a name="unknownmember-element-assl"></a>Elemento UnknownMember (ASSL)
  Indica se il membro sconosciuto è visibile.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMember>...</UnknownMember>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Dimension](../objects/dimension-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Visibile*|Il membro sconosciuto esiste ed è visualizzato.|  
|*Nascosto*|Il membro sconosciuto esiste ma non è visualizzato.|  
|*Nessuno*|Il membro sconosciuto non è utilizzato.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `UnknownMember` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.UnknownMemberBehavior>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento UnknownMemberName &#40;ASSL&#41;](name-element-assl.md)   
 [Elemento UnknownMemberTranslation &#40;ASSL&#41;](../objects/translation-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  