---
title: Elemento Parameters (XMLA) | Microsoft Docs
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
- Parameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameters
- urn:schemas-microsoft-com:xml-analysis#Parameters
- microsoft.xml.analysis.parameters
helpviewer_keywords:
- Parameters element
ms.assetid: d46454a1-a1d1-4aa8-95ea-54be22a53e83
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 87836c6ca9f33c100b3ba10ba91379370e787773
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158862"
---
# <a name="parameters-element-xmla"></a>Elemento Parameters (XMLA)
  Contiene una raccolta di [parametri](parameter-element-xmla.md) gli elementi utilizzati per il [Execute](../xml-elements-methods-execute.md) (metodo).  
  
 **Namespace:** `urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Eseguire](../xml-elements-methods-execute.md)|  
|Elementi figlio|[Parametro](parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Comandi alcune XML for Analysis (XMLA), ad esempio la [processo](../xml-elements-commands/process-element-xmla.md) comando, possono richiedere informazioni aggiuntive. L'elemento `Parameters` fornisce un meccanismo per fornire informazioni aggiuntive, incluse le informazioni a blocchi, per un comando XMLA.  
  
 Se il comando XMLA non utilizza l'elemento `Parameters`, l'elemento può essere omesso in caso di chiamata al metodo `Execute`.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
