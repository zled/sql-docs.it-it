---
title: Elemento NullKeyNotAllowed (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NullKeyNotAllowed Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullKeyNotAllowed
helpviewer_keywords:
- NullKeyNotAllowed element
ms.assetid: 4ece99eb-954b-4da1-add4-dd9efd5fff0a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0d17edc031d66282b433571b18ef1c32cf6e09bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054571"
---
# <a name="nullkeynotallowed-element-assl"></a>Elemento NullKeyNotAllowed (ASSL)
  Determina come il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] motore di elaborazione gestisce un errore di chiave null rilevato durante l'elaborazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ErrorConfiguration>  
   ...  
   <NullKeyNotAllowed>...</NullKeyNotAllowed>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ReportAndContinue*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Si verificano errori di chiave Null quando in una colonna chiave in cui non sono consentiti valori Null ne viene rilevato uno, che fa sì che il record venga ignorato durante l'elaborazione. Tuttavia, questo errore si verifica solo se il [NullProcessing](nullprocessing-element-assl.md) (elemento) per il `DataItem` predecessore del `ErrorConfiguration` elemento padre è impostato su *errore*.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*IgnoreError*|L'errore viene ignorato e l'elaborazione prosegue.|  
|*ReportAndContinue*|L'errore viene segnalato e l'elaborazione prosegue.|  
|*ReportAndStop*|L'errore viene segnalato e l'elaborazione viene arrestata.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `NullKeyNotAllowed` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ErrorConfiguration &#40;ASSL&#41;](../objects/errorconfiguration-element-assl.md)  
  
  
