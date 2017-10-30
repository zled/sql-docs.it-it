---
title: CovarianceN (MDX) | Documenti Microsoft
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
- COVARIANCEN
dev_langs:
- kbMDX
helpviewer_keywords:
- Covariancen function
ms.assetid: 1cc621cd-ffa0-40aa-91f0-bc5cb57f692b
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2eeee4c108965c00e847a8c3acdd60334e39000f
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="covariancen-mdx"></a>CovarianceN (MDX)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce la covarianza del campione delle coppie di valori x-y valutata su un set, utilizzando la formula della popolazione non distorta (dividendo per il numero di coppie x-y).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CovarianceN(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression_y*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse Y.  
  
 *Numeric_Expression_x*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse X.  
  
## <a name="remarks"></a>Osservazioni  
 Il **CovarianceN** funzione valuta il set specificato in base alla prima espressione numerica, per ottenere i valori per l'asse y. La funzione valuta quindi il set specificato in base alla seconda espressione numerica, se specificata, per ottenere il set di valori per l'asse x. Se la seconda espressione numerica viene omessa, come valori per l'asse X la funzione utilizza il contesto corrente delle celle contenute nel set specificato.  
  
 Il **CovarianceN** funzione utilizza la formula della popolazione non distorta. È in contrasto con la [covarianza](../mdx/covariance-mdx.md) funzione che utilizza la formula della popolazione distorta (dividendo per il numero di coppie x-y).  
  
> [!NOTE]  
>  Il **CovarianceN** funzione ignora le celle vuote o che contengono testo o valori logici. Tuttavia, la funzione include celle con valori zero.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

