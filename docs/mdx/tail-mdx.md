---
title: Tail (MDX) | Documenti Microsoft
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
- TAIL
dev_langs:
- kbMDX
helpviewer_keywords:
- Tail function
ms.assetid: d62a1bb2-55c0-4939-8526-cdc3d444ffe2
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c836c38e54063961c9714cc076fe66383ef01864
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="tail-mdx"></a>Tail (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un subset dalla fine di un set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Tail(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Count*  
 Espressione numerica valida che specifica il numero di tuple che devono essere restituite.  
  
## <a name="remarks"></a>Osservazioni  
 Il **della parte finale del** funzione restituisce il numero di tuple specificato dalla fine del set specificato. L'ordine degli elementi viene mantenuto. Il valore predefinito di *conteggio* è 1. Se il numero specificato di tuple è minore di 1, la funzione restituisce il set vuoto. Se il numero di tuple specificato supera il numero di tuple nel set, la funzione restituisce il set originale.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la misura Reseller Sales per le cinque sottocategorie di prodotti più vendute, indipendentemente dalla gerarchia, in base a Reseller Gross Profit. Il **della parte finale del** funzione viene utilizzata per restituire solo gli ultimi cinque set del risultato dopo il reverse-ordinamento del risultato mediante la **ordine** (funzione).  
  
```  
SELECT Tail  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BASC  
      )  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
