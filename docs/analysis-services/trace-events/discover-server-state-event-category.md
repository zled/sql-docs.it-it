---
title: Individuare la categoria di eventi dello stato di Server | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83bad9f141c0da4918f7558f0b34b7816e51d737
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="discover-server-state-event-category"></a>Individuazione stato del server - categoria di eventi
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoria di eventi Individuazione stato del server include le classi di evento descritte nella tabella seguente.  
  
|Event Class|ID evento|Description|  
|-----------------|--------------|-----------------|  
|Server State Discover Begin|33|Raccoglie tutti gli eventi di inizio individuazione dello stato del server XMLA dall'avvio della traccia.|  
|Server State Discover Data|34|Raccoglie tutti gli eventi di dati di individuazione dello stato del server XMLA dall'avvio della traccia. Tali eventi acquisiscono il contenuto della risposta alla richiesta di individuazione.|  
|Server State Discover End|35|Raccoglie tutti gli eventi di fine individuazione dello stato del server XMLA dall'avvio della traccia.|  
  
 Per informazioni sulle colonne associate a ogni classe di evento degli eventi query, vedere [Colonne di dati degli eventi di individuazione dello stato del server](../../analysis-services/trace-events/discover-server-state-events-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
