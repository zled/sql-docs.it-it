---
title: Unorder-(MDX) | Documenti Microsoft
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
- UNORDER
dev_langs:
- kbMDX
helpviewer_keywords:
- Unorder function
ms.assetid: a805df2a-6320-45bc-989f-90e85faf027f
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2593c6f22915cbe5615f8d104b718fd4b3a7d6a5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="unorder-mdx"></a>Unorder (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Rimuove l'ordinamento imposto da un set specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Osservazioni  
 Il **Unorder** funzione rimuove qualsiasi ordinamento imposto sulle tuple contenute nel set da qualsiasi altra funzione o istruzione, ad esempio il [ordine](../mdx/order-mdx.md) (funzione). L'ordine delle tuple nel set restituito dal **Unorder** funzione è indeterminato.  
  
 Il **Unorder** funzione viene utilizzata come hint per [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per l'ottimizzazione di query per l'elaborazione dei set. Se l'ordine delle tuple all'interno di un set è importante per una query o un calcolo, utilizzando il **Unorder** funzione può fornire un miglioramento delle prestazioni in tali casi. Ad esempio, il [NonEmpty (MDX)](../mdx/nonempty-mdx.md) funzione possibile ottenere prestazioni migliori quando il set specificato a questa funzione è ordinato rispetto ai casi [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] deve mantenere l'ordine, anche se con [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], query processor tenta di eseguire automaticamente questa funzione per molte funzioni, ad esempio **somma** e **aggregazione**. Il miglioramento delle prestazioni dell'utilizzo di **Unorder** è apprezzabile in set molto grandi, costituiti da milioni di tuple.  
  
## <a name="example"></a>Esempio  
 Nello pseudocodice seguente viene illustrata la sintassi per questa funzione.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
