---
title: "Nozioni fondamentali sullo scripting MDX (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cubi [Analysis Services], script"
  - "calcoli [Analysis Services], script"
  - "MDX [Analysis Services], script"
  - "script [MDX]"
  - "cubi [Analysis Services], calcoli"
  - "espressioni MDX [Analysis Services], script"
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# Nozioni fondamentali sullo scripting MDX (Analysis Services)
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], uno script MDX è costituito da una o più espressioni o istruzioni MDX che popolano un cubo tramite calcoli.  
  
 Uno script MDX definisce il processo di calcolo per un cubo ed è considerato parte del cubo stesso. La modifica di uno script MDX associato a un cubo comporta pertanto la modifica immediata del processo di calcolo per il cubo.  
  
 Per creare script MDX, è possibile usare Progettazione cubi in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Per altre informazioni, vedere [Definire le assegnazioni e altri comandi script](../../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md) e [Introduction to MDX Scripting in Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892) (Introduzione alla creazione di script MDX in Microsoft SQL Server 2005).  
  
 Per problemi di prestazioni relativi a query e calcoli MDX, vedere la sezione relativa all'ottimizzazione MDX nella [guida alle prestazioni di SQL Server Analysis Services](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Script MDX di base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)|Include informazioni dettagliate sullo script MDX di base, compreso lo script MDX predefinito inserito in ogni cubo, e sui principi generali di funzionamento degli script MDX nei cubi di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Gestione di ambito e contesto &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/managing-scope-and-context-mdx.md)|Descrive come usare l'istruzione [CALCULATE](../Topic/CALCULATE%20Statement%20\(MDX\).md), l'istruzione [SCOPE](../Topic/SCOPE%20Statement%20\(MDX\).md) e la funzione [This](../../../mdx/this-mdx.md) per gestire il contesto e l'ambito in uno script MDX.|  
|[Utilizzo di variabili e parametri &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|Descrive come usare le variabili e i parametri in uno script MDX.|  
|[Gestione degli errori &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/error-handling-mdx.md)|Illustra la gestione degli errori in uno script MDX.|  
|[Istruzioni e funzioni MDX supportate &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/supported-mdx-mdx.md)|Include un elenco di istruzioni, funzioni e operatori MDX supportati negli script MDX.|  
  
## Vedere anche  
 [Guida di riferimento al linguaggio MDX](../../../mdx/mdx-language-reference-mdx.md)  
  
  