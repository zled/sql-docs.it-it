---
title: Elemento NullKeyConvertedToUnknown (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 95f8a31e4600b73901d692ca7472759a681d9006
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="nullkeyconvertedtounknown-element-assl"></a>Elemento NullKeyConvertedToUnknown (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*IgnoreError*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Si verificano errori di conversione di valori Null quando in una colonna chiave viene rilevato un valore Null, che viene interpretato come membro **Unknown** . Tuttavia, questo errore si verifica solo se il [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md) elemento per il [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md) predecessore del **ErrorConfiguration** elemento padre è impostato su  *UnknownMember*.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*IgnoreError*|L'errore viene ignorato e l'elaborazione prosegue.|  
|*ReportAndContinue*|L'errore viene segnalato e l'elaborazione prosegue.|  
|*ReportAndStop*|L'errore viene segnalato e l'elaborazione viene arrestata.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **NullKeyConvertedToUnknown** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ErrorConfiguration & #40; ASSL & #41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
