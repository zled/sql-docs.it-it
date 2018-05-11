---
title: Categoria di eventi di elaborazione delle query | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 576a07ac29c598691ccdbf00cd3ca165edf99c0d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="query-processing-events-category"></a>Categoria degli eventi di elaborazione delle query
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Nella categoria di eventi relativa all'elaborazione di query sono incluse le classi di eventi descritte nella tabella seguente.  
  
|**Event Class**|**ID evento**|**Description**|  
|---------------------|------------------|---------------------|  
|Query Subcube|11|Query sul sottocubo, per Ottimizzazione basata sulle statistiche di utilizzo.|  
|Query Subcube Verbose|12|Query sul sottocubo con informazioni dettagliate. L'abilitazione di questo evento potrebbe causare una riduzione delle prestazioni.|  
|Get Data From Aggregation|60|Risposta alla query tramite il recupero dei dati dall'aggregazione. L'abilitazione di questo evento potrebbe causare una riduzione delle prestazioni.|  
|Get Data From Cache|61|Risposta alla query tramite il recupero dei dati da una delle cache. L'abilitazione di questo evento potrebbe causare una riduzione delle prestazioni.|  
|Query Cube Begin|70|Raccoglie tutti gli eventi Query Cube Begin dall'avvio della traccia.|  
|Query Cube End|71|Raccoglie tutti gli eventi Query Cube End dall'avvio della traccia.|  
|Calculate Non Empty Begin|72|Inizio del calcolo dei valori non vuoti.|  
|Calculate Non Empty Current|73|Stato corrente del calcolo dei valori non vuoti.|  
|Calculate Non Empty End|74|Fine del calcolo dei valori non vuoti.|  
|Serialize Results Begin|75|Inizio della serializzazione dei risultati.|  
|Serialize Results Current|76|Stato corrente della serializzazione dei risultati.|  
|Serialize Results End|77|Fine della serializzazione dei risultati.|  
|Execute MDX Script Begin|78|Inizio dell'esecuzione di script MDX.|  
|Execute MDX Script Current|79|Stato corrente dell'esecuzione di script MDX.|  
|Execute MDX Script End|80|Fine dell'esecuzione di script MDX.|  
|Query Dimension|81|Query su dimensione.|  
|VertiPaq SE Query Begin|82|Query VertiPaq SE|  
|VertiPaq SE Query End|83|Query VertiPaq SE|  
  
 Per informazioni sulle colonne associate a ogni classe di evento di elaborazione query, vedere [Query Processing Events Data Columns](../../analysis-services/trace-events/query-processing-events-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
