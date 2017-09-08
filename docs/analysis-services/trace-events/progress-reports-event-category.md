---
title: Categoria di eventi report di stato | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3489d5176553ba8482646610a048955b93399043
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

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
  
 Per informazioni sulle colonne associate a ogni classe di evento inclusa nella categoria Report di stato, vedere [Colonne di dati degli eventi di report di stato](../../analysis-services/trace-events/progress-reports-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
