---
title: HIERARCHIZE (MDX) | Documenti Microsoft
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
- HIERARCHIZE
dev_langs:
- kbMDX
helpviewer_keywords:
- Hierarchize function
ms.assetid: e9795003-70e7-4b4c-9074-45b5b9b817fa
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 81477801484bdad233f627fb0829991c498cc9fd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="hierarchize-mdx"></a>Hierarchize (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ordina i membri di un set in una gerarchia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Hierarchize(Set_Expression [ , POST ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Osservazioni  
 Il **Hierarchize** funzione Organizza i membri del set specificato in ordine gerarchico. e mantiene sempre i duplicati.  
  
-   Se **POST** non viene specificato, la funzione Ordina membri in un livello in base all'ordine naturale. ovvero, se non sono specificate altre condizioni di ordinamento, secondo l'ordinamento predefinito dei membri nella gerarchia. I membri figlio seguono immediatamente i membri padre corrispondenti.  
  
-   Se **POST** è specificato, il **Hierarchize** funzione ordina i membri di un livello tramite un ordine di post-naturale. In altri termini, i membri figlio precedono i relativi elementi padre.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene eseguito il drill-up del membro Canada. Il **Hierarchize** funzione viene utilizzata per organizzare i membri del set specificato in ordine gerarchico, che è necessario per il **DrillUpMember** (funzione).  
  
```  
SELECT DrillUpMember   
   (  
      Hierarchize  
         (  
            {[Geography].[Geography].[Country].[Canada]  
            ,[Geography].[Geography].[Country].[United States]  
            ,[Geography].[Geography].[State-Province].[Alberta]  
            ,[Geography].[Geography].[State-Province].[Brunswick]  
            ,[Geography].[Geography].[State-Province].[Colorado]   
            }  
         ), {[Geography].[Geography].[Country].[United States]}  
   )  
ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente restituisce la somma del `Measures.[Order Quantity]` membro, aggregato sui primi nove mesi del 2003 contenuti nella `Date` dimensione, dal **Adventure Works** cubo. Il **PeriodsToDate** funzione definisce le tuple del set su cui opera la funzione di aggregazione. Il **Hierarchize** funzione Organizza i membri del set specificato di membri della dimensione Product in ordine gerarchico.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
