---
title: IsEmpty (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ISEMPTY
dev_langs:
- kbMDX
helpviewer_keywords:
- IsEmpty function
ms.assetid: b4a50996-61d1-4e23-8003-7d530195ea72
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6cc77efe9a3c7c3c1b9801f0545c785f6934e290
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica se l'espressione valutata corrisponde al valore di cella vuota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Value_Expression*  
 Espressione MDX (Multidimensional Expression) valida che in genere restituisce le coordinate delle celle di un membro o di una tupla.  
  
## <a name="remarks"></a>Osservazioni  
 Il **IsEmpty** risultato della funzione **true** se l'espressione valutata è un valore di cella vuota. In caso contrario, questa funzione restituisce **false**.  
  
> [!NOTE]  
>  La proprietà predefinita di un membro è costituita dal valore del membro.  
  
 Il **IsEmpty** funzione è l'unico modo per verificare in modo affidabile una cella vuota perché il valore di cella vuota ha un significato speciale [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Se la valutazione dell'espressione valore restituisce un errore, la funzione restituirà **false**. Un'espressione valore può restituire un errore, ad esempio, se in un riferimento alle proprietà viene fatto riferimento a una proprietà non valida o inesistente.  
  
 Per ulteriori informazioni sulle celle vuote, vedere la documentazione relativa a OLE DB.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito TRUE se il valore Internet Sales Amount per il membro corrente della gerarchia Fiscal nella dimensione Date restituisce una cella vuota:  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di valori vuoti](../mdx/working-with-empty-values.md)   
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
