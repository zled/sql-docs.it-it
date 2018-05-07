---
title: (MDX) | Documenti Microsoft
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
- IS
dev_langs:
- kbMDX
helpviewer_keywords:
- IS operator
ms.assetid: dc8c0b91-3bb1-49e5-8d70-57545baaa8e0
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5a3cc017970de59914e639c42a23e7808756f076
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="is-mdx"></a>IS (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un confronto logico tra due espressioni di oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Expression1 IS ( Expression2 | NULL )  
```  
  
#### <a name="parameters"></a>Parametri  
 *Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un riferimento a un oggetto MDX.  
  
 *Expression2*  
 Espressione MDX valida che restituisce un riferimento a un oggetto MDX.  
  
## <a name="return-value"></a>Valore restituito  
 Un valore booleano che restituisce **true** se entrambi gli argomenti fanno riferimento allo stesso oggetto; in caso contrario, **false**. Se il **NULL** viene specificata una parola chiave, l'operatore restituisce **true** se *Expression1* è **null**; in caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Il **IS** operatore viene spesso usato per determinare se tuple e membri sono idempotente, vale a dire che sono esattamente equivalenti.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come utilizzare il **IS** operatore per verificare se il membro corrente su un asse è un membro specifico:  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
