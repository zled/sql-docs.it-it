---
title: Categoria di eventi report di stato | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8bcfa530f87d7a8caaee6814c2e2e2282e2783ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055087"
---
# <a name="progress-reports-event-category"></a>categoria di eventi di report di stato
  La categoria di eventi di report di stato include le classi di eventi descritte nella tabella seguente.  
  
|Event Class|ID evento|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|Raccoglie tutti gli eventi di inizio dei report di stato dall'avvio della traccia.|  
|Progress Report End|6|Raccoglie tutti gli eventi di fine dei report di stato dall'avvio della traccia.|  
|Progress Report Current|7|Raccoglie tutti gli eventi di report dello stato corrente dall'avvio della traccia. Durante l'elaborazione, ad esempio, i report dello stato corrente includono le informazioni di elaborazione sugli oggetti da elaborare, ad esempio dimensioni, partizioni, cubo e così via.|  
|Progress Report Error|8|Raccoglie tutti gli eventi di errore nei report di stato dall'avvio della traccia.|  
  
 Ogni evento Inizio dei report di stato inizia con un flusso di eventi di stato e viene terminato con un evento Fine dei report di stato. Il flusso può includere un numero qualsiasi di eventi Report dello stato corrente ed Errore nel report di stato.  
  
 Per informazioni sulle colonne associate a ogni classe di evento inclusa nella categoria Report di stato, vedere [Colonne di dati degli eventi di report di stato](progress-reports-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gli eventi di traccia di Analysis Services](analysis-services-trace-events.md)  
  
  