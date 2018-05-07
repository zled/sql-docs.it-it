---
title: Istruzione CALCULATE (MDX) | Documenti Microsoft
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
- CALCULATE
dev_langs:
- kbMDX
helpviewer_keywords:
- CALCULATE statement
ms.assetid: 41e196a1-d49e-487b-a42a-73e5d441ed1b
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 855ba79dcfdd54bcd44353d0f851d0151926307a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-scripting---calculate"></a>Creazione di script MDX, calcolare
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Consente di popolare tutte le celle di un cubo con un valore di aggregazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Argomenti  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Quando si crea un cubo utilizzando [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], l'istruzione CALCULATE viene automaticamente inclusa come prima istruzione nello script MDX del cubo. L'istruzione CALCULATE indica alle celle del cubo di eseguire l'aggregazione a partire dalle celle con una granularità più bassa. Dopo l'aggregazione di una cella, l'utilizzo delle espressioni per popolare le celle con una granularità più bassa influisce sul valore aggregato delle celle con una granularità superiore. Sebbene questa aggregazione sia consigliabile nella maggior parte dei casi, è possibile non applicarla o eseguire altre istruzioni prima di questa.  
  
 L'istruzione CALCULATE non può essere inclusa in un sottocubo nidificato all'interno dello script MDX. Un sottocubo nidificato viene definito utilizzando l'istruzione SCOPE. Per ulteriori informazioni sull'istruzione SCOPE, vedere [istruzione SCOPE &#40;MDX&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  I membri calcolati non vengono aggregati.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni di Scripting MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Nozioni fondamentali sullo Scripting MDX & #40; Analysis Services & #41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Definire le assegnazioni e altri comandi script](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
