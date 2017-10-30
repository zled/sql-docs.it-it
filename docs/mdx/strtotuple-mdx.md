---
title: StrToTuple (MDX) | Documenti Microsoft
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
- STRTOTUPLE
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToTuple function
ms.assetid: e162cc01-cddd-4654-baab-d73abdc33b80
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2ca9d105bf04c91fd2c65bea74f92a0d0ef1edd
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="strtotuple-mdx"></a>StrToTuple (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce la tupla specificata da una stringa in formato MDX (Multidimensional Expression).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *Tuple_Specification*  
 Espressione stringa valida che specifica, in modo diretto o indiretto, una tupla.  
  
## <a name="remarks"></a>Osservazioni  
 Il **StrToTuple** funzione restituisce il set specificato. Il **StrToTuple** funzione viene in genere utilizzata con funzioni definite dall'utente per la restituzione di una tupla specificata da una funzione esterna a un'istruzione MDX.  
  
-   Quando viene utilizzato il flag CONSTRAINED, la tupla specificata deve contenere nomi di membri completi o non qualificati. Questo flag viene utilizzato per ridurre il rischio di attacchi intrusivi tramite la stringa specificata. Se viene specificata una stringa non direttamente risolvibile in nomi di membri completi o non qualificati, viene visualizzato l'errore seguente: "Le restrizioni imposte dal flag CONSTRAINED nella funzione STRTOTUPLE sono state violate".  
  
-   Quando non viene utilizzato il flag CONSTRAINED, la tupla specificata può essere risolta in un'espressione MDX valida che restituisce una tupla.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la funzione viene utilizzata per restituire la misura Reseller Sales Amount relativa al membro Bayern per l'anno di calendario 2004. La specifica della tupla fornita contiene un'espressione di tupla MDX valida.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente la funzione viene utilizzata per restituire la misura Reseller Sales Amount relativa al membro Bayern per l'anno di calendario 2004. La specifica della tupla fornita contiene nomi di membri qualificati, come richiesto dal flag CONSTRAINED.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente la funzione viene utilizzata per restituire la misura Reseller Sales Amount relativa al membro Bayern per l'anno di calendario 2004. La specifica della tupla fornita contiene un'espressione di tupla MDX valida.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito un errore a causa del flag CONSTRAINED. Nonostante la tupla specificata contenga un'espressione di tupla MDX valida, il flag CONSTRAINED richiede in essa nomi di membri completi o non qualificati.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

