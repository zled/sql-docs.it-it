---
title: "Compatibilità con le versioni precedenti di Analysis Services di SQL Server 2017 | Documenti Microsoft"
ms.date: 07/11/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology: 
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
ms.assetid: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 97a19e2f1bf40216163208136d22103eddc89cc2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="analysis-services-backward-compatibility-sql-2017"></a>Compatibilità con le versioni precedenti di Analysis Services (2017 SQL)
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

In questo articolo vengono descritte le modifiche nella disponibilità di funzionalità e comportamento tra la versione corrente e la versione precedente.

## <a name="deprecated-features"></a>Funzionalità deprecate
Oggetto *funzionalità deprecata* verrà interrotto dal prodotto in una versione futura, ma è ancora supportata e inclusa nella versione corrente per garantire la compatibilità con le versioni precedenti. Si consiglia che sospendere l'utilizzo di funzionalità deprecate nei progetti nuovi ed esistenti per garantire la compatibilità con le versioni future.

Le funzionalità seguenti sono deprecate in questa versione:
  
|||  
|-|-|  
|**Modalità/categoria**|**Funzionalità**|
|Multidimensionale|Data Mining|
|Multidimensionale|Gruppi di misure collegati remoti|
|Tabella|Modelli a livello di compatibilità 1100 e 1103|
|Tabella|Proprietà di modello a oggetti tabulare: Column.IsDefaultImage Column.TableDetailPosition, Column.IsDefaultLabel,|


## <a name="discontinued-features"></a>Funzionalità non più supportate
Oggetto *funzionalità non più disponibile* è stata deprecata in una versione precedente. Possono continuare a essere incluso nella versione corrente, ma non è più supportata. Funzionalità non più disponibili potrebbero venire rimosso completamente in un futuro di rilascio o aggiornare.

Le funzionalità seguenti sono state deprecate in una versione precedente e non sono più supportate in questa versione.
  
|||  
|-|-|  
|**Modalità/categoria**|**Funzionalità**|  
|Tabella|Valore della proprietà VertipaqPagingPolicy memoria (2), file mappati Abilita paging su disco l'utilizzo di memoria.|
|Multidimensionale|Partizioni remote|  
|Multidimensionale|Gruppi di misure collegati remoti|  
|Multidimensionale|Writeback dimensionale|  
|Multidimensionale|Dimensioni collegate|
|Strumenti|SQL Server Profiler per l'acquisizione della traccia<br /><br /> La sostituzione prevede l'uso del profiler di eventi estesi incorporato in SQL Server Management Studio.  <br /> Vedere [Monitorare Analysis Services con eventi estesi di SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Strumenti|Server Profiler per la riproduzione della traccia <br />Sostituzione. Non è prevista alcuna sostituzione.|  
|Trace Management Objects e API di traccia|Oggetti Microsoft.AnalysisServices.Trace (contiene le API per gli oggetti Analysis Services Trace e Replay). La sostituzione è multiparte:<br /><br /> -Configurazione della traccia: Microsoft.SqlServer.Management.XEvent<br />-Lettura di traccia: Microsoft.SqlServer.XEvent.Linq<br />-   Riproduzione della traccia: nessuna|  

## <a name="breaking-changes"></a>Modifiche di rilievo
Oggetto *modifica di rilievo* causa una funzionalità, modello di dati, il codice dell'applicazione o script non corretto dopo l'aggiornamento alla versione corrente.

Non sono presenti modifiche di rilievo in questa versione.

## <a name="behavior-changes"></a>Modifiche del comportamento
Oggetto *modifica del comportamento* influisce sul funzionamento di stessa funzionalità nella versione corrente rispetto alla versione precedente. Vengono descritte solo le modifiche di comportamento significativo. Le modifiche nell'interfaccia utente non sono incluse.

Le modifiche al MDSCHEMA_MEASUREGROUP_DIMENSIONS e DISCOVER_CALC_DEPENDENCY, descritti in dettaglio nel [novità di SQL Server 2017 CTP 2.1 per Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/05/18/whats-new-in-sql-server-2017-ctp-2-1-for-analysis-services/) annuncio.


## <a name="see-also"></a>Vedere anche
[Compatibilità con le versioni precedenti di Analysis Services (SQL Server 2016)](analysis-services-backward-compatibility.md)
