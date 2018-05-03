---
title: LinRegIntercept (MDX) | Documenti Microsoft
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
- LINREGINTERCEPT
dev_langs:
- kbMDX
helpviewer_keywords:
- LinRegIntercept function
ms.assetid: 6ef2527d-e519-4b66-b67e-131c5831234e
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ad53c2f6aa216383072f0399b54bad98a67643ee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="linregintercept-mdx"></a>LinRegIntercept (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Calcola la regressione lineare di un set e restituisce il valore dell'intercetta x nella retta di regressione y = ax + b.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LinRegIntercept(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression_y*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse Y.  
  
 *Numeric_Expression_x*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse X.  
  
## <a name="remarks"></a>Osservazioni  
 La regressione lineare, che utilizza il metodo dei minimi quadrati, calcola l'equazione di una retta di regressione, ovvero la retta di migliore approssimazione per una serie di punti. Retta di regressione è l'equazione seguente, in cui un viene definito inclinazione e b viene definito intercetta:  
  
 y = ax+b  
  
 Il **LinRegIntercept** funzione valuta il set specificato in base alla prima espressione numerica per ottenere i valori per l'asse y. La funzione valuta quindi il set specificato in base alla seconda espressione numerica, se specificata, per ottenere i valori per l'asse X. Se la seconda espressione numerica viene omessa, come valori per l'asse X la funzione utilizza il contesto corrente delle celle contenute nel set specificato. L'omissione dell'argomento dell'asse X è frequente con le dimensioni temporali.  
  
 Dopo aver ottenuto il set di punti, il **LinRegIntercept** funzione restituisce l'intersezione della retta di regressione (b nell'equazione sopra riportata).  
  
> [!NOTE]  
>  Il **LinRegIntercept** funzione ignora le celle vuote o che contengono testo o valori logici. Tuttavia, la funzione include celle con valori zero.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita l'intercetta della linea di regressione relativa alle misure Unit Sales e Store Sales.  
  
```  
LinRegIntercept(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
