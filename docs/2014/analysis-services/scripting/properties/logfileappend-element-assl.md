---
title: Elemento LogFileAppend (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- LogFileAppend Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LogFileAppend
helpviewer_keywords:
- LogFileAppend element
ms.assetid: f85e94a9-e5c5-478a-a5a0-fc99ed19b582
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bea470af9f145be58e9a6e0d2645f2173097a587
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200451"
---
# <a name="logfileappend-element-assl"></a>Elemento LogFileAppend (ASSL)
  Determina se il [traccia](../objects/trace-element-assl.md) elemento aggiunge la registrazione restituita al file di log esistente o lo sovrascrive.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Trace>  
  
   <LogFileAppend>...</LogFileAppend>  
  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|False|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Traccia](../objects/trace-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `LogFileAppend` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analizza l'elemento &#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
