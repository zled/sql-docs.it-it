---
title: Elemento AggregateFunction (ASSL) | Microsoft Docs
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
- AggregateFunction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregateFunction
helpviewer_keywords:
- AggregateFunction element
ms.assetid: 880b6bd0-d62a-4221-831c-39f748ee84f2
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc2eccf4ca6e41ffba52424c4f45edb71c9c1c46
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261207"
---
# <a name="aggregatefunction-element-assl"></a>Elemento AggregateFunction (ASSL)
  Definisce il tipo di funzione di aggregazione usata da un [misura](../objects/measure-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Measure>  
   ...  
   <AggregateFunction>...</AggregateFunction>  
   ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Sum*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Misura](../objects/measure-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Sum*|Per l'aggregazione della misura viene utilizzata la funzione `Sum`.|  
|*Conteggio*|Per l'aggregazione della misura viene utilizzata la funzione `Count`.|  
|*Min*|Per l'aggregazione della misura viene utilizzata la funzione `Min`.|  
|*Max*|Per l'aggregazione della misura viene utilizzata la funzione `Max`.|  
|*DistinctCount*|Per l'aggregazione della misura viene utilizzata la funzione `DistinctCount`.|  
|*Nessuno*|Non viene eseguita alcuna aggregazione della misura.|  
|*ByAccount*|La misura viene aggregata in base al tipo di conto.|  
|*AverageOfChildren*|La misura viene aggregata restituendo la media dei relativi membri figlio.|  
|*FirstChild*|La misura viene aggregata restituendone il primo membro figlio.|  
|*LastChild*|La misura viene aggregata restituendone l'ultimo membro figlio.|  
|*FirstNonEmpty*|La misura viene aggregata restituendone il primo membro non vuoto.|  
|*LastNonEmpty*|La misura viene aggregata restituendone l'ultimo membro non vuoto.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `AggregateFunction` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
