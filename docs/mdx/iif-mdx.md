---
title: IIf (MDX) | Documenti Microsoft
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
- IIF
dev_langs:
- kbMDX
helpviewer_keywords:
- IIf function
ms.assetid: ec7b35e6-f4c5-40bf-93c8-b83c1cc26fe2
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0b520aa3c3761c8dd8452b1732923b7415bcbca6
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="iif-mdx"></a>IIf (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vengono restituite diverse espressioni del ramo a seconda che una condizione Boolean sia true o false.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IIf(Logical_Expression, Expression1 [HINT <hints>], Expression2 [HINT <hints>])  
```  
  
## <a name="arguments"></a>Argomenti  
 La funzione IIf accetta tre argomenti: iif (\<condition >, \<quindi creare un branch >, \<else branch >).  
  
 *Logical_Expression*  
 Una condizione che restituisce **true** (1) o **false** (0). Deve essere un'espressione logica MDX (Multidimensional Expression) valida.  
  
 *Hint di expression1 [Eager | Strict | Lazy]]*  
 Utilizzato quando l'espressione logica restituisce **true**. Expression1 deve essere un'espressione MDX (Multidimensional Expression) valida.  
  
 *Hint di expression2 [Eager | Strict | Lazy]]*  
 Utilizzato quando l'espressione logica restituisce **false**. Expression2 deve essere un'espressione MDX (Multidimensional Expression) valida.  
  
## <a name="remarks"></a>Osservazioni  
 La condizione specificata dall'espressione logica restituisce **false** quando il valore di questa espressione è zero. Qualsiasi altro valore restituisce **true**.  
  
 Se la condizione è **true**, **IIf** funzione restituisce la prima espressione. In caso contrario, la funzione restituisce la seconda espressione.  
  
 Le espressioni specificate possono restituire valori oppure oggetti MDX. Le espressioni specificate non devono inoltre essere necessariamente dello stesso tipo.  
  
 Il **IIf** funzione non è consigliata per la creazione di un set di membri in base ai criteri di ricerca. Utilizzare invece il [filtro](../mdx/filter-mdx.md) funzione per valutare ogni membro di un set specificato in base a un'espressione logica e restituire un subset di membri.  
  
> [!NOTE]  
>  Se una delle espressioni restituisce NULL, quando la condizione viene soddisfatta il set di risultati sarà NULL.  
  
 Hint è un modificatore facoltativo che determina il modo e il momento in cui l'espressione viene valutata. Consente di eseguire l'override del piano di query predefinito specificando il modo in cui l'espressione viene valutata.  
  
-   Tramite EAGER l'espressione viene valutata nel sottospazio IIF originale.  
  
-   Tramite STRICT l'espressione viene valutata solo nel sottospazio limitato creato dall'espressione della condizione logica.  
  
-   Tramite LAZY l'espressione viene valutata in modalità cella per cella.  
  
 Mentre EAGER e STRICT si applicano solo ai rami then-else di IIF, LAZY si applica a tutte le espressioni MDX. Qualsiasi espressione MDX può essere seguita da un HINT LAZY tramite cui l'espressione verrà valutata in modalità cella per cella.  
  
 EAGER e STRICT si escludono a vicenda nell'hint e possono essere utilizzati nella stessa funzione IIF(,,) in diverse espressioni.  
  
 Per ulteriori informazioni, vedere [hint per la Query funzione IIF in SQL Server Analysis Services 2008](http://go.microsoft.com/fwlink/?LinkId=269540) e [piani di esecuzione e pianificare gli hint per la funzione IIF di MDX e l'istruzione CASE](http://go.microsoft.com/fwlink/?LinkId=269565).  
  
## <a name="examples"></a>Esempi  
 La query seguente viene illustrato un utilizzo semplice di **IIF** all'interno di una misura calcolata per restituire uno dei due diversi valori di stringa quando la misura Internet Sales Amount è maggiore o minore di $10000:  
  
 `WITH MEMBER MEASURES.IIFDEMO AS`  
  
 `IIF([Measures].[Internet Sales Amount]>10000`  
  
 `, "Sales Are High", "Sales Are Low")`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.IIFDEMO} ON 0,`  
  
 `[Date].[Date].[Date].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 IIF viene spesso utilizzata per gestire gli errori delle divisioni per zero all'interno di misure calcolate, come nell'esempio seguente:  
  
 `WITH`  
  
 `//Returns 1.#INF when the previous period contains no value`  
  
 `//but the current period does`  
  
 `MEMBER MEASURES.[Previous Period Growth With Errors] AS`  
  
 `([Measures].[Internet Sales Amount]-([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER))`  
  
 `/`  
  
 `([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)`  
  
 `,FORMAT_STRING='PERCENT'`  
  
 `//Traps division by zero and returns null when the previous period contains`  
  
 `//no value but the current period does`  
  
 `MEMBER MEASURES.[Previous Period Growth] AS`  
  
 `IIF(([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)=0,`  
  
 `NULL,`  
  
 `([Measures].[Internet Sales Amount]-([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER))`  
  
 `/`  
  
 `([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)`  
  
 `),FORMAT_STRING='PERCENT'`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.[Previous Period Growth With Errors], MEASURES.[Previous Period Growth]} ON 0,`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004],`  
  
 `[Date].[Calendar].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Subcategory].&[26])`  
  
 Di seguito è riportato un esempio di **IIF** restituisce uno di due set nella funzione Generate per creare un set complesso di tuple su righe:  
  
 `SELECT {[Measures].[Internet Sales Amount]} ON 0,`  
  
 `//If Internet Sales Amount is zero or null`  
  
 `//returns the current year and the All Customers member`  
  
 `//else returns the current year broken down by Country`  
  
 `GENERATE(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `, IIF([Measures].[Internet Sales Amount]=0,`  
  
 `{([Date].[Calendar Year].CURRENTMEMBER, [Customer].[Country].[All Customers])}`  
  
 `, {{[Date].[Calendar Year].CURRENTMEMBER} * [Customer].[Country].[Country].MEMBERS}`  
  
 `))`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Subcategory].&[26])`  
  
 In questo esempio viene infine illustrato l'utilizzo degli hint di piano:  
  
 `WITH MEMBER MEASURES.X AS`  
  
 `IIF(`  
  
 `[Measures].[Internet Sales Amount]=0`  
  
 `, NULL`  
  
 `, (1/[Measures].[Internet Sales Amount]) HINT EAGER)`  
  
 `SELECT {[Measures].x} ON 0,`  
  
 `[Customer].[Customer Geography].[Country].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

