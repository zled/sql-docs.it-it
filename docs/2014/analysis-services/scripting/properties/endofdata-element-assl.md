---
title: Elemento EndOfData (ASSL) | Microsoft Docs
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
- EndOfData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EndOfData
helpviewer_keywords:
- EndOfData element
ms.assetid: 4cee48bc-d486-4125-9d65-f323c6ec9d09
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1640b052f72e28790a131ddd63eecaa833ced52a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285957"
---
# <a name="endofdata-element-assl"></a>Elemento EndOfData (ASSL)
  Indica la fine dei dati ricevuti da un [PushedDataSource](../data-type/datasource-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<PushedDataSource>  
   ...  
   <EndOfData>...</EndOfData>  
   ...  
</PushedDataSource  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[PushedDataSource](../data-type/datasource-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'ultimo pacchetto di dati ricevuto da `PushedDataSource` deve impostare l'elemento `EndOfData` su `True`.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
