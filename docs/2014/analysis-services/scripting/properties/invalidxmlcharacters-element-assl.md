---
title: Elemento InvalidXmlCharacters (ASSL) | Microsoft Docs
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
- InvalidXmlCharacters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- InvalidXmlCharacters
helpviewer_keywords:
- InvalidXmlCharacters element
ms.assetid: 92b1210c-1075-4f2f-a2c4-dfdc6d7e5c05
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a3735beb602045bc4789d716bdf1cb5968af06f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229671"
---
# <a name="invalidxmlcharacters-element-assl"></a>Elemento InvalidXmlCharacters (ASSL)
  Specifica il metodo di gestione per i caratteri di XML nei dati di origine che non sono validi.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataItem>  
   ...  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
   ...  
</DataItem  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Mantenere*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Mantenere*|I caratteri XML non validi vengono mantenuti.|  
|*Rimuovi*|I caratteri XML non validi vengono rimossi.|  
|*Sostituisci*|I caratteri XML non validi sono sostituiti con caratteri punto interrogativo (?)|  
  
 L'enumerazione che corrisponde ai valori consentiti di `InvalidXmlCharacters` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.InvalidXmlCharacters>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
