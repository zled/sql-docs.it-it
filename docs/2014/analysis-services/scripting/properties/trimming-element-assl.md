---
title: Elemento trimming (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Trimming Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Trimming
helpviewer_keywords:
- Trimming element
ms.assetid: 8b3bbf89-8309-4d00-9aea-a5918f0c7027
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 250394f67c79eec799f75dd0b6f590f6bff8f988
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198781"
---
# <a name="trimming-element-assl"></a>Elemento Trimming (ASSL)
  Specifica come i dati vengono rimossi dall'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataItem>  
   ...  
   <Trimming>...</Trimming>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Ok*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*A sinistra*|I dati vengono tagliati a sinistra.|  
|*Ok*|I dati vengono tagliati a destra.|  
|*LeftRight*|I dati vengono tagliati a sinistra e a destra.|  
|*Nessuno*|I dati non vengono tagliati.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Trimming` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.Trimming>.  
  
 L'elemento che corrisponde al padre di `Trimming` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
