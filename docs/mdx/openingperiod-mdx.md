---
title: OpeningPeriod (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENINGPERIOD
dev_langs:
- kbMDX
helpviewer_keywords:
- OpeningPeriod function
ms.assetid: bebf55cf-e5c6-42b1-98f2-1d6e54093d4c
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 30100b2762d3365c1599e665db54e2446e392fb3
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="openingperiod-mdx"></a>OpeningPeriod (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Osservazioni  
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
 [TopCount &#40; MDX &#41;](../mdx/topcount-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40; MDX &#41;](../mdx/firstsibling-mdx.md)  
  
  

