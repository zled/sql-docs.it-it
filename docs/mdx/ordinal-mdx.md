---
title: Numero ordinale (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Ordinal
dev_langs: kbMDX
helpviewer_keywords: Ordinal function
ms.assetid: 9d416c39-da4a-4f0d-8d85-a76af5df0a87
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2cf441cb5eaaba8ec7b0e14adb1f770464006abb
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="ordinal-mdx"></a>Ordinal (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
  
