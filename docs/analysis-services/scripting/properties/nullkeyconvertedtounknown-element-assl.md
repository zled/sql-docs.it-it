---
title: Elemento NullKeyConvertedToUnknown (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: NullKeyConvertedToUnknown Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: NullKeyConvertedToUnknown
helpviewer_keywords: NullKeyConvertedToUnknown element
ms.assetid: 1a6cde33-01ba-4095-b464-16d1ad3c6905
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: da985c222a0e5bb6fa36fe1ed0f102e7d79fa547
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="nullkeyconvertedtounknown-element-assl"></a>Elemento NullKeyConvertedToUnknown (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Specifica l'azione da intraprendere quando viene rilevato un errore di conversione di valori null.  
  
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
 [Elemento ErrorConfiguration &#40; ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
