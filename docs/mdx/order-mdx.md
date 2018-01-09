---
title: Order (MDX) | Documenti Microsoft
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
f1_keywords: ORDER
dev_langs: kbMDX
helpviewer_keywords: Order function
ms.assetid: 84acff52-2443-4424-a09e-694e6f14c109
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: c67e4106b760f9218172e7ada5628e34dd308f8a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="order-mdx"></a>Order (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Organizza i membri di un set specificato, facoltativamente rispettando o violando la gerarchia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Numeric expression syntax  
Order(Set_Expression, Numeric_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
String expression syntax  
Order(Set_Expression, String_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
 *String_Expression*  
 Espressione stringa valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero espresso come stringa.  
  
## <a name="remarks"></a>Osservazioni  
 Il **ordine** funzione può essere di tipo gerarchica (utilizzando il **ASC** o **DESC** flag) o gerarchico (come specificato utilizzando il **BASC** o **BDESC** flag; il **B** è l'acronimo di "interruzione della gerarchia"). Se **ASC** o **DESC** è specificato, il **ordine** funzione prima organizza i membri in base alla loro posizione nella gerarchia e quindi ogni livello. Se **BASC** o **BDESC** è specificato, il **ordine** funzione Organizza i membri del set indipendentemente dalla gerarchia. Viene specificato alcun flag, **ASC** è l'impostazione predefinita.  
  
 Se il **ordine** funzione viene utilizzata con un set in cui due o più gerarchie sono Crossjoin e **DESC** flag viene utilizzato, vengono ordinati solo i membri dell'ultima gerarchia del set. Questa situazione rappresenta una modifica rispetto ad Analysis Services 2000 in cui tutte le gerarchie del set sono ordinate.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce, dal **Adventure Works** del cubo, il numero di ordini dei rivenditori per tutti elementi Calendar Quarters dalla gerarchia Calendar nella dimensione Date. Il **ordine** funzione Riordina il set per l'asse ROWS. Il **ordine** funzione ordina il set da `[Reseller Order Count]` in ordine gerarchico discendente come base il `[Calendar]` gerarchia.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Si noti che in questo esempio, quando il **DESC** flag viene modificato in **BDESC**, la gerarchia viene interrotta e viene restituito l'elenco di elementi Calendar Quarters senza considerare per la gerarchia:  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Nell'esempio seguente viene restituita la misura Reseller Sales per le cinque sottocategorie di prodotti più vendute, indipendentemente dalla gerarchia, in base a Reseller Gross Profit. Il **Subset** funzione viene utilizzata per restituire solo le prime 5 tuple nel set di dopo l'ordinamento del risultato mediante la **ordine** (funzione).  
  
 `SELECT Subset`  
  
 `(Order`  
  
 `([Product].[Product Categories].[SubCategory].members`  
  
 `,[Measures].[Reseller Gross Profit]`  
  
 `,BDESC`  
  
 `)`  
  
 `,0`  
  
 `,5`  
  
 `) ON 0`  
  
 `FROM [Adventure Works]`  
  
 L'esempio seguente usa il **Rank** funzione per classificare i membri della gerarchia City, in base alla misura Reseller Sales Amount e visualizzarli in ordine di rango. Tramite il **ordine** funzione per ordinare il set di membri della gerarchia City, l'ordinamento viene eseguito una sola volta e quindi seguito da un'analisi lineare prima di essere visualizzato in un criterio di ordinamento.  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
 L'esempio seguente restituisce il numero di prodotti nel set che sono univoci, utilizzando il **ordine** funzione per ordinare le tuple non vuote prima di applicare il **filtro** (funzione). Il **CurrentOrdinal** funzione viene utilizzata per confrontare ed eliminare i valori equivalenti.  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , (OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          )  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
 Per comprendere come **DESC** flag i set di tuple, considerare innanzitutto i risultati della query seguente:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Sull'asse delle righe è possibile vedere che i Sales Territory Groups sono stati ordinati in ordine decrescente per Quantità della tassa nel modo seguente: North America, Europe, Pacific, NA. Osservare cosa accade se si crossjoin il set di Sales Territory Groups con il set di Product Subcategories e applicare il **ordine** funziona nello stesso modo, come segue:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Mentre il set Product Subcategories è stato ordinato in modo gerarchico decrescente, gli elementi Sales Territory Groups attualmente non sono ordinati e vengono visualizzati nello stesso ordine in cui sono presenti nella gerarchia, ovvero Europe, NA, North America e Pacific. Questa situazione si verifica perché solo l'ultima gerarchia del set di tuple, ovvero Product Subcategories, è ordinata. Per riprodurre il comportamento di Analysis Services 2000, utilizzare una serie di annidati **genera** funzioni per ordinare ogni set prima che venga eseguito il cross join, ad esempio:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
GENERATE(  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
,  
ORDER(  
[Sales Territory].[Sales Territory].CURRENTMEMBER  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC))  
ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
