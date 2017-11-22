---
title: MemberToStr (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: MEMBERTOSTR
dev_langs: kbMDX
helpviewer_keywords: MemberToStr function
ms.assetid: 2076b24a-603a-4d74-91bd-a3d347739bcd
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: afbc6a17e21b36f2235f5213e6a869641333fb9d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="membertostr-mdx"></a>MemberToStr (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una stringa in formato MDX (Multidimensional Expression) che corrisponde a un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
MemberToStr(Member_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione restituisce una stringa che contiene l'elemento uniquename di un membro e che viene utilizzata generalmente per passare un elemento uniquename di un membro a una funzione esterna.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la stringa [Geography].[Geography].[Country].&[United States]:  
  
 `WITH MEMBER Measures.x AS MemberToStr`  
  
 `([Geography].[Geography].[Country].[United States])`  
  
 `SELECT Measures.x ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
