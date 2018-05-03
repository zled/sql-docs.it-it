---
title: SetToStr (MDX) | Documenti Microsoft
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
f1_keywords:
- SETTOSTR
dev_langs:
- kbMDX
helpviewer_keywords:
- SetToStr function
ms.assetid: b761e002-26cd-460e-b424-fb8e306746fa
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c07337023c90e9ac3c2dd9ec04da276b0c891641
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="settostr-mdx"></a>SetToStr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce una stringa in formato MDX (Multidimensional Expression) corrispondente al set specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione viene utilizzata per trasferire una rappresentazione stringa di un set a una funzione esterna per l'analisi. La stringa restituita è racchiusa tra parentesi graffe {}, con ogni elemento nel set di separati da una virgola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita una stringa contenente tutti i membri della gerarchia dell'attributo Geography.Country.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
