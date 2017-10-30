---
title: Predecessore (MDX) | Documenti Microsoft
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
- ANCESTOR
dev_langs:
- kbMDX
helpviewer_keywords:
- Ancestor function
ms.assetid: b5bf2ce4-20df-4ebc-97eb-e44a6f64cc50
caps.latest.revision: 46
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a9aad080913e792291f8d72281afe522704042e5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="ancestor-mdx"></a>Ancestor (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Funzione che restituisce il predecessore di un membro specificato al livello specificato oppure alla distanza specificata dal membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Level syntax  
Ancestor(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestor(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Distanza*  
 Espressione numerica valida che specifica la distanza dal membro specificato.  
  
## <a name="remarks"></a>Osservazioni  
 Con il **predecessore** funzione, si specifica la funzione con un'espressione di membro MDX e quindi un'espressione MDX di un livello è un predecessore del membro oppure un'espressione numerica che rappresenta il numero di livelli di sopra di tale membro. Con queste informazioni, il **predecessori** funzione restituisce il membro predecessore a tale livello.  
  
> [!NOTE]  
>  Per restituire un set contenente il membro predecessore, anziché il solo membro predecessore, utilizzare il [predecessori &#40; MDX &#41; ](../mdx/ancestors-mdx.md) (funzione).  
  
 Se si specifica un'espressione di livello il **predecessore** funzione restituisce il predecessore del membro specificato al livello specificato. Se il membro specificato non è incluso nella stessa gerarchia del livello specificato, la funzione restituisce un errore.  
  
 Se viene specificata una distanza, la **predecessore** funzione restituisce il predecessore del membro specificato che rappresenta il numero di passaggi specificato nella gerarchia specificata dall'espressione di membro. Un membro può essere specificato come membro di una gerarchia dell'attributo, una gerarchia definita dall'utente o, in alcuni casi, una gerarchia padre-figlio. Con il numero 1 viene restituito l'elemento padre di un membro, mentre con il numero 2 viene restituito l'elemento padre del padre di un membro, se esistente. Il numero 0 restituisce il membro stesso.  
  
> [!NOTE]  
>  Utilizzare questo modulo del **predecessore** funzione per i casi in cui il livello dell'elemento padre è sconosciuto o non può essere rinominato.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata un'espressione di livello e vengono restituiti l'importo delle vendite su Internet per ogni State-Province in Australia e la relativa percentuale sul totale delle vendite su Internet per l'Australia.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
   [Measures].[Internet Sales Amount],    
      Ancestor   
         (  
         [Customer].[Customer Geography].CurrentMember,  
            [Customer].[Customer Geography].[Country]  
         )  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
        [Customer].[Customer Geography].[Country].&[Australia],  
           [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene utilizzata un'espressione numerica e vengono restituiti l'importo delle vendite su Internet per ogni State-Province in Australia e la relativa percentuale sul totale delle vendite su Internet per tutti i paesi.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
      [Measures].[Internet Sales Amount],  
         Ancestor   
            ([Customer].[Customer Geography].CurrentMember, 2)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
         [Customer].[Customer Geography].[Country].&[Australia],  
            [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

