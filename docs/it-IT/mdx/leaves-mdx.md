---
title: Lascia (MDX) | Documenti Microsoft
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
- LEAVES
dev_langs:
- kbMDX
helpviewer_keywords:
- Leaves function
ms.assetid: 09f908aa-1b2d-4af9-8c8d-c023915241b2
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c9ac580c71d1c82876a41953d6f8b5411dc7dd55
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="leaves-mdx"></a>Leaves (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un set composto da tutti gli attributi (facoltativamente limitato a quelli appartenenti a una dimensione specifica). Per ogni attributo x nel set restituito, se x è l'attributo di granularità o è correlato direttamente o indirettamente all'attributo di granularità, la granularità viene impostata sull'attributo x senza influire sulla sezione. Il **lascia** funzione è progettata per l'utilizzo all'interno di un'istruzione SCOPE o sul lato sinistro di un'assegnazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Dimension_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una dimensione.  
  
## <a name="remarks"></a>Osservazioni  
 I membri foglia sono tuple ottenute eseguendo il cross join del livello più basso di tutte le gerarchie dell'attributo. I membri calcolati vengono esclusi.  
  
-   Se viene specificato un nome di dimensione, il **lascia** funzione restituisce un set che contiene i membri foglia dell'attributo chiave della dimensione specificata.  
  
-   Se la dimensione è associata a più gruppi di misure, viene utilizzato il gruppo nell'ambito corrente.  
  
-   Se non si specifica un nome di dimensione, la funzione restituirà un set che contiene i membri foglia dell'intero cubo.  
  
    > [!NOTE]  
    >  Se l'espressione di dimensione viene risolta in una gerarchia e il nome univoco della gerarchia è uguale a quello della dimensione (la proprietà HierarchyUniqueNameStyle della dimensione del cubo è ExcludeDimensionName e il nome della gerarchia corrisponde al nome della dimensione), viene utilizzata la dimensione.  
  
    > [!IMPORTANT]  
    >  Se la granularità nei gruppi di misure nell'ambito corrente non è la stessa per tutti gli attributi, viene generato un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
