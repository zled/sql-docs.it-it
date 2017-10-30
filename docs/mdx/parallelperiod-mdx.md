---
title: ParallelPeriod (MDX) | Documenti Microsoft
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
- PARALLELPERIOD
dev_langs:
- kbMDX
helpviewer_keywords:
- ParallelPeriod function
ms.assetid: 9c87f5a6-5694-46f1-9890-bd9705190ea7
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 294bab2d1403b6f6195a0888c731c95cfd938df8
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un membro di un periodo precedente nella stessa posizione relativa del membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ParallelPeriod( [ Level_Expression [ ,Index [ , Member_Expression ] ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Indice*  
 Espressione numerica valida che specifica il numero di periodi paralleli per l'intervallo.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Pur essendo simili per il [Cousin](../mdx/cousin-mdx.md) funzione, il **ParallelPeriod** funzione è più strettamente correlata alle serie temporali. Il **ParallelPeriod** funzione accetta il predecessore del membro specificato al livello specificato, consente di trovare pari livello del predecessore con l'intervallo specificato e infine restituisce il periodo parallelo del membro specificato tra i discendenti di pari livello.  
  
 Il **ParallelPeriod** funzione include i valori predefiniti seguenti:  
  
-   Se si specifica un'espressione di livello né un'espressione di membro, il valore del membro predefinito è il membro corrente della prima gerarchia nella prima dimensione di tipo *ora* nel gruppo di misure.  
  
-   Se viene specificata un'espressione di livello, ma non viene specificata un'espressione di membro, il valore del membro predefinito è *Level_Expression*. **Hierarchy.CurrentMember**.  
  
-   Il valore di indice predefinito è 1.  
  
-   Il livello predefinito è il livello dell'elemento padre del membro specificato.  
  
 Il **ParallelPeriod** funzione è equivalente all'istruzione MDX seguente:  
  
 `Cousin(Member_Expression, Ancestor(Member_Expression, Level_Expression) .Lag(Numeric_Expression))`  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il periodo parallelo per il mese di ottobre 2003 con un intervallo di tre periodi, in base al livello trimestre. Viene così restituito il mese di gennaio 2003.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Quarter]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene restituito il periodo parallelo per il mese di ottobre 2003 con un intervallo di tre periodi, in base al livello semestre. Viene così restituito il mese di aprile 2002.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Semester]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

