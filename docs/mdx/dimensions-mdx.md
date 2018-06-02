---
title: Dimensioni (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43c105daff0d53c886df087600da99bdd1292574
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577893"
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
  
## <a name="remarks"></a>Remarks  
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
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
