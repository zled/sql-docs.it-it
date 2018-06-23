---
title: Categoria di eventi Database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 550d8d2496ff9da641141337978d94968d109cbe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077791"
---
# <a name="database-event-category"></a>Categoria di eventi Database
  La categoria di eventi **Database** include classi di evento per il monitoraggio del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Classe di evento Data File Auto Grow](data-file-auto-grow-event-class.md)|Indica che le dimensioni del file di dati sono aumentate automaticamente. Questo evento non viene generato se le dimensioni del file vengono incrementate in modo esplicito tramite ALTER DATABASE.|  
|[Classe di evento Data File Auto Shrink](data-file-auto-shrink-event-class.md)|Indica che il file di dati è stato compattato.|  
|[Classe di evento Database Mirroring Connection](database-mirroring-connection-event-class.md)|Evento generato per indicare lo stato di una connessione di trasporto per il mirroring del database.|  
|[Classe di evento Database Mirroring State Change](database-mirroring-state-change-event-class.md)|Indica quando lo stato di un database con mirroring cambia.|  
|[Classe di evento Database Suspect Data Page](database-suspect-data-page-event-class.md)|Indica quando una pagina viene aggiunta alla tabella **suspect_pages** nel database **msdb** .|  
|[Classe di evento Log File Auto Grow](log-file-auto-grow-event-class.md)|Indica che le dimensioni del file di log sono aumentate automaticamente. L'evento non viene generato se le dimensioni del file di log vengono incrementate in modo esplicito tramite ALTER DATABASE.|  
|[Classe di evento Log File Auto Shrink](log-file-auto-shrink-event-class.md)|Indica che le dimensioni del file di log sono aumentate automaticamente. L'evento non viene generato se le dimensioni del file di log vengono ridotte in modo esplicito tramite ALTER DATABASE.|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)  
  
  