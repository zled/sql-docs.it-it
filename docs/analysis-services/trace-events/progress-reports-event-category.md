---
title: Categoria di eventi report di stato | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6ffc1030149040ed56855cd837c1e4664e64e4c9
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="progress-reports-event-category"></a>categoria di eventi di report di stato
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
  
