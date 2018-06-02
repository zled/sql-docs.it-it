---
title: Istruzione CALCULATE (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 603d36e9c099ab6148e2e7c485f9c40ad99f63a8
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579943"
---
# <a name="mdx-scripting---calculate"></a>Creazione di script MDX, calcolare
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Consente di popolare tutte le celle di un cubo con un valore di aggregazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Argomenti  
 None  
  
## <a name="remarks"></a>Remarks  
 Quando si crea un cubo utilizzando [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], l'istruzione CALCULATE viene automaticamente inclusa come prima istruzione nello script MDX del cubo. L'istruzione CALCULATE indica alle celle del cubo di eseguire l'aggregazione a partire dalle celle con una granularità più bassa. Dopo l'aggregazione di una cella, l'utilizzo delle espressioni per popolare le celle con una granularità più bassa influisce sul valore aggregato delle celle con una granularità superiore. Sebbene questa aggregazione sia consigliabile nella maggior parte dei casi, è possibile non applicarla o eseguire altre istruzioni prima di questa.  
  
 L'istruzione CALCULATE non può essere inclusa in un sottocubo nidificato all'interno dello script MDX. Un sottocubo nidificato viene definito utilizzando l'istruzione SCOPE. Per ulteriori informazioni sull'istruzione SCOPE, vedere [istruzione SCOPE &#40;MDX&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  I membri calcolati non vengono aggregati.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni di Scripting MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Nozioni fondamentali sullo Scripting MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Definire le assegnazioni e altri comandi script](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
