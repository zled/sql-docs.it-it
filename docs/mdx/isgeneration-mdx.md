---
title: IsGeneration (MDX) | Documenti Microsoft
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
- ISGENERATION
dev_langs:
- kbMDX
helpviewer_keywords:
- IsGeneration function
ms.assetid: fd11d2e0-d81d-45af-ac45-c98634d05550
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b40d895af5298cf3538280a3875363401819930d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="isgeneration-mdx"></a>IsGeneration (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica se il membro specificato è incluso in una generazione specifica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IsGeneration(Member_Expression, Generation_Number)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Generation_Number*  
 Espressione numerica valida che specifica la generazione rispetto alla quale il membro specificato viene valutato.  
  
## <a name="remarks"></a>Osservazioni  
 Il **IsGeneration** risultato della funzione **true** se il membro specificato è il numero di generazione specificata. In caso contrario, la funzione restituisce **false**. Inoltre, se il membro specificato restituisce un membro vuoto, il **IsGeneration** risultato della funzione **false**.  
  
 I membri foglia hanno indice di generazione 0. L'indice di generazione dei membri non foglia viene determinato aggiungendo 1 all'indice di generazione più alto ottenuto dall'unione di tutti i membri figlio del membro specificato. Dato il modo in cui viene determinato l'indice di generazione dei membri non foglia, è possibile che un determinato membro non foglia appartenga a più generazioni.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito TRUE se [Date].[Fiscal].CurrentMember è parte della seconda generazione:  
  
 `WITH MEMBER MEASURES.ISGENERATIONDEMO AS`  
  
 `IsGeneration([Date].[Fiscal].CURRENTMEMBER, 2)`  
  
 `SELECT {MEASURES.ISGENERATIONDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
