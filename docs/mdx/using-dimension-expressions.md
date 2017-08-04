---
title: Utilizzo di espressioni di dimensione | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- expressions [MDX], dimensions
- dimensions [Analysis Services], MDX
ms.assetid: 1d40cffb-e88f-4284-93cf-d62ab4f08395
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 66a955b547f5760ae1193b541fde5f3dc13d323f
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="using-dimension-expressions"></a>Utilizzo delle espressioni di dimensione
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  In genere le espressioni di dimensione e di gerarchia vengono utilizzate per passare parametri a funzioni nelle espressioni MDX al fine di ottenere membri, set o tuple da una gerarchia.  
  
 Le espressioni di dimensione possono essere solo espressioni semplici perché rappresentano identificatori di oggetto. Vedere [espressioni &#40; MDX &#41; ](../mdx/expressions-mdx.md) per una spiegazione delle espressioni semplici e complesse.  
  
## <a name="dimension-expressions"></a>Espressioni di dimensione  
 Un'espressione di dimensione contiene un identificatore di dimensione o una funzione per le dimensioni.  
  
 Le espressioni di dimensione sono utilizzate raramente da sole. In genere infatti si specifica una gerarchia su una dimensione. L'unica eccezione è quando si utilizza la dimensione Measures perché non dispone di gerarchie.  
  
 Nell'esempio seguente viene illustrato un membro calcolato che utilizza l'espressione [Measures] insieme alle funzioni .Members e Count() per restituire il numero di membri sulla dimensione Measures:  
  
 `WITH MEMBER [Measures].[MeasureCount] AS`  
  
 `COUNT([Measures].MEMBERS)`  
  
 `SELECT [Measures].[MeasureCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Identificatore della dimensione viene visualizzata come *Dimension_Name* nella notazione BNF utilizzata per descrivere le istruzioni MDX.  
  
## <a name="hierarchy-expressions"></a>Espressioni di gerarchia  
 Analogamente alle espressioni di dimensione, anche le espressioni di gerarchia contengono un identificatore di gerarchia o una funzione per le gerarchie. Nell'esempio seguente viene illustrato l'utilizzo dell'espressione di gerarchia [Date].[Calendar], insieme alle funzioni .Levels e .Count, per restituire il numero di livelli nella gerarchia Calendar della dimensione Date:  
  
 `WITH MEMBER [Measures].[CalendarLevelCount] AS`  
  
 `[Date].[Calendar].Levels.Count`  
  
 `SELECT [Measures].[CalendarLevelCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 L'utilizzo più comune delle espressioni di gerarchia avviene insieme alla funzione .Members per restituire tutti i membri di una gerarchia. Nell'esempio seguente vengono restituiti tutti i membri di [Date].[Calendar] sull'asse delle righe:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Un identificatore di gerarchia viene visualizzato come *Dimension_Name**.* *Hierarchy_Name* nella notazione BNF utilizzata per descrivere le istruzioni MDX.  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; MDX &#41;](../mdx/expressions-mdx.md)  
  
  

