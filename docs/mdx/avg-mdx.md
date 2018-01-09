---
title: AVG (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: AVG
dev_langs: kbMDX
helpviewer_keywords: Avg function [MDX]
ms.assetid: efe61272-c3eb-4a33-b231-e00c30be16aa
caps.latest.revision: "42"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 4972d38cb5cd52d0da7d76c6eb771520a89fb896
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="avg-mdx"></a>Avg (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Valuta un set e restituisce la media dei valori non vuoti delle celle del set, calcolata sulle misure del set o su una misura specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Avg( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato un set di tuple vuote o un set vuoto, il **Avg** funzione restituisce un valore vuoto.  
  
 Il **Avg** funzione calcola la media dei valori non vuoti delle celle nel set specificato calcolando innanzitutto la somma dei valori nelle celle nel set specificato e quindi dividendo la somma calcolata per il conteggio delle celle non vuote nel set specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignora i valori Null durante il calcolo del valore medio di un set di numeri.  
  
 Se un'espressione numerica specifica (in genere una misura) non è specificata, il **Avg** funzione calcola la media di ogni misura all'interno del contesto di query corrente. Se viene fornita una misura specifica, il **Avg** funzione valuta innanzitutto la misura sul set e quindi la funzione calcola la media in base alla misura specificata.  
  
> [!NOTE]  
>  Quando si utilizza il **CurrentMember** funzione in un'istruzione di membro calcolato, è necessario specificare un'espressione numerica, perché è presente alcuna misura predefinita per la coordinata corrente in un contesto di query.  
  
 Per forzare l'inclusione delle celle vuote, l'applicazione deve utilizzare il [CoalesceEmpty](../mdx/coalesceempty-mdx.md) di funzione o specificare un valore valido *Numeric_Expression* che fornisce un valore pari a zero (0) per i valori vuoti. Per ulteriori informazioni sulle celle vuote, vedere la documentazione relativa a OLE DB.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la media di una misura su un set specificato. Si noti che la misura specificata può essere la misura predefinita per i membri del set specificato o una misura specificata.  
  
 `WITH SET [NW Region] AS`  
  
 `{[Geography].[State-Province].[Washington]`  
  
 `, [Geography].[State-Province].[Oregon]`  
  
 `, [Geography].[State-Province].[Idaho]}`  
  
 `MEMBER [Geography].[Geography].[NW Region Avg] AS`  
  
 `AVG ([NW Region]`  
  
 `--Uncomment the line below to get an average by Reseller Gross Profit Margin`  
  
 `--otherwise the average will be by whatever the default measure is in the cube,`  
  
 `--or whatever measure is specified in the query`  
  
 `--, [Measures].[Reseller Gross Profit Margin]`  
  
 `)`  
  
 `SELECT [Date].[Calendar Year].[Calendar Year].Members ON 0`  
  
 `FROM [Adventure Works]`  
  
 `WHERE ([Geography].[Geography].[NW Region Avg])`  
  
 L'esempio seguente restituisce la media giornaliera del `Measures.[Gross Profit Margin]` misura, calcolata sui giorni di ogni mese dell'anno fiscale 2003, dal **Adventure Works** cubo. Il **Avg** funzione calcola la Media dal set di giorni in cui sono contenuti in ogni mese del `[Ship Date].[Fiscal Time]` gerarchia. La prima e la seconda versione del calcolo sono esemplificative del comportamento predefinito della funzione Avg relativo rispettivamente all'esclusione e all'inclusione nella media dei giorni in cui non sono state registrate vendite.  
  
 `WITH MEMBER Measures.[Avg Gross Profit Margin] AS`  
  
 `Avg(`  
  
 `Descendants(`  
  
 `[Ship Date].[Fiscal].CurrentMember,`  
  
 `[Ship Date].[Fiscal].[Date]`  
  
 `),`  
  
 `Measures.[Gross Profit Margin]`  
  
 `), format_String='percent'`  
  
 `MEMBER Measures.[Avg Gross Profit Margin Including Empty Days] AS`  
  
 `Avg(`  
  
 `Descendants(`  
  
 `[Ship Date].[Fiscal].CurrentMember,`  
  
 `[Ship Date].[Fiscal].[Date]`  
  
 `),`  
  
 `CoalesceEmpty(Measures.[Gross Profit Margin],0)`  
  
 `), Format_String='percent'`  
  
 `SELECT`  
  
 `{Measures.[Avg Gross Profit Margin],Measures.[Avg Gross Profit Margin Including Empty Days]} ON COLUMNS,`  
  
 `[Ship Date].[Fiscal].[Fiscal Year].Members ON ROWS`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Product].&[344])`  
  
 L'esempio seguente restituisce la media giornaliera del `Measures.[Gross Profit Margin]` misura, calcolata sui giorni di ogni semestre dell'anno fiscale 2003, dal **Adventure Works** cubo.  
  
```  
WITH MEMBER Measures.[Avg Gross Profit Margin] AS  
   Avg(  
      Descendants(  
         [Ship Date].[Fiscal].CurrentMember,   
            [Ship Date].[Fiscal].[Date]  
      ),   
      Measures.[Gross Profit Margin]  
   )  
SELECT  
   Measures.[Avg Gross Profit Margin] ON COLUMNS,  
      [Ship Date].[Fiscal].[Fiscal Year].[FY 2003].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
