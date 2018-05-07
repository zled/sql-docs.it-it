---
title: Radice (MDX) | Documenti Microsoft
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
- Root
dev_langs:
- kbMDX
helpviewer_keywords:
- Root function
ms.assetid: f6c42e87-5a52-4e43-9dd1-ca757f2db79c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5865092286f65e69fed97142dc07fa51c9510446
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="root-mdx"></a>Radice (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce una tupla che include il **tutti** i membri di ogni gerarchia dell'attributo all'interno dell'ambito corrente in un cubo, una dimensione o una tupla. Per ulteriori informazioni sull'ambito, vedere [istruzione SCOPE &#40;MDX&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Se una gerarchia dell'attributo non ha un **tutti** membro, tupla contiene il membro predefinito per tale gerarchia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Cube syntax  
Root ()  
Dimension syntax  
Root( Dimension_Name )  
Tuple syntax  
Root( Tuple_Expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Dimension_Name*  
 Espressione stringa valida che specifica il nome di una dimensione.  
  
 *Tuple_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una tupla.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificata un nome di dimensione né un'espressione di tupla, il **radice** funzione restituisce una tupla che contiene il **tutti** membro (o il membro predefinito se la **tutti** membro non esiste) di ogni gerarchia dell'attributo nel cubo. L'ordine dei membri nella tupla dipende dalla sequenza in cui sono definite le gerarchie dell'attributo nel cubo.  
  
 Se viene specificato un nome di dimensione, il **radice** funzione restituisce una tupla che contiene il **tutti** membro (o il membro predefinito se la **tutti** membro non esiste) di ogni gerarchia dell'attributo nella dimensione specificata in base al contesto del membro corrente. L'ordine dei membri nella tupla dipende dalla sequenza in cui sono definite le gerarchie dell'attributo nella dimensione.  
  
> [!NOTE]  
>  Se viene specificato un nome di gerarchia, il **tupla** funzione selezionerà il nome della dimensione dal nome della gerarchia specificato.  
  
 Se viene specificata un'espressione di tupla, il **radice** funzione restituisce una tupla che contiene l'intersezione della tupla specificata e **tutti** i membri di tutti gli altri attributi di dimensione non in modo esplicito nella tupla specificata.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la tupla contenente il **tutti** membro (o il valore predefinito se la **tutti** membro non esiste) di ogni gerarchia nel cubo Adventure Works.  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene restituita la tupla contenente il **tutti** membro (o il valore predefinito se la **tutti** membro non esiste) di ogni gerarchia nella dimensione Date del cubo Adventure Works e il valore per il membro specificato della dimensione Measures che si interseca con tali membri predefiniti.  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 L'esempio seguente restituisce la tupla contenente il membro della tupla specificato (1 luglio 2001, insieme al **tutti** membro (o il valore predefinito se la **tutti** membro non esiste) di ogni gerarchia non specificata nella data dimensione cubo di Adventure Works e il valore per il membro specificato della dimensione Measures che si interseca con tali membri.  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
