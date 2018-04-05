---
title: Stima (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PREDICT
dev_langs:
- kbMDX
helpviewer_keywords:
- Predict function
ms.assetid: a82f3edd-249b-4559-98d3-6e10d81a095d
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d7266e462167dcae27a30b033c368f910b6dfc0f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="predict-mdx"></a>Predict (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

    
> [!CAUTION]  
>  Questa funzione è in corso di rimozione a causa di inconsistenze interne.  
>   
>  Per una soluzione alternativa che utilizza un'espressione DMX, rivedere la sezione di esempio.  
  
 Restituisce il valore di un'espressione numerica valutata su un modello di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Mining_Model_Name*  
 Espressione stringa valida che rappresenta il nome di un modello di data mining.  
  
 *String_Expression*  
 Espressione stringa valida che restituisce un'espressione DMX valida per il modello di data mining specificato.  
  
## <a name="remarks"></a>Osservazioni  
 Il **Predict** funzione valuta l'espressione stringa specificata all'interno del contesto del modello di data mining specificato.  
  
 La sintassi e le funzioni di data mining sono documentate nella specifica DMX (Data Mining Expressions).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono stimati il nome del cluster e la relativa distanza da un particolare cliente tramite il modello di data mining Customer Clusters:  
  
```  
WITH MEMBER MEASURES.CLNAME AS   
PREDICT("Customer Clusters", "Cluster()")  
MEMBER MEASURES.CLDISTANCE AS   
PREDICT("Customer Clusters", "ClusterDistance(Cluster())")  
SELECT {MEASURES.CLNAME, MEASURES.CLDISTANCE} ON 0   
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Customer].&[12012])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
