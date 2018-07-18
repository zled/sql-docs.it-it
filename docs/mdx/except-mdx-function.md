---
title: Except (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 03d9b5140eb0cbf9d868e43c65213efe917994a9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740000"
---
# <a name="except-mdx-function"></a>Except-funzione (MDX)


  Valuta due set e rimuove le tuple del primo set presenti anche nel secondo, mantenendo facoltativamente i duplicati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Except(Set_Expression1, Set_Expression2 [, ALL ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Remarks  
 Se **tutti** è specificato, i duplicati individuati nel primo set vengono mantenuti; duplicati trovati nel secondo set verranno comunque rimosse. I membri verranno restituiti nell'ordine in cui sono visualizzati nel primo set.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di questa funzione.  
  
```  
   //This query shows the quantity of orders for all products,  
   //with the exception of Components, which are not  
   //sold.  
SELECT   
   [Date].[Month of Year].Children  ON COLUMNS,  
   Except  
      ([Product].[Product Categories].[All].Children ,  
         {[Product].[Product Categories].[Components]}  
      ) ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   ([Measures].[Order Quantity])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [- &#40;Ad eccezione di&#41; &#40;MDX&#41;](../mdx/except-mdx-operator.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
