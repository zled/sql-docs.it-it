---
title: Formattare l'elemento (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 344730d6f46a3772252a91d6672f44b7f54e1123
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
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
  
  
