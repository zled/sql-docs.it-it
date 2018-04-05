---
title: LastPeriods (MDX) | Documenti Microsoft
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
- LASTPERIODS
dev_langs:
- kbMDX
helpviewer_keywords:
- LastPeriods function
ms.assetid: a15df7a1-b261-48ed-aacc-d2804db8dbf7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a3a9f0940796ecbc8138447fa8dd4ba59febbe96
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Osservazioni  
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
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
