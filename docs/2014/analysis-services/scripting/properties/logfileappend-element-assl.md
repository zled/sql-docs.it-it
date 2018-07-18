---
title: Elemento LogFileAppend (ASSL) | Microsoft Docs
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
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4cd2f873b3d7394dac45a1a40b9b98483118f44
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190911"
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
  
  
