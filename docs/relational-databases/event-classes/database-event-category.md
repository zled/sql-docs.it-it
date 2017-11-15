---
title: Categoria di eventi Database | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 47cc15d2461cb6fe3ce23a4f683cd2dcee24ff15
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="database-event-category"></a>Categoria di eventi Database
  La categoria di eventi **Database** include classi di evento per il monitoraggio del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Classe di evento Data File Auto Grow](../../relational-databases/event-classes/data-file-auto-grow-event-class.md)|Indica che le dimensioni del file di dati sono aumentate automaticamente. Questo evento non viene generato se le dimensioni del file vengono incrementate in modo esplicito tramite ALTER DATABASE.|  
|[Classe di evento Data File Auto Shrink](../../relational-databases/event-classes/data-file-auto-shrink-event-class.md)|Indica che il file di dati è stato compattato.|  
|[Classe di evento Database Mirroring Connection](../../relational-databases/event-classes/database-mirroring-connection-event-class.md)|Evento generato per indicare lo stato di una connessione di trasporto per il mirroring del database.|  
|[Classe di evento Database Mirroring State Change](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md)|Indica quando lo stato di un database con mirroring cambia.|  
|[Classe di evento Database Suspect Data Page](../../relational-databases/event-classes/database-suspect-data-page-event-class.md)|Indica quando una pagina viene aggiunta alla tabella **suspect_pages** nel database **msdb** .|  
|[Classe di evento Log File Auto Grow](../../relational-databases/event-classes/log-file-auto-grow-event-class.md)|Indica che le dimensioni del file di log sono aumentate automaticamente. L'evento non viene generato se le dimensioni del file di log vengono incrementate in modo esplicito tramite ALTER DATABASE.|  
|[Classe di evento Log File Auto Shrink](../../relational-databases/event-classes/log-file-auto-shrink-event-class.md)|Indica che le dimensioni del file di log sono aumentate automaticamente. L'evento non viene generato se le dimensioni del file di log vengono ridotte in modo esplicito tramite ALTER DATABASE.|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../../relational-databases/extended-events/extended-events.md)  
  
  
