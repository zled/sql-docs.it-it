---
title: "Modifiche di rilievo nelle funzionalit&#224; di Analysis Services in SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifiche di rilievo [Analysis Services]"
  - "aggiornamento di Analysis Services"
ms.assetid: aeb02542-5a6c-458c-a110-13413dd3e9d9
caps.latest.revision: 55
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 53
---
# Modifiche di rilievo nelle funzionalit&#224; di Analysis Services in SQL Server 2016
  Una *modifica di rilievo* causa l'interruzione del funzionamento di un modello di dati, un codice di applicazione o uno script dopo l'aggiornamento del modello o del server.  
  
> [!NOTE]  
>  Al contrario, una *modifica al comportamento* corrisponde a una modifica del codice che non causa l'interruzione del funzionamento di un modello o un'applicazione, ma che presenta un comportamento diverso da una versione precedente.  Esempi di modifiche al comportamento possono essere la modifica di un valore predefinito o la disattivazione di una configurazione delle proprietà o delle opzioni che precedentemente era consentita. Per altre informazioni sulle modifiche al comportamento in questa versione, vedere [Behavior Changes to Analysis Services Features in SQL Server 2016](../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md).  
  
## Aggiornamento della versione .NET 4.0  
 Le librerie client Analysis Services Management Objects (AMO), ADOMD.NET e Tabular Object Model (TOM) in [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] ora sono destinate al runtime .NET 4.0. Questa modifica può essere di rilievo per le applicazioni destinate a .NET 3.5. Le applicazioni che usano versioni più recenti di questi assembly devono ora essere destinate a .NET 4.0 o versione successiva.  
  
## Aggiornamento della versione AMO  
 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] è un aggiornamento di versione per [Analysis Services Management Objects &#40;AMO&#41;](../Topic/Analysis%20Services%20Management%20Objects%20\(AMO\).md) e costituisce una modifica sostanziale in determinate circostanze.  L'esecuzione del codice e degli script esistenti che chiamano AMO continuerà proprio come prima dell'aggiornamento da una versione precedente. Tuttavia, se è necessario *ricompilare* l'applicazione e la destinazione è un'istanza di [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] , è necessario aggiungere lo spazio dei nomi seguente per rendere operativo il codice o lo script:  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 Ora è necessario lo spazio dei nomi [Microsoft.AnalysisServices.Core](../Topic/Microsoft.AnalysisServices.Core.md) quando si fa riferimento all'assembly Microsoft.AnalysisServices nel codice. Gli oggetti che precedentemente erano presenti solo nello spazio dei nomi **Microsoft.AnalysisServices** vengono spostati nello spazio dei nomi principale in questa versione se l'oggetto viene usato nello stesso modo in scenari sia in formato tabulare che multidimensionale.  Ad esempio, le API correlate al server vengono rilocate allo spazio dei nomi principale.  
  
 Anche se ora esistono più spazi dei nomi, entrambi presenti nello stesso assembly (Microsoft.AnalysisServices.dll).  
  
## Modifiche di XEvent DISCOVER  
 Per un supporto migliore dello streaming XEvent DISCOVER in SSMS per [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], `DISCOVER_XEVENT_TRACE_DEFINITION` è sostituito con le seguenti tracce XEvent:  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  
  
## Vedere anche  
 [Analysis Services Backward Compatibility](../analysis-services/analysis-services-backward-compatibility.md)  
  
  