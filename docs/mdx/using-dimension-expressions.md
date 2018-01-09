---
title: Utilizzo di espressioni di dimensione | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- expressions [MDX], dimensions
- dimensions [Analysis Services], MDX
ms.assetid: 1d40cffb-e88f-4284-93cf-d62ab4f08395
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 1417fd747df92c84fe66e2c69996f57ab51875e1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="using-dimension-expressions"></a>Utilizzo delle espressioni di dimensione
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
  
