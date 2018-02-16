---
title: Prospettive | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 815d1c6d75613855d84e9bb7ab6e5c369d97bf81
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="perspectives"></a>Prospettive
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Una prospettiva è una definizione che consente agli utenti di visualizzare un cubo in modo più semplice. Una prospettiva rappresenta un subset delle caratteristiche di un cubo e consente agli amministratori di creare viste di un cubo, in modo tale che gli utenti possano concentrarsi su dati per loro più importanti. Una prospettiva contiene subset di tutti gli oggetti di un cubo, ma non può includere elementi non definiti nel cubo padre.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.Perspective> semplice è composto da informazioni di base, dimensioni, gruppi di misure, calcoli, indicatori KPI e azioni. Le informazioni di base includono il nome e la misura predefinita della prospettiva. Le dimensioni sono un subset delle dimensioni del cubo. I gruppi di misure sono un subset dei gruppi di misure del cubo. I calcoli sono un subset dei calcoli relativi al cubo. Gli indicatori KPI sono un subset degli indicatori KPI del cubo. Le azioni sono un subset delle azioni del cubo.  
  
 Per utilizzare la prospettiva, è necessario aggiornare ed elaborare un cubo.  
  
 I cubi possono essere oggetti molto complessi per gli utenti di esplorare in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Un singolo cubo può rappresentare il contenuto di un data warehouse completo, con più gruppi di misure che rappresentano più tabelle dei fatti e più dimensioni in base a più tabelle delle dimensioni. Un cubo di questo tipo può essere molto complesso e potente e può quindi costituire un ostacolo per gli utenti che hanno necessità di interagire con solo una parte ridotta del cubo per soddisfare determinati requisiti di Business Intelligence e creazione di report.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è possibile utilizzare una prospettiva per ridurre la complessità percepita di un cubo in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Una prospettiva definisce subset visualizzabili del cubo in grado di offrire punti di vista mirati, specifici di un'attività aziendale o di un'applicazione. La prospettiva controlla la visibilità degli oggetti contenuti in un cubo. In una prospettiva è possibile visualizzare o nascondere gli oggetti seguenti:  
  
-   Dimensioni  
  
-   Attributi  
  
-   Gerarchie  
  
-   Gruppi di misure  
  
-   Misure  
  
-   Indicatori di prestazioni chiave (KPI)  
  
-   Calcoli (membri calcolati, set denominati e comandi script)  
  
-   Azioni  
  
 Ad esempio, il **Adventure Works** cubo il [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] esempio [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database contiene undici gruppi di misure e ventuno dimensioni di cubo diverse, corrispondenti a vendite, previsioni di vendita e dati finanziari. Un'applicazione client può fare riferimento direttamente al cubo completo, tuttavia questo punto di vista potrebbe rivelarsi eccessivo per un utente che desidera estrarre solo informazioni di vendita di base. In alternativa, è possibile utilizzare lo stesso utente il **gli obiettivi di vendita** prospettiva per limitare la visualizzazione del **Adventure Works** cubo per solo gli oggetti pertinenti alle previsioni di vendita.  
  
 Gli oggetti di un cubo che non sono visibili all'utente tramite una prospettiva possono comunque contenere riferimenti diretti e possono essere recuperati utilizzando istruzioni XMLA (XML for Analysis), MDX (Multidimensional Expressions) o DMX (Data Mining Extensions). Le prospettive non limitano l'accesso agli oggetti di un cubo e non dovrebbero essere utilizzate a questo scopo, ma piuttosto come soluzioni per migliorare l'accesso degli utenti a un cubo.  
  
 Una prospettiva è una vista di sola lettura del cubo. Non è infatti possibile rinominare o modificare gli oggetti di un cubo utilizzando una prospettiva. Analogamente, il comportamento o le caratteristiche di un cubo, ad esempio l'utilizzo dei totali visualizzati, non possono essere modificati utilizzando una prospettiva.  
  
## <a name="security"></a>Sicurezza  
 Le prospettive non sono pensate per essere utilizzate come meccanismo di sicurezza, ma piuttosto come strumento per migliorare le prestazioni delle applicazioni di Business Intelligence. Tutte le impostazioni di sicurezza di una determinata prospettiva vengono ereditate dal cubo sottostante. Ad esempio, le prospettive non possono accedere agli oggetti di un cubo se l'utente non dispone già del relativo diritto di accesso. È quindi necessario risolvere la sicurezza del cubo prima di poter fornire l'accesso agli oggetti del cubo tramite una prospettiva.  
  
  
