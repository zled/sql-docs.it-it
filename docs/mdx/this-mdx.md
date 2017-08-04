---
title: (MDX) | Documenti Microsoft
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
- THIS
dev_langs:
- kbMDX
helpviewer_keywords:
- This function [MDX]
ms.assetid: 87acddee-ae54-49ee-8923-1b760606e8b7
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 54b73433950bb6e60d1262955c3f65ad0ab7413e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="this-mdx"></a>This (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il sottocubo corrente da utilizzare con le assegnazioni nello script di calcolo MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
This   
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **questo** funzione può essere utilizzata al posto di un'espressione di sottocubo per ottenere il sottocubo corrente all'interno dell'ambito corrente all'interno dello script di calcolo MDX. Il **questo** necessario utilizzare la funzione sul lato sinistro di un'assegnazione.  
  
## <a name="examples"></a>Esempi  
 Nel frammento di Script MDX seguente viene illustrato come utilizzare la parola chiave This con istruzioni SCOPE per fare assegnazioni ai sottocubi:  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2005],`  
  
 `[Date].[Fiscal].[Fiscal Quarter].Members,`  
  
 `[Measures].[Sales Amount Quota]`  
  
 `) ;`  
  
 `This = ParallelPeriod`  
  
 `(`  
  
 `[Date].[Fiscal].[Fiscal Year], 1,`  
  
 `[Date].[Fiscal].CurrentMember`  
  
 `) * 1.35 ;`  
  
 `/*-- Allocate equally to months in FY 2002 -----------------------------*/`  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2002],`  
  
 `[Date].[Fiscal].[Month].Members`  
  
 `) ;`  
  
 `This = [Date].[Fiscal].CurrentMember.Parent / 3 ;`  
  
 `End Scope ;`  
  
 `End Scope;`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Calcoli](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  

