---
title: Asse (MDX) | Documenti Microsoft
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
- AXIS
dev_langs:
- kbMDX
helpviewer_keywords:
- Axis function
ms.assetid: a3a60a1e-e266-4fa1-ae13-bae73544de33
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 95a1d7f16c7f30f2a118820414994a615090d96c
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="axis-mdx"></a>Axis (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il set di tuple su un asse specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Axis_Number*  
 Espressione numerica valida che specifica il numero dell'asse.  
  
## <a name="remarks"></a>Osservazioni  
 Il **asse** funzione utilizza la posizione in base zero di un asse per restituire il set di tuple su un asse. Ad esempio, `Axis(0)` restituisce l'asse COLUMNS, `Axis(1)` restituisce l'asse ROWS e così via. Il **asse** funzione non può essere utilizzata sull'asse del filtro. Questa funzione può essere utilizzata per rendere i membri calcolati specifici del contesto della query eseguita. Ad esempio, potrebbe essere necessario un membro calcolato che fornisce la somma solo dei membri selezionati sull'asse delle righe. Può essere utilizzata anche per rendere la definizione di un asse dipendente dalla definizione di un altro asse: ad esempio, ordinando il contenuto dell'asse delle righe in base al valore del primo elemento sull'asse delle colonne.  
  
> [!NOTE]  
>  Un asse può fare riferimento solo a un asse precedente. Ad esempio, `Axis(0)` deve essere successiva alla valutazione dell'asse COLUMNS, come avviene quando viene eseguita su un asse ROW o PAGE.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio di query seguente viene illustrato l'utilizzo della funzione Axis:  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SETTOSTR(AXIS(1))`  
  
 `SELECT MEASURES.AXISDEMO ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Nell'esempio seguente viene illustrato come utilizzare la funzione Axis all'interno di un membro calcolato:  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SUM(AXIS(1), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.AXISDEMO} ON 0,`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

