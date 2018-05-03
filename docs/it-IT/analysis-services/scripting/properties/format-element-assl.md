---
title: Formattare l'elemento (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Format Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Format
helpviewer_keywords:
- Format element
ms.assetid: 881ea707-52a7-46f7-ba16-ac2ec44eca22
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 659ced84363bdf483d88112bd67145a19c94bace
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="format-element-assl"></a>Elemento Format (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il formato richiesto del [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 I valori consentiti per il **formato** elemento sono formati Microsoft Office Excel e le stringhe *TrimRight*, *TrimLeft*, *TrimAll*, e *TrimNone*. Per il taglio *TrimRight* è l'impostazione predefinita.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|Qualsiasi stringa in formato Excel|I dati vengono formattati in base alla stringa di formato denominata o personalizzata specificata. È possibile specificare qualsiasi stringa di formato supportata da Excel.|  
|*TrimAll*|I dati vengono tagliati a sinistra e a destra.|  
|*TrimLeft*|I dati vengono tagliati a sinistra.|  
|*TrimNone*|I dati non vengono tagliati.|  
|*TrimRight*|I dati vengono tagliati a destra.|  
  
 L'elemento che corrisponde all'elemento padre **formato** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
