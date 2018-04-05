---
title: Query su dati multidimensionali con MDX | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multidimensional data [Analysis Services], querying
ms.assetid: e0a5dd60-35a3-4a4f-b36f-52ecea814886
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 1c7afc85473545c4801973c3fdf8b19a95141917
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="querying-multidimensional-data-with-mdx"></a>Query su dati multidimensionali con MDX
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]MDX (Multidimensional Expressions) è il linguaggio di query che consente di utilizzare e recuperare dati multidimensionali in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Il linguaggio MDX è basato sulla specifica XML for Analysis (XMLA), con estensioni specifiche per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. MDX usa espressioni costituite da identificatori, valori, istruzioni, funzioni e operatori che possono essere valutate da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per recuperare un oggetto, ad esempio un set o un membro, oppure un valore scalare, ad esempio una stringa o un numero.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] le query e le espressioni MDX vengono usate per le operazioni seguenti:  
  
-   Restituire dati a un'applicazione client da un cubo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
-   Modellare i risultati delle query.  
  
-   Eseguire attività di progettazione per i cubi, tra cui la definizione di membri calcolati, set denominati, assegnazioni con ambito e indicatori di prestazioni chiave (KPI).  
  
-   Eseguire attività di amministrazione, inclusa la sicurezza di dimensioni e celle.  
  
 MDX è in apparenza simile sotto numerosi aspetti alla sintassi SQL in genere utilizzata con i database relazionali. MDX non è tuttavia un'estensione del linguaggio SQL, rispetto al quale presenta molte differenze. Per creare espressioni MDX per la progettazione o la sicurezza dei cubi oppure per creare query MDX in grado di restituire e modellare dati multidimensionali, è necessario conoscere i concetti di base della modellazione multidimensionale e MDX, degli elementi della sintassi MDX, nonché degli operatori, delle istruzioni e delle funzioni MDX.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Concetti chiave di MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)|È possibile usare espressioni MDX (Multidimensional Expression) per eseguire query su dati multidimensionali o creare espressioni MDX da usare all'interno di un cubo, ma è prima necessario comprendere i concetti e la terminologia relativi alle dimensioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|[Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)|Nel linguaggio MDX (Multidimensional Expressions) è possibile eseguire query su oggetti multidimensionali, ad esempio un cubo, e restituire set di celle multidimensionali contenenti i dati del cubo. In questo argomento e negli argomenti correlati viene fornita una panoramica delle query MDX.|  
|[Nozioni fondamentali sullo scripting MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], uno script MDX (Multidimensional Expressions) è costituito da una o più espressioni o istruzioni MDX che popolano un cubo tramite calcoli.<br /><br /> Uno script MDX definisce il processo di calcolo per un cubo ed è considerato parte del cubo stesso. La modifica di uno script MDX associato a un cubo comporta pertanto la modifica immediata del processo di calcolo per il cubo.<br /><br /> Per creare script MDX, è possibile usare Progettazione cubi in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi della sintassi MDX &#40;MDX&#41;](../../../mdx/mdx-syntax-elements-mdx.md)   
 [Guida di riferimento al linguaggio MDX](../../../mdx/mdx-language-reference-mdx.md)  
  
  
