---
title: Covarianza (MDX) | Documenti Microsoft
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
- COVARIANCE
dev_langs:
- kbMDX
helpviewer_keywords:
- Covariance function
ms.assetid: 5faf6742-62db-4c5c-8797-096bf1cab273
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ede1c98c6087dc31c91cc95041461908bd6bb229
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="covariance-mdx"></a>Covariance (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce la covarianza della popolazione delle coppie di valori x-y valutata su un set, utilizzando la formula della popolazione distorta (dividendo per il numero di coppie x-y).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Covariance(Set_Expression,Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression_y*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse Y.  
  
 *Numeric_Expression_x*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse X.  
  
## <a name="remarks"></a>Osservazioni  
 Il **covarianza** funzione valuta il set specificato in base alla prima espressione numerica, per ottenere i valori per l'asse y. La funzione valuta quindi il set specificato in base alla seconda espressione numerica, se specificata, per ottenere il set di valori per l'asse x. Se il secondo expressionis numerica non specificata, la funzione utilizza il contesto corrente delle celle nel set specificato come valori per l'asse x.  
  
 Il **covarianza** funzione utilizza la formula della popolazione distorta. È in contrasto con la [CovarianceN](../mdx/covariancen-mdx.md) funzione che utilizza la formula della popolazione non distorta (dividendo il numero di coppie x-y, quindi sottraendo 1).  
  
> [!NOTE]  
>  Il **covarianza** funzione ignora le celle vuote o che contengono testo o valori logici vengono ignorati. Tuttavia, la funzione include celle con valori zero.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare la funzione Covariance:  
  
```  
WITH   
MEMBER [Measures].[CovarianceDemo] AS  
COVARIANCE([Date].[Date].[Date].Members, [Measures].[Internet Sales Amount], [Measures].[Internet Order Count])   
SELECT {[Measures].[CovarianceDemo]} ON 0   
FROM  
[Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

