---
title: Elemento Annotation (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Annotation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Annotation
helpviewer_keywords:
- Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c8c8b70e9e15e01a0864cd9f3491aa188be6777
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103401"
---
# <a name="annotation-element-assl"></a>Elemento Annotation (ASSL)
  Contiene elementi utilizzati per estendere lo schema ASSL (Analysis Services Scripting Language).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Annotations>  
   <Annotation>  
      <Name>...</Name>  
      <Visibility>...</Visibility>  
      <Value>...</Value>  
   </Annotation>  
</Annotations >  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Annotazioni](../collections/annotations-element-assl.md)|  
|Elementi figlio|[Nome](../properties/name-element-assl.md), [valore](../properties/value-element-assl.md), [visibilità](../properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento `Annotation` fornisce estensibilità dello schema ASSL per tutti gli oggetti ad esclusione di quelli utilizzati esclusivamente per definire un tipo di dati complesso. L'elemento `Value` dell'elemento `Annotation` può contenere valori XML validi di qualsiasi spazio dei nomi XML diverso da ASSL, soggetti alle regole seguenti:  
  
-   Il valore XML può contenere solo elementi.  
  
-   Ogni elemento deve avere un nome univoco. È consigliabile che il valore dell'elemento `Name` dell'elemento `Annotation` faccia riferimento allo spazio dei nomi di destinazione.  
  
 Queste regole vengono imposte per consentire l'esposizione dei contenuti dell'elemento `Annotation` come set di coppie nome/valore tramite altre interfacce, ad esempio DSO (Decision Support Objects).  
  
 I commenti e gli spazi vuoti all'interno dell'elemento `Annotation` non inclusi in un elemento figlio non possono essere mantenuti. Tutti gli elementi devono inoltre essere di lettura/scrittura. Gli elementi di sola lettura vengono ignorati.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
