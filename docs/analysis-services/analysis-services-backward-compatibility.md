---
title: "Compatibilità con le versioni precedenti di SQL Server 2016 Analysis Services | Documenti Microsoft"
ms.custom: 
ms.date: 07/11/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: misc
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing Analysis Services, backward compatibility
- backward compatibility [Analysis Services]
- compatibility [Analysis Services]
- Analysis Services, backward compatibility
- upgrading Analysis Services
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
ms.assetid: 618b6c3a-e20d-47a9-b2c6-6d848dfba05a
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4b7c58d201f40123ab206d02a4b32948c3d976c2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="analysis-services-backward-compatibility-sql-server-2016"></a>Compatibilità con le versioni precedenti di Analysis Services (SQL Server 2016)
[!INCLUDE[ssas-appliesto-sql2016](../includes/ssas-appliesto-sql2016.md)]

In questo articolo vengono descritte le modifiche nella disponibilità di funzionalità e comportamento tra la versione corrente e quella precedente.

## <a name="deprecated-features"></a>Funzionalità deprecate
Oggetto *funzionalità deprecata* verrà interrotto dal prodotto in una versione futura, ma è ancora supportata e inclusa nella versione corrente per garantire la compatibilità con le versioni precedenti. Si consiglia che sospendere l'utilizzo di funzionalità deprecate nei progetti nuovi ed esistenti per garantire la compatibilità con le versioni future.
  
Le funzionalità seguenti sono deprecate in questa versione:
  
|||  
|-|-|  
|**Modalità/categoria**|**Funzionalità**|  
|Multidimensionale|Partizioni remote|  
|Multidimensionale|Gruppi di misure collegati remoti|  
|Multidimensionale|Writeback dimensionale|  
|Multidimensionale|Dimensioni collegate|   
|Multidimensionale|Notifiche di tabella di SQL Server per il caching attivo.  <br />La sostituzione prevede l'uso del polling per il caching attivo. <br />Vedere [Memorizzazione nella cache attiva &#40;dimensioni&#41;](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md) e [Memorizzazione nella cache attiva &#40;partizioni&#41;](../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|Multidimensionale|Cubi di sessione. Non è prevista alcuna sostituzione.|  
|Multidimensionale|Cubi locali. Non è prevista alcuna sostituzione.|  
|Tabella|I livelli di compatibilità 1100 e 1103 del modello tabulare saranno supportati in una versione futura. La sostituzione è possibile impostare i modelli a livello di compatibilità 1200 o superiore, la conversione di definizioni di modello in metadati tabulari. Vedere [Livello di compatibilità per i modelli tabulari in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).|  
|Strumenti|SQL Server Profiler per l'acquisizione della traccia<br /><br /> La sostituzione prevede l'uso del profiler di eventi estesi incorporato in SQL Server Management Studio.  <br /> Vedere [Monitorare Analysis Services con eventi estesi di SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Strumenti|Server Profiler per la riproduzione della traccia <br />Sostituzione. Non è prevista alcuna sostituzione.|  
|Trace Management Objects e API di traccia|Oggetti Microsoft.AnalysisServices.Trace (contiene le API per gli oggetti Analysis Services Trace e Replay). La sostituzione è multiparte:<br /><br /> -Configurazione della traccia: Microsoft.SqlServer.Management.XEvent<br />-Lettura di traccia: Microsoft.SqlServer.XEvent.Linq<br />-   Riproduzione della traccia: nessuna|  
  
> [!NOTE]  
>  Gli annunci di funzionalità precedentemente deprecate di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] rimangono validi. Considerato che il codice che supporta tali funzionalità non è ancora stato eliminato dal prodotto, molte di queste funzionalità sono ancora presenti in questa versione. Mentre le funzionalità precedentemente deprecate potrebbero essere accessibili, che sono ancora considerate deprecate e potrebbero essere fisicamente rimosse dal prodotto in qualsiasi momento.  

## <a name="discontinued-features"></a>Funzionalità non più supportate
Oggetto *funzionalità non più disponibile* è stata deprecata in una versione precedente. Possono continuare a essere incluso nella versione corrente, ma non è più supportata. Funzionalità non più disponibili potrebbero venire rimosso completamente in un futuro di rilascio o aggiornare.

Le funzionalità seguenti sono state deprecate in una versione precedente e non sono più supportate in questa versione.

|||  
|-|-|  
|**Funzionalità**|**Sostituzione o soluzione alternativa**|  
|[CalculationPassValue &#40;MDX&#41;](../mdx/calculationpassvalue-mdx.md)|Nessuno Questa funzionalità è stata deprecata in SQL Server 2005.|  
|[CalculationCurrentPass &#40;MDX&#41;](../mdx/calculationcurrentpass-mdx.md)|Nessuno Questa funzionalità è stata deprecata in SQL Server 2005.|  
|Hint di Query Optimizer NON_EMPTY_BEHAVIOR|Nessuno Questa funzionalità è stata deprecata in SQL Server 2008.|  
|Assembly COM|Nessuno Questa funzionalità è stata deprecata in SQL Server 2008.|  
|Proprietà intrinseca di cella CELL_EVALUATION_LIST|Nessuno Questa funzionalità è stata deprecata in SQL Server 2005.|  
  
> [!NOTE]  
>  Gli annunci di funzionalità precedentemente deprecate di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] rimangono validi. Considerato che il codice che supporta tali funzionalità non è ancora stato eliminato dal prodotto, molte di queste funzionalità sono ancora presenti in questa versione. Mentre le funzionalità precedentemente deprecate potrebbero essere accessibili, che sono ancora considerate deprecate e potrebbero essere fisicamente rimosse dal prodotto in qualsiasi momento.  

## <a name="breaking-changes"></a>Modifiche di rilievo
Una *modifica di rilievo* causa l'interruzione del funzionamento di un modello di dati, un codice di applicazione o uno script dopo l'aggiornamento del modello o del server.
  
### <a name="net-40-version-upgrade"></a>Aggiornamento della versione .NET 4.0  
 Le librerie client Analysis Services Management Objects (AMO), ADOMD.NET e del modello a oggetti tabulare (TOM) è ora destinato al runtime di .NET 4.0. Questa modifica può essere di rilievo per le applicazioni destinate a .NET 3.5. Le applicazioni che usano versioni più recenti di questi assembly devono ora essere destinate a .NET 4.0 o versione successiva.  
  
### <a name="amo-version-upgrade"></a>Aggiornamento della versione AMO  
 Questa versione è un aggiornamento di versione per [Analysis Services Management Objects &#40; AMO &#41; ](https://msdn.microsoft.com/library/mt436122.aspx) e costituisce una modifica sostanziale in determinate circostanze.  L'esecuzione del codice e degli script esistenti che chiamano AMO continuerà proprio come prima dell'aggiornamento da una versione precedente. Tuttavia, se è necessario *ricompilare* l'applicazione e la destinazione un'istanza di SQL Server 2016 Analysis Services, è necessario aggiungere lo spazio dei nomi seguente per rendere operativo il codice o script:  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 Ora è necessario lo spazio dei nomi [Microsoft.AnalysisServices.Core](https://msdn.microsoft.com/library/microsoft.analysisservices.core.aspx) quando si fa riferimento all'assembly Microsoft.AnalysisServices nel codice. Gli oggetti che precedentemente erano presenti solo nello spazio dei nomi **Microsoft.AnalysisServices** vengono spostati nello spazio dei nomi principale in questa versione se l'oggetto viene usato nello stesso modo in scenari sia in formato tabulare che multidimensionale.  Ad esempio, le API correlate al server vengono rilocate allo spazio dei nomi principale.  
  
 Anche se ora esistono più spazi dei nomi, entrambi presenti nello stesso assembly (Microsoft.AnalysisServices.dll).  
  
### <a name="xevent-discover-changes"></a>Modifiche di XEvent DISCOVER  
 Per migliorare il supporto XEvent individuare lo streaming in SSMS per SQL Server 2016 Analysis Services, `DISCOVER_XEVENT_TRACE_DEFINITION` viene sostituito con le tracce XEvent seguenti:  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  

## <a name="behavior-changes"></a>Modifiche del comportamento
Una *modifica del comportamento* influisce sulle modalità d'uso o di interazione delle funzionalità nella versione corrente rispetto alle versioni precedenti di SQL Server.
  
Modifiche dei valori predefiniti, configurazione manuale necessaria per completare un aggiornamento o un ripristino di funzionalità o una nuova implementazione di una funzionalità esistente sono tutti esempi di modifiche del comportamento nel prodotto.
  
Di seguito sono elencati i comportamenti delle funzionalità cambiati in questa versione, che comunque non interrompono un codice o un modello esistente dopo l'aggiornamento.
  
### <a name="analysis-services-in-sharepoint-mode"></a>Analysis Services in modalità SharePoint
 L'esecuzione della configurazione guidata di PowerPivot non è più necessaria come attività di post-installazione. Questo vale per tutte le versioni supportate di SharePoint che caricano i modelli da corrente di SQL Server 2016 Analysis Services.
  
### <a name="directquery-mode-for-tabular-models"></a>Modalità DirectQuery per modelli tabulari
 *DirectQuery* è una modalità di accesso ai dati per modelli tabulari, in cui l'esecuzione di query avviene in un database relazionale di back-end, recuperando un set di risultati in tempo reale. Viene usata spesso per set di dati di grandi dimensioni per i quali la memoria non è sufficiente o quando i dati sono volatili e si vuole che i dati più recenti vengano restituiti in query in un modello tabulare.
  
 DirectQuery è disponibile come modalità di accesso ai dati nelle ultime versioni rilasciate. In SQL Server 2016 Analysis Services, l'implementazione è stata leggermente modificata, presupponendo che il modello tabulare sia a livello di compatibilità 1200 o superiore. DirectQuery ha meno restrizioni rispetto a prima. Include inoltre diverse proprietà di database.
  
 Se si usa DirectQuery in un modello tabulare esistente, è possibile mantenere il modello al livello di compatibilità attuale pari a 1100 o 1103 e continuare a usare DirectQuery come implementato per tali livelli. In alternativa, è possibile aggiornare a 1200 o superiore per usufruire dei miglioramenti apportati a DirectQuery.
  
 Nessun aggiornamento sul posto di un modello DirectQuery infatti le impostazioni di livelli di compatibilità precedenti non hanno controparti esatte nei livelli di compatibilità 1200 e superiore più recenti. Se si dispone di un modello tabulare esistente eseguito in modalità DirectQuery, è necessario aprire il modello in SQL Server Data Tools, disattivare DirectQuery, impostare il **livello di compatibilità** proprietà al livello 1200 o superiore e quindi riconfigurare DirectQuery proprietà. Vedere [modalità DirectQuery](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md) per informazioni dettagliate.


## <a name="see-also"></a>Vedere anche
[Compatibilità con le versioni precedenti di Analysis Services (SQL Server 2017)](analysis-services-backward-compatibility-sql2017.md)
