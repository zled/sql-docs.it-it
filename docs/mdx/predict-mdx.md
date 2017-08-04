---
title: Stima (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7bec1c96bd70b9b75c3a8c212cf1f6c04c27c73e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="predict-mdx"></a>Predict (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
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
  
  

