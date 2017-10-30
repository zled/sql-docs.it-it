---
title: Numero ordinale (MDX) | Documenti Microsoft
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
- Ordinal
dev_langs:
- kbMDX
helpviewer_keywords:
- Ordinal function
ms.assetid: 9d416c39-da4a-4f0d-8d85-a76af5df0a87
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b848698799bc0c620d9592e90f508f01ac279f6f
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="ordinal-mdx"></a>Ordinal (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore ordinale in base zero associato a un livello.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>Argomenti  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
## <a name="remarks"></a>Osservazioni  
 Il **ordinale** viene spesso utilizzata in combinazione con il **IIF** e **CurrentMember** funzioni per visualizzare in modo condizionale valori differenti a diversi livelli di gerarchia, in base alla posizione ordinale di ogni cella specifica nel risultato della query. Ad esempio, è possibile utilizzare il **ordinale** funzione per eseguire calcoli a determinati livelli e visualizzare un valore predefinito "N/d" ad altri livelli.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il numero ordinale corrispondente al livello Calendar Quarter nella gerarchia Calendar.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

