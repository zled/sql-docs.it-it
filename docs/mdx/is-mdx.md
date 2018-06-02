---
title: (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5c36a5f45e34d6d78043f6ce8a3e3fb040ecc9f6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578593"
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
  
## <a name="remarks"></a>Remarks  
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
  
  
