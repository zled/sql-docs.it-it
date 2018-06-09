---
title: Union (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e51749416c0668ccc4760132bb860121ebae6e3d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743490"
---
# <a name="union--mdx"></a>Union (MDX)


  Restituisce un set generato dall'unione di due set, mantenendo facoltativamente i membri duplicati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Standard syntax  
Union(Set_Expression1, Set_Expression2 [,...n][, ALL])  
  
Alternate syntax 1  
Set_Expression1 + Set_Expression2 [+...n]  
  
Alternate syntax 2  
{Set_Expression1 , Set_Expression2 [,...n]}  
```  
  
## <a name="arguments"></a>Argomenti  
 *Espressione set 1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Espressione set 2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione restituisce l'unione di due o più set specificati *.* Con la sintassi standard e con la sintassi alternativa 1, i duplicati vengono eliminati per impostazione predefinita. Con la sintassi standard, utilizzando il **tutti** flag consente di mantenere duplicati nel set unito. I duplicati vengono eliminati dalla parte finale del set. Con la sintassi alternativa 2, i duplicati vengono sempre mantenuti.  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti illustrano il comportamento del **unione** con ogni sintassi.  
  
### <a name="standard-syntax-duplicates-eliminated"></a>Sintassi standard, con eliminazione dei duplicati  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="standard-syntax-duplicates-retained"></a>Sintassi standard, con mantenimento dei duplicati  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   , ALL  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-1-duplicates-eliminated"></a>Sintassi alternativa 1, con eliminazione dei duplicati  
  
```  
SELECT   
   [Date].[Calendar Year].children   
   + {[Date].[Calendar Year].[CY 2002]}   
   + {[Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-2-duplicates-retained"></a>Sintassi alternativa 2, con mantenimento dei duplicati  
  
```  
SELECT   
   {[Date].[Calendar Year].children  
   , [Date].[Calendar Year].[CY 2002]  
   , [Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [+ &#40;Union&#41; &#40;MDX&#41;](../mdx/union-mdx-operator-reference.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
