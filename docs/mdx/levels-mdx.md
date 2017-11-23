---
title: Livelli (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Levels
dev_langs: kbMDX
helpviewer_keywords: Levels function
ms.assetid: 1a989cc9-8aa8-4ec3-b5e9-795d6fa84983
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: dbe9522966cb3efdeffc8f2a34297f9edb80c99b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="levels-mdx"></a>Levels (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il livello la cui posizione all'interno di una dimensione o gerarchia è specificata da un'espressione numerica oppure il cui nome è specificato da un'espressione stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Level_Number*  
 Espressione numerica valida che specifica il numero di un livello.  
  
 *Level_Name*  
 Espressione stringa valida che specifica il nome di un livello.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato un numero di livello, il **livelli** funzione restituisce il livello associato alla posizione in base zero specificata.  
  
 Se viene specificato un nome di livello, il **livelli** funzione restituisce il livello specificato.  
  
> [!NOTE]  
>  Utilizzare la sintassi delle espressioni stringa per le funzioni definite dall'utente.  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti illustrano ciascuno del **livelli** funzione sintassi.  
  
### <a name="numeric"></a>Numeric  
 Nell'esempio seguente viene restituito il livello Country:  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 Nell'esempio seguente viene restituito il livello Country:  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
