---
title: Riferimento agli operatori MDX (MultiDimensional Expression) | Documenti Microsoft
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
dev_langs: kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], operators
- operators [MDX]
- MDX [Analysis Services], operators
ms.assetid: 1cdb8c31-a5f6-4430-b509-f81344f4622a
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: ddbddfefdaf6b51cbd9cc60eb9111a6c07cfaac8
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="mdx-operator-reference-mdx"></a>Guida di riferimento agli operatori MDX (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Il linguaggio MDX (Multidimensional Expression) supporta operatori sui set, di stringa, aritmetici, logici, di confronto e unari. Nella tabella seguente vengono elencati gli operatori supportati e le relative descrizioni.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[-&#40; Commento &#41; &#40; MDX &#41;](../mdx/comment-mdx-operator-reference.md)|Indica un testo di commento specificato dall'utente.|  
|[-&#40; Ad eccezione di &#41; &#40; MDX &#41;](../mdx/except-mdx-operator.md)|Esegue un'operazione sui set che restituisce la differenza tra due set, rimuovendo i membri duplicati.|  
|[-&#40; Negativo &#41; &#40; MDX &#41;](../mdx/negative-mdx.md)|Esegue un'operazione unaria che restituisce l'opposto del valore di un'espressione numerica.|  
|[-&#40; Sottrarre &#41; &#40; MDX &#41;](../mdx/subtract-mdx.md)|Esegue un'operazione aritmetica che sottrae un numero da un altro.|  
|[&#42; &#40; Crossjoin &#41; &#40; MDX &#41;](../mdx/crossjoin-mdx-operator-reference.md)|Esegue un'operazione sui set che restituisce il prodotto incrociato di due set.|  
|[&#42; &#40; Moltiplicare &#41; &#40; MDX &#41;](../mdx/multiply-mdx.md)|Esegue un'operazione aritmetica di moltiplicazione tra due numeri.|  
|[&#40; divisione &#41; &#40; MDX &#41;](../mdx/divide-mdx-operator-reference.md)|Esegue un'operazione aritmetica di divisione di un numero per un altro.|  
|[^ &#40; Power &#41; &#40; MDX &#41;](../mdx/power-mdx.md)|Esegue un'operazione aritmetica che eleva un numero a un altro numero.|  
|[Commento &#40; MDX &#41;](../mdx/comment-mdx.md)|Indica un testo di commento specificato dall'utente.|  
|[&#40; Commento &#41; &#40; MDX &#41;](../mdx/comment-mdx-double-slash.md)|Evidenzia il testo inserito dall'utente.|  
|[: &#40; Intervallo di &#41; &#40; MDX &#41;](../mdx/range-mdx.md)|Esegue un'operazione sui set che restituisce un set ordinato in modo naturale, in cui i due membri specificati costituiscono gli endpoint e tutti i membri compresi tra questi ultimi vengono inclusi come membri del set.|  
|[+ &#40; Aggiungi &#41; &#40; MDX &#41;](../mdx/add-mdx.md)|Esegue un'operazione aritmetica di somma di due numeri.|  
|[+ &#40; Positivo &#41; &#40; MDX &#41;](../mdx/positive-mdx.md)|Esegue un'operazione unaria che restituisce il valore positivo di un'espressione numerica.|  
|[+ &#40; Concatenazione di stringhe &#41; &#40; MDX &#41;](../mdx/string-concatenation-mdx.md)|Esegue un'operazione di stringa che concatena due o più tuple o stringhe di caratteri oppure una combinazione di stringhe e tuple.|  
|[+ &#40; Unione &#41; &#40; MDX &#41;](../mdx/union-mdx-operator-reference.md)|Esegue un'operazione sui set che restituisce l'unione di due set, rimuovendo i membri duplicati.|  
|[&#60; &#40; Minore di &#41; &#40; MDX &#41;](../mdx/less-than-mdx.md)|Esegue un'operazione di confronto che determina se il valore di un'espressione MDX è minore di quello di un'altra espressione MDX.|  
|[&#60; = &#40; Minore o uguale a &#41; &#40; MDX &#41;](../mdx/less-than-or-equal-to-mdx.md)|Esegue un'operazione di confronto che determina se il valore di un'espressione MDX è minore o uguale a quello di un'altra espressione MDX.|  
|[&#60; &#62; &#40; Non uguale a &#41; &#40; MDX &#41;](../mdx/not-equal-to-mdx.md)|Esegue un'operazione di confronto che determina se il valore di un'espressione MDX è diverso da quello di un'altra espressione MDX.|  
|[= &#40; Uguale a &#41; &#40; MDX &#41;](../mdx/equal-to-mdx.md)|Esegue un'operazione di confronto che determina se il valore di un'espressione MDX è uguale a quello di un'altra espressione MDX.|  
|[&#62; &#40; Maggiore di &#41; &#40; MDX &#41;](../mdx/greater-than-mdx.md)|Esegue un'operazione di confronto che determina se il valore di un'espressione MDX è maggiore di quello di un'altra espressione MDX.|  
|[&#62; = &#40; Maggiore o uguale a &#41; &#40; MDX &#41;](../mdx/greater-than-or-equal-to-mdx.md)|Esegue un'operazione di confronto che determina se il valore di un'espressione MDX è maggiore o uguale a quello di un'altra espressione MDX.|  
|[E &#40; MDX &#41;](../mdx/and-mdx.md)|Esegue la congiunzione logica di due espressioni numeriche.|  
|[È &#40; MDX &#41;](../mdx/is-mdx.md)|Esegue un confronto logico tra due espressioni di oggetto.|  
|[NON &#40; MDX &#41;](../mdx/not-mdx.md)|Esegue la negazione logica di un'espressione numerica.|  
|[O &#40; MDX &#41;](../mdx/or-mdx.md)|Esegue la disgiunzione logica di due espressioni numeriche.|  
|[XOR &#40; MDX &#41;](../mdx/xor-mdx.md)|Esegue un'operazione di esclusione logica tra due espressioni numeriche.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti al linguaggio MDX &#40; MDX &#41;](../mdx/mdx-language-reference-mdx.md)  
  
  
