---
title: Elemento AggregateFunction (ASSL) | Documenti Microsoft
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e292a0c509a746130493c7df601a9d373096c406
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063925"
---
# <a name="aggregatefunction-element-assl"></a>Elemento AggregateFunction (ASSL)
  Definisce il tipo di funzione di aggregazione usata da un [misure](../objects/measure-element-assl.md) elemento.  
  
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
  
## <a name="remarks"></a>Remarks  
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
  
  