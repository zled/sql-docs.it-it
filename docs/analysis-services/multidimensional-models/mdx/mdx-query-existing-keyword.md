---
title: Parola chiave EXISTING (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5078aa14be3c476e8b89545ed1541f12b7686f4e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-query---existing-keyword"></a>Query MDX - parola chiave EXISTING
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
 [Count &#40;Set&#41; &#40;MDX&#41;](../../../mdx/count-set-mdx.md)   
 [AddCalculatedMembers &#40; MDX &#41;](../../../mdx/addcalculatedmembers-mdx.md)   
 [Funzione di aggregazione &#40; MDX &#41;](../../../mdx/aggregate-mdx.md)   
 [Filtro &#40; MDX &#41;](../../../mdx/filter-mdx.md)   
 [Proprietà &#40; MDX &#41;](../../../mdx/properties-mdx.md)   
 [DrilldownLevel &#40; MDX &#41;](../../../mdx/drilldownlevel-mdx.md)   
 [HIERARCHIZE &#40; MDX &#41;](../../../mdx/hierarchize-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  

