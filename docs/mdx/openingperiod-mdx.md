---
title: OpeningPeriod (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9384a2993423c68db1d65a92cb0b532502c110b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581363"
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il primo elemento di pari livello tra i discendenti di un livello specificato, facoltativamente in corrispondenza di un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione è principalmente finalizzata all'utilizzo con una dimensione temporale, ma può essere utilizzata con qualsiasi dimensione.  
  
-   Se si specifica un'espressione di livello il **OpeningPeriod** funzione Usa la gerarchia che contiene il livello specificato e restituisce il primo elemento di pari livello tra i discendenti del membro predefinito al livello specificato.  
  
-   Se vengono specificate sia un'espressione di livello e un'espressione di membro, il **OpeningPeriod** funzione restituisce il primo elemento di pari livello tra i discendenti del membro specificato al livello specificato all'interno della gerarchia che contiene il livello specificato.  
  
-   Se viene specificata né un'espressione di livello né un'espressione di membro, il **OpeningPeriod** funzione utilizza il livello predefinito e un membro della dimensione con un tipo di tempo.  
  
> [!NOTE]  
>  Il [ClosingPeriod](../mdx/closingperiod-mdx.md) è simile alla funzione di **OpeningPeriod** funzione, con la differenza che il **ClosingPeriod** funzione restituisce l'ultimo elemento di pari livello anziché il primo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro FY2002 della dimensione Date (il cui tipo semantico è temporale). Viene restituito questo membro poiché il livello Fiscal Year è il primo discendente del livello [Totale], la gerarchia Fiscal è la gerarchia predefinita poiché costituisce la prima gerarchia definita dall'utente nella raccolta di gerarchie e il membro FY2002 è il primo elemento di pari livello nella gerarchia a questo livello.  
  
```  
SELECT OpeningPeriod() ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro 1 luglio 2001 al livello Date.Date.Date della gerarchia dell'attributo Date.Date. Tale membro costituisce il primo elemento di pari livello del discendente del livello [Totale] nella gerarchia dell'attributo Date.Date.  
  
```  
SELECT OpeningPeriod([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro gennaio 2003, che costituisce il primo elemento di pari livello del discendente del membro 2003 a livello di anno nella gerarchia definita dall'utente Calendar.  
  
```  
SELECT OpeningPeriod([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro luglio 2002, che costituisce il primo elemento di pari livello del discendente del membro 2003 a livello di anno nella gerarchia definita dall'utente Fiscal.  
  
```  
SELECT OpeningPeriod([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [TopCount &#40;MDX&#41;](../mdx/topcount-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40;MDX&#41;](../mdx/firstsibling-mdx.md)  
  
  
