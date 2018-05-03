---
title: Parola chiave EXISTING (MDX) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 888c3039c98b36b15f28f6cfac21506547f3940c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-query---existing-keyword"></a>Query MDX - parola chiave EXISTING
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Forza la valutazione di un determinato set all'interno del contesto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione set MDX (Multidimensional Expression) valida.  
  
## <a name="remarks"></a>Osservazioni  
 Per impostazione predefinita, i set vengono valutati all'interno del contesto del cubo che include i membri del set. È tuttavia possibile forzare la valutazione di un set specificato all'interno del contesto corrente utilizzando la parola chiave **Existing** .  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il numero dei rivenditori le cui vendite sono diminuite nel periodo di tempo precedente, in base ai valori del membro State-Province selezionati dall'utente valutati tramite la funzione **Aggregate** . È tuttavia possibile forzare la valutazione di un set specificato all'interno del contesto corrente utilizzando la parola chiave [Hierarchize &#40;MDX&#41;](../../../mdx/hierarchize-mdx.md) e [DrilldownLevel (MDX)](../../../mdx/drilldownlevel-mdx.md) vengono usate per restituire i valori relativi alla diminuzione delle vendite per le categorie di prodotti nella dimensione Product. La parola chiave **Existing** forza la valutazione del set nella funzione **Filter** nel contesto corrente, ovvero i membri Washington e Oregon della gerarchia dell'attributo State-Province.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Numero & #40; Set & #41; & #40; MDX & #41;](../../../mdx/count-set-mdx.md)   
 [AddCalculatedMembers & #40; MDX & #41;](../../../mdx/addcalculatedmembers-mdx.md)   
 [Funzione di aggregazione & #40; MDX & #41;](../../../mdx/aggregate-mdx.md)   
 [Filtro & #40; MDX & #41;](../../../mdx/filter-mdx.md)   
 [Proprietà & #40; MDX & #41;](../../../mdx/properties-mdx.md)   
 [DrilldownLevel & #40; MDX & #41;](../../../mdx/drilldownlevel-mdx.md)   
 [HIERARCHIZE & #40; MDX & #41;](../../../mdx/hierarchize-mdx.md)   
 [Riferimento alla funzione MDX & #40; MDX & #41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  
