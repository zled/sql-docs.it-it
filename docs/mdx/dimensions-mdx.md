---
title: Dimensioni (MDX) | Documenti Microsoft
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
- Dimensions
dev_langs:
- kbMDX
helpviewer_keywords:
- Dimensions function
ms.assetid: 64f63aa0-ef74-4415-a0c9-8acc6cd81739
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 2f0c3ea111eafd55f4fc1f0a0eacc0993ef0d713
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dimensions-mdx"></a>Dimensions (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce la gerarchia specificata da un'espressione numerica o stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Hierarchy_Number*  
 Espressione numerica valida che specifica il numero di una gerarchia.  
  
 *Hierarchy_Name*  
 Espressione stringa valida che specifica il nome di una gerarchia.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato un numero di gerarchia, il **dimensioni** funzione restituisce una gerarchia la cui posizione in base zero all'interno del cubo è stato specificato il numero di gerarchia.  
  
 Se viene specificato un nome di gerarchia, il **dimensioni** funzione restituisce la gerarchia specificata. In genere, si utilizza questa versione di stringa di **dimensioni** funzione con funzioni definite dall'utente.  
  
> [!NOTE]  
>  Il **misure** dimensione è sempre rappresentata da `Dimensions(0)`.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa il **dimensioni** funzione per restituire il nome, numero di livelli e conteggio dei membri di una gerarchia specificata, utilizzando un'espressione numerica sia un'espressione stringa.  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
