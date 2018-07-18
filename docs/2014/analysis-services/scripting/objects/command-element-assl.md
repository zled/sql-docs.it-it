---
title: Comando elemento (ASSL) | Microsoft Docs
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
- Command Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Command
helpviewer_keywords:
- Command element
ms.assetid: 277598b5-9939-4d7f-8c75-06470c3fabdd
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a9e59c50341f3ad0e517f64b67c0189a0614d57
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249091"
---
# <a name="command-element-assl"></a>Elemento Command (ASSL)
  Definisce un comando che è disponibile per l'uso all'interno del contesto dell'elemento padre del [comandi](../collections/commands-element-assl.md) raccolta.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Commands>  
   <Command>  
      <Text>...</Text>  
   </Command>  
</Commands >  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Comandi](../collections/commands-element-assl.md)|  
|Elementi figlio|[Text](../properties/text-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Command>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
