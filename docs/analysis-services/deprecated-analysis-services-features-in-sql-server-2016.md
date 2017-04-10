---
title: "Funzionalit&#224; di Analysis Services deprecate in SQL Server 2016 | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Analysis Services, compatibilità con le versioni precedenti"
  - "SSAS, compatibilità con le versioni precedenti"
  - "SQL Server Analysis Services, backward compatibility"
  - "funzionalità deprecate [Analysis Services]"
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
caps.latest.revision: 52
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 52
---
# Funzionalit&#224; di Analysis Services deprecate in SQL Server 2016
  Una *funzionalità deprecata* è una funzionalità che verrà eliminata dal prodotto in una versione futura, ma che è ancora supportata e inclusa nella versione corrente per mantenere la compatibilità con le versioni precedenti. In genere una funzionalità deprecata viene rimossa in una versione principale, spesso all'interno di due versioni dell'annuncio originale. Ad esempio, le funzionalità deprecate annunciate in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] probabilmente non saranno supportate da [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 **Non supportate nella prossima versione principale di SQL Server**  
  
|||  
|-|-|  
|**Category**|**Funzionalità**|  
|Multidimensionale|Partizioni remote|  
|Multidimensionale|Gruppi di misure collegati remoti|  
|Multidimensionale|Writeback dimensionale|  
|Multidimensionale|Dimensioni collegate|  
  
 **Non supportate in una versione futura di SQL Server**  
  
|||  
|-|-|  
|**Category**|**Funzionalità**|  
|Multidimensionale|Notifiche di tabella di SQL Server per il caching attivo.  <br />La sostituzione prevede l'uso del polling per il caching attivo. <br />Vedere [Memorizzazione nella cache attiva &#40;dimensioni&#41;](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md) e [Memorizzazione nella cache attiva &#40;partizioni&#41;](../Topic/Proactive%20Caching%20\(Partitions\).md).|  
|Multidimensionale|Cubi di sessione. Non è prevista alcuna sostituzione.|  
|Multidimensionale|Cubi locali. Non è prevista alcuna sostituzione.|  
|Tabella|I livelli di compatibilità 1100 e 1103 del modello tabulare saranno supportati in una versione futura. La sostituzione prevede l'impostazione di modelli al livello di compatibilità 1200, con conversione delle definizioni di modello in metadati tabulari. Vedere [Livello di compatibilità per i modelli tabulari in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).|  
|Strumenti|SQL Server Profiler per l'acquisizione della traccia<br /><br /> La sostituzione prevede l'uso del profiler di eventi estesi incorporato in SQL Server Management Studio.  <br /> Vedere [Monitorare Analysis Services con eventi estesi di SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Strumenti|Server Profiler per la riproduzione della traccia <br />Sostituzione. Non è prevista alcuna sostituzione.|  
|Trace Management Objects e API di traccia|Oggetti Microsoft.AnalysisServices.Trace (contiene le API per gli oggetti Analysis Services Trace e Replay). La sostituzione è multiparte:<br /><br /> -   Configurazione della traccia:Microsoft.SqlServer.Management.XEvent<br />-   Lettura della traccia:Microsoft.SqlServer.XEvent.Linq<br />-   Riproduzione della traccia: nessuna|  
  
> [!NOTE]  
>  Gli annunci di funzionalità precedentemente deprecate di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] rimangono validi. Considerato che il codice che supporta tali funzionalità non è ancora stato eliminato dal prodotto, molte di queste funzionalità sono ancora presenti in questa versione. Mentre le funzionalità precedentemente deprecate potrebbero essere accessibili, sono ancora considerate deprecate e potrebbero essere fisicamente rimosse dal prodotto in qualsiasi momento durante il rilascio di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. È consigliabile evitare di usare funzionalità deprecate in nuovi modelli o in nuove applicazioni basate su [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## Vedere anche  
 [Analysis Services Backward Compatibility](../analysis-services/analysis-services-backward-compatibility.md)   
 [Funzionalità di Analysis Services non più usate in SQL Server 2016](../analysis-services/discontinued-analysis-services-functionality-in-sql-server-2016.md)  
  
  