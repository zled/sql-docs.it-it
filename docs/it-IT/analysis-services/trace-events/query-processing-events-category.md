---
title: Categoria di eventi di elaborazione delle query | Documenti Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a94b3198-be85-4935-845d-1cd4e121fc94
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 433a7260b538622c118e67411807538c6b4391d3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
