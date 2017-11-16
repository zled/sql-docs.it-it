---
title: MDX (Analysis Services) di nozioni fondamentali sullo Scripting | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 11d9dd08521f271284c13a3d93e37fe32d8850b5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>Nozioni fondamentali sullo scripting MDX (Analysis Services)
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], uno script MDX è costituito da una o più espressioni o istruzioni MDX che popolano un cubo tramite calcoli.  
  
 Uno script MDX definisce il processo di calcolo per un cubo ed è considerato parte del cubo stesso. La modifica di uno script MDX associato a un cubo comporta pertanto la modifica immediata del processo di calcolo per il cubo.  
  
 Per creare script MDX, è possibile usare Progettazione cubi in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Per altre informazioni, vedere [Definire le assegnazioni e altri comandi script](../../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md) e [Introduction to MDX Scripting in Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892)(Introduzione alla creazione di script MDX in Microsoft SQL Server 2005).  
  
 Per problemi di prestazioni relativi a query e calcoli MDX, vedere la sezione relativa all'ottimizzazione MDX nella [guida alle prestazioni di SQL Server Analysis Services](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Script MDX di base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)|Include informazioni dettagliate sullo script MDX di base, compreso lo script MDX predefinito inserito in ogni cubo, e sui principi generali di funzionamento degli script MDX nei cubi di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Gestione di ambito e contesto &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/managing-scope-and-context-mdx.md)|Descrive come usare l'istruzione [CALCULATE](../../../mdx/mdx-scripting-calculate.md) , l'istruzione [SCOPE](../../../mdx/mdx-scripting-scope.md) e la funzione [This](../../../mdx/this-mdx.md) per gestire il contesto e l'ambito in uno script MDX.|  
|[Utilizzo di variabili e parametri &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|Descrive come usare le variabili e i parametri in uno script MDX.|  
|[Gestione degli errori &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/error-handling-mdx.md)|Illustra la gestione degli errori in uno script MDX.|  
|[Istruzioni e funzioni MDX supportate &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/supported-mdx-mdx.md)|Include un elenco di istruzioni, funzioni e operatori MDX supportati negli script MDX.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento al linguaggio MDX](../../../mdx/mdx-language-reference-mdx.md)  
  
  

