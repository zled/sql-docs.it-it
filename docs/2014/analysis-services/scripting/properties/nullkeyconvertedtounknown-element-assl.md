---
title: Elemento NullKeyConvertedToUnknown (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NullKeyConvertedToUnknown Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullKeyConvertedToUnknown
helpviewer_keywords:
- NullKeyConvertedToUnknown element
ms.assetid: 1a6cde33-01ba-4095-b464-16d1ad3c6905
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6aaf78e4081b0f2fe04bf9b4037639f5b86f5311
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121721"
---
# <a name="nullkeyconvertedtounknown-element-assl"></a>Elemento NullKeyConvertedToUnknown (ASSL)
  Specifica l'azione da intraprendere quando si verifica un errore di conversione null.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*IgnoreError*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Si verificano errori di conversione di valori Null quando in una colonna chiave viene rilevato un valore Null, che viene interpretato come membro `Unknown`. Tuttavia, questo errore si verifica solo se il [NullProcessing](nullprocessing-element-assl.md) (elemento) per il [DataItem](../data-type/dataitem-data-type-assl.md) predecessore del `ErrorConfiguration` elemento padre è impostato su *UnknownMember*.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*IgnoreError*|L'errore viene ignorato e l'elaborazione prosegue.|  
|*ReportAndContinue*|L'errore viene segnalato e l'elaborazione prosegue.|  
|*ReportAndStop*|L'errore viene segnalato e l'elaborazione viene arrestata.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `NullKeyConvertedToUnknown` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ErrorConfiguration &#40;ASSL&#41;](../objects/errorconfiguration-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
