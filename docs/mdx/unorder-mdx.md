---
title: Unorder-(MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b5e360c8f15eafba2b4565ca41a557c9e1ceda9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743450"
---
# <a name="unorder-mdx"></a>Unorder (MDX)


  Rimuove l'ordinamento imposto da un set specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Remarks  
 Il **Unorder** funzione rimuove qualsiasi ordinamento imposto sulle tuple contenute nel set da qualsiasi altra funzione o istruzione, ad esempio il [ordine](../mdx/order-mdx.md) (funzione). L'ordine delle tuple nel set restituito dal **Unorder** funzione è indeterminato.  
  
 Il **Unorder** funzione viene utilizzata come un hint di ottimizzazione delle query per l'elaborazione dei set. Se l'ordine delle tuple all'interno di un set è importante per una query o un calcolo, utilizzando il **Unorder** funzione può fornire un miglioramento delle prestazioni in tali casi. Ad esempio, il [NonEmpty (MDX)](../mdx/nonempty-mdx.md) funzione possibile ottenere prestazioni migliori quando il set specificato a questa funzione è ordinato rispetto ai casi [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] deve mantenere l'ordine, anche se con [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], query processor tenta di eseguire automaticamente questa funzione per molte funzioni, ad esempio **somma** e **aggregazione**. Il miglioramento delle prestazioni dell'utilizzo di **Unorder** è apprezzabile in set molto grandi, costituiti da milioni di tuple.  
  
## <a name="example"></a>Esempio  
 Nello pseudocodice seguente viene illustrata la sintassi per questa funzione.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
