---
title: Formato elemento (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Format Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Format
helpviewer_keywords:
- Format element
ms.assetid: 881ea707-52a7-46f7-ba16-ac2ec44eca22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ed7cf229d4ef65e324a59d2d9292948ae530147
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228011"
---
# <a name="format-element-assl"></a>Elemento Format (ASSL)
  Contiene il formato richiesto del [DataItem](../data-type/dataitem-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Note  
 I valori consentiti per il `Format` elemento sono formati di Microsoft Office Excel e le stringhe *TrimRight*, *TrimLeft*, *TrimAll*, e  *TrimNone*. Per il taglio *TrimRight* è il valore predefinito.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|Qualsiasi stringa in formato Excel|I dati vengono formattati in base alla stringa di formato denominata o personalizzata specificata. È possibile specificare qualsiasi stringa di formato supportata da Excel.|  
|*TrimAll*|I dati vengono tagliati a sinistra e a destra.|  
|*TrimLeft*|I dati vengono tagliati a sinistra.|  
|*TrimNone*|I dati non vengono tagliati.|  
|*TrimRight*|I dati vengono tagliati a destra.|  
  
 L'elemento che corrisponde al padre di `Format` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
