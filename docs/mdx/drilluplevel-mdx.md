---
title: DrillupLevel (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DRILLUPLEVEL
dev_langs:
- kbMDX
helpviewer_keywords:
- DrillupLevel function
ms.assetid: 63431f79-f3a1-40c4-bf57-2b6bd8991cc3
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8fb99e8e1984f0bbfddf4e7e8bd48e7fa05c0e45
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue il drill-up dei membri di un set situati al livello immediatamente inferiore al livello specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
## <a name="remarks"></a>Osservazioni  
 Il **DrillupLevel** funzione restituisce un set di membri organizzato gerarchicamente in base ai membri inclusi nel set specificato. L'ordine dei membri nel set specificato viene mantenuto.  
  
 Se si specifica un'espressione di livello il **DrillupLevel** funzione restituisce il set recuperando solo i membri che sono di sopra del livello specificato. Se si specifica un'espressione di livello ma nessun membro del livello specificato è rappresentato nel set specificato, viene restituito tale set.  
  
 Se non si specifica un'espressione di livello, la funzione genera il set recuperando solo i membri del livello superiore rispetto al livello inferiore della prima dimensione indicata nel set specificato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il set di membri del primo set che si trovano al di sopra del livello Subcategory.  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
