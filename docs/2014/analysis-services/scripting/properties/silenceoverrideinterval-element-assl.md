---
title: Elemento SilenceOverrideInterval (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SilenceOverrideInterval Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SilenceOverrideInterval
helpviewer_keywords:
- SilenceOverrideInterval element
ms.assetid: 0dcd2db4-9bc0-4460-b1dd-def0b38c4617
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba345f4d7ebe21af3c2ff79739f3badf89da03d4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192491"
---
# <a name="silenceoverrideinterval-element-assl"></a>Elemento SilenceOverrideInterval (ASSL)
  Definisce la quantità di tempo che deve trascorrere dopo avere ricevuto la notifica iniziale prima dell'inizio incondizionato della creazione di immagini OLAP multidimensionale (MOLAP).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <SilenceOverrideInterval>...</SilenceOverrideInterval>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|duration|  
|Valore predefinito|P0s|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di `SilenceOverrideInterval` prevale sul valore di `SilenceInterval` se durante il periodo di inattività viene ricevuta una notifica.  
  
 L'elemento che corrisponde al padre di `SilenceOverrideInterval` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
