---
title: ': (Intervallo) (MDX) | Documenti Microsoft'
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
- ':'
dev_langs:
- kbMDX
helpviewer_keywords:
- ': (range operator)'
- range operator (:)
ms.assetid: f9b36aca-4efd-49b4-9e4f-12914c1b24a6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: cba26f6b69ca22a1ab39fa753749d6a8b1a150df
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="-range-mdx"></a>: (intervallo) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un'operazione sui set che restituisce un set ordinato in modo naturale, in cui i due membri specificati costituiscono gli endpoint e tutti i membri compresi tra questi ultimi vengono inclusi come membri del set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression : Member_Expression      
```  
  
#### <a name="parameters"></a>Parametri  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="return-value"></a>Valore restituito  
 Set che contiene i membri specificati e tutti i membri compresi tra i membri specificati.  
  
## <a name="remarks"></a>Osservazioni  
 Entrambi i parametri devono specificare membri allo stesso livello e nella stessa gerarchia di una dimensione data. Se entrambi i parametri specificano lo stesso membro, il **: (intervallo)** operatore restituisce un set contenente solo il membro specificato. Se il primo parametro è Null, il set contiene tutti i membri dall'inizio del livello del membro specificato nel secondo parametro, fino a includere quel membro. Se il secondo parametro è Null, il set contiene tutti i membri dal membro specificato nel primo parametro, fino a includere l'ultimo membro sullo stesso livello.  
  
 In MDX non esiste un equivalente funzionale di questo operatore per i set.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di questo operatore.  
  
```  
-- This query returns the freight cost per user  
-- for products, averaged by month, for the first quarter.  
With Member [Measures].[Freight Per Customer] as  
 (  
     [Measures].[Internet Freight Cost]  
     /   
     [Measures].[Customer Count]  
)  
  
SELECT   
    {[Ship Date].[Calendar].[Month].&[2004]&[1] : [Ship Date].[Calendar].[Month].&[2004]&[3]} ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
