---
title: (Divisione) (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fbf7e28d9e33d2eccbc3d51b8ff61c0cabd75270
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577973"
---
# <a name="divide---mdx-operator-reference"></a>Divisione - riferimento agli operatori MDX
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un'operazione aritmetica di divisione di un numero per un altro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Parametri  
 *dividendo*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un valore numerico.  
  
 *divisore*  
 Espressione MDX valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Valore con il tipo di dati del parametro con precedenza maggiore.  
  
## <a name="remarks"></a>Remarks  
 Il valore effettivo restituito dal **/ (divisione)** operatore rappresenta il quoziente della prima espressione divisa per la seconda espressione.  
  
 È necessario che alle due espressioni sia applicato lo stesso tipo di dati oppure che un'espressione possa essere convertita in modo implicito nel tipo di dati dell'altra espressione. Se *divisore* restituisce un valore null, verrà generato un errore. Se entrambi *divisore* e *dividendo* restituiscono un valore null, l'operatore restituisce un valore null.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di questo operatore.  
  
```  
-- This query returns the freight cost per user,  
-- for products, averaged by month.   
With Member [Measures].[Freight Per Customer] as  
    [Measures].[Internet Freight Cost]  
    /   
    [Measures].[Customer Count]  
  
SELECT   
    [Ship Date].[Calendar].[Calendar Year] Members ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
 La divisione di un valore diverso da zero o non Null per zero o null restituirà il valore Infinito, il quale viene visualizzato nei risultati di query come "1, #INF". Nella maggior parte dei casi, è necessario controllare le divisioni per zero per evitare questa situazione. Nell'esempio seguente viene illustrata la modalità di questo controllo:  
  
 `//Returns 1.#INF when Internet Sales Amount is zero or null`  
  
 `Member [Measures].[Reseller to Internet Ratio] AS`  
  
 `[Measures].[Reseller Sales Amount]`  
  
 `/`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `//Traps the division by zero scenario and returns null instead of 1.#INF`  
  
 `Member [Measures].[Reseller to Internet Ratio With Error Handling] AS`  
  
 `IIF([Measures].[Internet Sales Amount]=0, NULL,`  
  
 `[Measures].[Reseller Sales Amount]`  
  
 `/`  
  
 `[Measures].[Internet Sales Amount])`  
  
 `SELECT`  
  
 `{[Measures].[Reseller to Internet Ratio],[Measures].[Reseller to Internet Ratio With Error Handling]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 `WHERE([Date].[Calendar].[Calendar Year].&[2001])`  
  
## <a name="see-also"></a>Vedere anche  
 [IIf &#40;MDX&#41;](../mdx/iif-mdx.md)   
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
