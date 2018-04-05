---
title: Utilizzo di espressioni di membro | Documenti Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- members [MDX], expressions
- expressions [MDX], members
ms.assetid: 63c7af49-8bea-47c5-9566-a961f77d2a3d
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: bc1574fc06eeaa032fb68d395106721fc33ec699
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="using-member-expressions"></a>Utilizzo delle espressioni di membro
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Un'espressione di membro contiene un identificatore di membro, una funzione per i membri o un'espressione che può essere convertita in un membro.  
  
 Gli identificatori di membro possono avere molti formati diversi. Il formato più semplice di un identificatore di membro è costituito dal nome del membro. Ad esempio  
  
```  
SELECT Amount ON 0  
FROM [Adventure Works]  
  
```  
  
 Tuttavia, se vi sono numerosi membri con lo stesso nome su differenti gerarchie, non sarà possibile in alcun modo determinare quale membro sarà restituito dalla query. Ad esempio, nella query seguente vengono richiesti dei dati per un membro con il nome [CY 2004]. La query viene eseguita correttamente, ma vengono individuati almeno sei membri con quel nome nel cubo di Adventure Works:  
  
```  
SELECT [CY 2004] ON 0  
FROM [Adventure Works]  
  
```  
  
 Pertanto, il formato più affidabile per un identificatore di membro è il nome univoco del membro che garantisce l'identificazione di uno specifico membro in un cubo. In Analysis Services è possibile generare nomi univoci in diversi modi, ma un nome univoco è sempre composto da almeno due identificatori: il nome della dimensione e il nome del membro o chiave membro. Un nome univoco ha il seguente formato:  
  
```  
  
Dimension_Name  
.[Hierarchy_Name.] [[{Member_Name | &Member_Key}.]... ] {Member_Name | &Member_Key}  
  
```  
  
 Di seguito vengono riportati alcuni esempi di nomi univoci di membro dal cubo di Adventure Works:  
  
```  
[Measures].[Amount]  
[Date].[Calendar Year].&[2004]  
[Date].[Calendar].[Calendar Quarter].&[2004]&[1]  
[Employee].[Employees].&[112]  
[Product].[Product Categories].[All Products]  
  
```  
  
 Sono molte le funzioni MDX che restituiscono membri. Per un elenco completo, vedere [riferimento alle funzioni MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  Per ulteriori informazioni sui nomi dei membri e le chiavi dei membri, vedere [utilizzo di membri, tuple e set &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; MDX &#41;](../mdx/expressions-mdx.md)  
  
  
