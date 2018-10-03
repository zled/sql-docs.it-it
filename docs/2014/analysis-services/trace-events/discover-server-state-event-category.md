---
title: Individuazione stato del Server-categoria di eventi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Discover Server State event category
- server state events [Analysis Services]
- discover server state events
- event classes [Analysis Services], discover server state
ms.assetid: b62ebf66-d090-4f74-8c83-11ed518b2018
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71e90163b90565aba00c15d00599dd821092d480
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185671"
---
# <a name="discover-server-state-event-category"></a>Individuazione stato del server - categoria di eventi
  La categoria di eventi Individuazione stato del server include le classi di evento descritte nella tabella seguente.  
  
|Event Class|ID evento|Description|  
|-----------------|--------------|-----------------|  
|Server State Discover Begin|33|Raccoglie tutti gli eventi di inizio individuazione dello stato del server XMLA dall'avvio della traccia.|  
|Server State Discover Data|34|Raccoglie tutti gli eventi di dati di individuazione dello stato del server XMLA dall'avvio della traccia. Tali eventi acquisiscono il contenuto della risposta alla richiesta di individuazione.|  
|Server State Discover End|35|Raccoglie tutti gli eventi di fine individuazione dello stato del server XMLA dall'avvio della traccia.|  
  
 Per informazioni sulle colonne associate a ogni classe di evento degli eventi query, vedere [Colonne di dati degli eventi di individuazione dello stato del server](discover-server-state-events-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](analysis-services-trace-events.md)  
  
  
