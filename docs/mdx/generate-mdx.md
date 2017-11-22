---
title: Generare (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: GENERATE
dev_langs: kbMDX
helpviewer_keywords: Generate function
ms.assetid: 696a229d-c2f1-47b7-9dca-7b0a6b547d9b
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b64e0aca29625cf83021666c29b6306192e8b877
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="generate-mdx"></a>Generate (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Applica un set a ogni membro di un altro set e unisce i set risultanti tramite un join di unione. In alternativa, questa funzione restituisce una stringa concatenata creata valutando un'espressione stringa su un set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set expression syntax  
Generate( Set_Expression1 ,  Set_Expression2 [ , ALL ]  )  
  
String expression syntax  
Generate( Set_Expression1 ,  String_Expression [ ,Delimiter ]  )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *String_Expression*  
 Espressione stringa valida che corrisponde in genere al nome del membro corrente (CurrentMember.Name) di ogni tupla nel set specificato.  
  
 *Delimitatore*  
 Delimitatore valido espresso come espressione stringa.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato un secondo set, il **genera** funzione restituisce un set generato applicando le tuple del secondo set a ogni tupla nel primo set*,* e quindi creando un join risultante dall'unione. Se **tutti** viene specificato, la funzione consente di mantenere duplicati nel set risultante.  
  
 Se viene specificata un'espressione di stringa, il **genera** funzione restituisce una stringa generata valutando l'espressione stringa specificata rispetto a ogni tupla nel primo set*,* quindi concatenando i risultati. Facoltativamente, è possibile delimitare la stringa separando i vari risultati nella stringa concatenata risultante.  
  
## <a name="examples"></a>Esempi  
  
### <a name="set"></a>Impostare  
 Nell'esempio seguente, la query restituisce un set che contiene la misura Internet Sales amount quattro volte, perché quattro sono i membri nel set [Date].[Calendar Year].[Calendar Year].MEMBERS:  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]}, ALL)  
ON 0  
FROM [Adventure Works]  
```  
  
 La rimozione di ALL modifica la query in modo che Internet Sales Amount sia restituito una sola volta:  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]})  
ON 0  
FROM [Adventure Works]  
```  
  
 L'utilizzo pratico più comune di **genera** è impostato per valutare un complesso espressione, ad esempio TopCount, su un set di membri. Nell'esempio di query seguente vengono visualizzati i primi 10 prodotti per ogni anno di calendario su righe:  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS  
, TOPCOUNT(  
[Date].[Calendar Year].CURRENTMEMBER  
*  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount]))  
ON 1  
FROM [Adventure Works]  
```  
  
 Si noti che diverse top 10 viene visualizzato per ogni anno e che l'utilizzo di **genera** è l'unico modo per ottenere questo risultato. Applicando un semplice crossjoin ai calendari e al set dei 10 prodotti migliori sarà possibile visualizzare i 10 migliori prodotti ogni volta, ripetuti per ogni anno, come illustrato nell'esempio seguente:  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS  
*   
TOPCOUNT(  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount])  
ON 1  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 Nell'esempio seguente viene illustrato come utilizzare **genera** per restituire una stringa:  
  
```  
WITH   
MEMBER MEASURES.GENERATESTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME)  
MEMBER MEASURES.GENERATEDELIMITEDSTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME, " AND ")  
SELECT   
{MEASURES.GENERATESTRINGDEMO, MEASURES.GENERATEDELIMITEDSTRINGDEMO}  
ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Questa forma del **genera** può risultare utile durante il debug di calcoli, in quanto consente di restituire una stringa che visualizza i nomi di tutti i membri di un set. Questo potrebbe essere più facile da leggere rispetto alla rigida rappresentazione MDX di un set che il [SetToStr &#40; MDX &#41; ](../mdx/settostr-mdx.md) risultato della funzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
