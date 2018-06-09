---
title: LastPeriods (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 58e94b5128760dfd1d179ecad3cae7bbf065ee10
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741020"
---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)


  Restituisce il set dei membri che precedono e includono un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Index*  
 Espressione numerica valida che specifica un numero di periodi.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Se il numero di periodi specificato è positivo, il **LastPeriods** funzione restituisce un set di membri che iniziano con il membro con intervallo *indice* -1 nell'espressione di membro specificato e termina con il membro specificato. Il numero di membri restituito dalla funzione è uguale a *indice*.  
  
 Se il numero di periodi specificato è negativo, il **LastPeriods** funzione restituisce un set di membri che iniziano con il membro specificato e termina con il membro che precede (- *indice* - 1) dal membro specificato. Il numero di membri restituito dalla funzione è uguale al valore assoluto di *indice*.  
  
 Se il numero di periodi specificato è uguale a zero, il **LastPeriods** funzione restituisce un set vuoto. Diversamente dal **Lag** funzione, che restituisce il membro specificato, se si specifica 0.  
  
 Se un membro non è specificato, il **LastPeriods** funzione Usa **CurrentMember**. Se nessuna dimensione è contrassegnata come temporale, l'analisi e l'esecuzione della funzione verranno completate senza errori, ma si verificherà un errore a livello di cella nell'applicazione client.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il valore predefinito della misura per il secondo, il terzo e il quarto trimestre fiscale dell'anno fiscale 2002.  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  È inoltre possibile scrivere l'esempio utilizzando l'operatore Range (:).  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura per il primo trimestre fiscale dell'anno fiscale 2002. Benché il numero specificato di periodi sia tre, ne verrà restituito solo uno, in quanto non vi sono periodi precedenti nell'anno fiscale.  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
