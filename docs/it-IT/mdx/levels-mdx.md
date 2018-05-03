---
title: Livelli (MDX) | Documenti Microsoft
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
- Levels
dev_langs:
- kbMDX
helpviewer_keywords:
- Levels function
ms.assetid: 1a989cc9-8aa8-4ec3-b5e9-795d6fa84983
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 0c75ebacdd811ebd64b242b74b3279d01f181c50
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="levels-mdx"></a>Levels (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
