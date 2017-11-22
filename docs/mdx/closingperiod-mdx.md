---
title: ClosingPeriod (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: CLOSINGPERIOD
dev_langs: kbMDX
helpviewer_keywords: ClosingPeriod function
ms.assetid: ae709017-219d-43e1-a98a-a85bd365b4cd
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: db1f3170f51d72f912dc84efce36eceeb9e839ec
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="closingperiod-mdx"></a>ClosingPeriod (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il membro che costituisce l'ultimo elemento di pari livello tra i discendenti di un membro specificato a un livello specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ClosingPeriod( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione è principalmente finalizzata all'utilizzo con una dimensione di tipo temporale, ma può essere utilizzata con qualsiasi dimensione.  
  
-   Se si specifica un'espressione di livello il **ClosingPeriod** funzione utilizza la dimensione che contiene il livello specificato e restituisce l'ultimo elemento di pari livello tra i discendenti del membro predefinito al livello specificato.  
  
-   Se vengono specificate sia un'espressione di livello e un'espressione di membro, il **ClosingPeriod** funzione restituisce l'ultimo elemento di pari livello tra i discendenti del membro specificato al livello specificato.  
  
-   Se si specifica un'espressione di livello né un'espressione di membro, il **ClosingPeriod** funzione utilizza il livello predefinito e un membro della dimensione (se presente) del cubo con un tipo di tempo.  
  
 Il **ClosingPeriod** funzione è equivalente all'istruzione MDX seguente:  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`.  
  
> [!NOTE]  
>  Il [OpeningPeriod](../mdx/openingperiod-mdx.md) è simile alla funzione di **ClosingPeriod** funzione, con la differenza che il **OpeningPeriod** funzione restituisce il primo elemento di pari livello anziché l'ultimo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro FY2007 della dimensione Date (il cui tipo semantico è temporale). Viene restituito questo membro poiché il livello Fiscal Year è il primo discendente del livello [Totale], la gerarchia Fiscal è la gerarchia predefinita poiché costituisce la prima gerarchia definita dall'utente nella raccolta di gerarchie e il membro FY 2007 è l'ultimo elemento di pari livello nella gerarchia a questo livello.  
  
```  
SELECT ClosingPeriod() ON 0  
FROM [Adventure Works]  
```  
  
 L'esempio seguente restituisce il valore predefinito della misura per il 30 novembre 2006 membro al livello Date.Date.Date per la gerarchia dell'attributo date. Tale membro costituisce l'ultimo elemento di pari livello del discendente del livello [Totale] nella gerarchia dell'attributo Date.Date.  
  
```  
SELECT ClosingPeriod ([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro dicembre 2003, che costituisce l'ultimo elemento di pari livello del discendente del membro 2003 a livello di anno nella gerarchia definita dall'utente Calendar.  
  
```  
SELECT ClosingPeriod ([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro giugno 2003, che costituisce l'ultimo elemento di pari livello del discendente del membro 2003 a livello di anno nella gerarchia definita dall'utente Fiscal.  
  
```  
SELECT ClosingPeriod ([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [OpeningPeriod &#40; MDX &#41;](../mdx/openingperiod-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [LastSibling &#40; MDX &#41;](../mdx/lastsibling-mdx.md)  
  
  
