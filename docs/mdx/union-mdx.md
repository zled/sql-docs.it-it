---
title: Union (MDX) | Documenti Microsoft
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
- functions [MDX], Union
ms.assetid: cc083455-8b3b-46af-bb55-1e238376f162
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d68afa2f9c424a0bb745ad2feaf781923eac624a
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="union--mdx"></a>Union (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un set generato dall'unione di due set, mantenendo facoltativamente i membri duplicati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Standard syntax  
Union(Set_Expression1, Set_Expression2 [,...n][, ALL])  
  
Alternate syntax 1  
Set_Expression1 + Set_Expression2 [+...n]  
  
Alternate syntax 2  
{Set_Expression1 , Set_Expression2 [,...n]}  
```  
  
## <a name="arguments"></a>Argomenti  
 *Espressione set 1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Espressione set 2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione restituisce l'unione di due o più set specificati*.* Con la sintassi standard e con la sintassi alternativa 1, i duplicati vengono eliminati per impostazione predefinita. Con la sintassi standard, utilizzando il **tutti** flag consente di mantenere duplicati nel set unito. I duplicati vengono eliminati dalla parte finale del set. Con la sintassi alternativa 2, i duplicati vengono sempre mantenuti.  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti illustrano il comportamento del **unione** con ogni sintassi.  
  
### <a name="standard-syntax-duplicates-eliminated"></a>Sintassi standard, con eliminazione dei duplicati  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="standard-syntax-duplicates-retained"></a>Sintassi standard, con mantenimento dei duplicati  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   , ALL  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-1-duplicates-eliminated"></a>Sintassi alternativa 1, con eliminazione dei duplicati  
  
```  
SELECT   
   [Date].[Calendar Year].children   
   + {[Date].[Calendar Year].[CY 2002]}   
   + {[Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-2-duplicates-retained"></a>Sintassi alternativa 2, con mantenimento dei duplicati  
  
```  
SELECT   
   {[Date].[Calendar Year].children  
   , [Date].[Calendar Year].[CY 2002]  
   , [Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [+ &#40; Unione &#41; &#40; MDX &#41;](../mdx/union-mdx-operator-reference.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

