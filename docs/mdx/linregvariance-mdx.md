---
title: LinRegVariance (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b3ae56238623c41d29ccb388a5aaa178352af196
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741230"
---
# <a name="linregvariance-mdx"></a>LinRegVariance (MDX)


  Calcola la regressione lineare di un set e restituisce la varianza associata alla retta di regressione y = ax + b.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LinRegVariance(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression_y*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse Y.  
  
 *Numeric_Expression_x*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse X.  
  
## <a name="remarks"></a>Remarks  
 La regressione lineare, che utilizza il metodo dei minimi quadrati, calcola l'equazione di una retta di regressione, ovvero la retta di migliore approssimazione per una serie di punti. Retta di regressione è l'equazione seguente, in cui un viene definito inclinazione e b viene definito intercetta:  
  
 y = ax+b  
  
 Il **LinRegVariance** funzione valuta il setagainst specificato, la prima espressione numerica per ottenere i valori per l'asse y. La funzione valuta quindi il setagainst specificato, l'espressione numerica in secondo luogo, se specificato, per ottenere i valori per l'asse x. Se il secondo expressionis numerica non specificata, la funzione utilizza il contesto corrente delle celle nel set specificato come valori per l'asse x. L'omissione dell'argomento dell'asse x è frequente con le dimensioni temporali.  
  
 Dopo aver ottenuto il set di punti, il **LinRegVariance** funzione restituisce la varianza statistica che descrive l'adattamento dell'equazione lineare ai punti.  
  
> [!NOTE]  
>  Il **LinRegVariance** funzione ignora le celle vuote o che contengono testo o valori logici. Tuttavia, la funzione include celle con valori zero.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la varianza statistica che descrive in quale misura l'equazione lineare si adatta ai punti per le misure relative a vendite unitarie e vendite dei negozi.  
  
```  
LinRegVariance(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
