---
title: StrToSet (MDX) | Documenti Microsoft
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
f1_keywords: STRTOSET
dev_langs: kbMDX
helpviewer_keywords: StrToSet function
ms.assetid: 1700a563-6527-450a-8d3b-975c65bb6e51
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 98095d2d8910a9e69d74712b99e1ccc7954826ae
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="strtoset-mdx"></a>StrToSet (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il set specificato da una stringa con formattazione MDX (Multidimensional Expression).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Specification*  
 Espressione stringa valida che specifica, direttamente o indirettamente, un set.  
  
## <a name="remarks"></a>Osservazioni  
 Il **StrToSet** funzione restituisce il set specificato nell'espressione stringa. Il **StrToSet** funzione viene in genere utilizzata con funzioni definite dall'utente per restituire una specifica di set da una funzione esterna a un'istruzione MDX o quando una query MDX con parametri.  
  
-   Quando viene utilizzato il flag CONSTRAINED, la specifica di set deve includere nomi di membri completi o non qualificati o un set di tuple contenenti nomi di membri completi o non qualificati racchiusi tra parentesi graffe {}. Questo flag viene utilizzato per ridurre il rischio di attacchi intrusivi tramite la stringa specificata. Se si specifica una stringa non direttamente risolvibile in nomi di membro completi o non qualificati, verrà visualizzato l'errore seguente: "Le restrizioni imposte dal flag CONSTRAINED nella funzione STRTOSET sono state violate".  
  
-   Quando non viene utilizzato il flag CONSTRAINED, è possibile risolvere la specifica di set specificata in un'espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
-   Per comprendere meglio le differenze tra set e membri, vedere Utilizzo di espressioni set e Utilizzo delle espressioni di membro.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce il set di membri della gerarchia dell'attributo State-Province tramite la **StrToSet** (funzione). La specifica di set contiene un'espressione set MDX valida.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito un errore a causa del flag CONSTRAINED. Sebbene la specifica di set contenga un'espressione MDX valida, per il flag CONSTRAINED la specifica di set deve includere nomi di membri completi o non qualificati.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituita la misura Reseller Sales Amount per Germania e Canada. La specifica di set inclusa nella stringa specificata contiene nomi di membri completi, come richiesto dal flag CONSTRAINED.  
  
```  
SELECT StrToSet ('{[Geography].[Geography].[Country].[Germany],[Geography].[Geography].[Country].[Canada]}', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
