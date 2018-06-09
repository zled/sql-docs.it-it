---
title: UniqueName (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 41642dc8bcaed03faaffdf9a16d8fc465aa2d360
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743930"
---
# <a name="uniquename-mdx"></a>UniqueName (MDX)


  Restituisce il nome univoco del livello, della dimensione, del membro o della gerarchia specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Dimension expression syntax  
Dimension_Expression.UniqueName  
  
Hierarchy expression syntax  
Hierarchy_Expression.UniqueName  
  
Level expression syntax  
Level_Expression.UniqueName  
  
Member expression syntax  
Member_Expression.UniqueName  
```  
  
## <a name="arguments"></a>Argomenti  
 *Dimension_Expression*  
 Espressione MDX (Multidimensional Expression) valida che viene risolta in una dimensione.  
  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Il **UniqueName** il nome univoco dell'oggetto, non il nome restituito dalla funzione di [nome](../mdx/name-mdx.md) (funzione). Il nome restituito non include il nome del cubo. I risultati restituiti dipendono dalle impostazioni sul lato server oppure dalla proprietà della stringa di connessione MDX Unique Name Style.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il valore del nome univoco per la dimensione Product, la gerarchia Product Categories, il livello Subcategory e il membro Bike Racks del cubo Adventure Works.  
  
```  
WITH MEMBER DimensionUniqueName   
   AS [Product].UniqueName  
MEMBER HierarchyUniqueName   
   AS [Product].[Product Categories].UniqueName  
MEMBER LevelUniqueName   
   AS [Product].[Product Categories].[Subcategory].UniqueName  
MEMBER MemberUniqueName   
   AS [Product].[Product Categories].[Subcategory].[Bike Racks]  
SELECT   
   {DimensionUniqueName  
   , HierarchyUniqueName  
   , LevelUniqueName  
   , MemberUniqueName }  
   ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
