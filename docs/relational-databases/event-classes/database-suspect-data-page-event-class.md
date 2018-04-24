---
title: Classe di evento Database Suspect Data Page | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- suspect_pages system table
- database mirroring [SQL Server], event notifications
- Database Suspect Data Page event class
ms.assetid: 098e1443-a8a0-425c-9311-0a479b1370ed
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d062eace204c298285f39426f56a954a147e4783
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="database-suspect-data-page-event-class"></a>classe di evento Database Suspect Data Page
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La classe di evento **Database Suspect Data Page** indica quando una pagina viene aggiunta alla tabella [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md) in [msdb](../../relational-databases/databases/msdb-database.md). Includere questa classe di evento nelle tracce che eseguono il monitoraggio dell'occorrenza di pagine sospette.  
  
> [!NOTE]  
>  Questo evento viene generato in modo asincrono dall'inserimento di una riga corrispondente nella tabella **suspect_pages** . Quindi un processo in ascolto per tale evento potrebbe non trovare immediatamente la voce **suspect_pages** corrispondente.  
  
 Quando la classe di evento **Database Suspect Data Page** viene inclusa in una traccia, il relativo overhead è ridotto. L'overhead potrebbe essere maggiore se il numero di pagine sospette aumenta, ad esempio se si stanno verificando problemi in un'unità disco.  
  
## <a name="database-suspect-data-page-event-class-data-columns"></a>Colonne di dati della classe di evento Database Suspect Data Page  
  
|Nome colonna di dati|Tipo di dati|Description|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID del database per il quale è stato generato l'evento della pagina sospetta. Corrisponde alla colonna **database_id** della tabella **suspect_pages** .|3|Sì|  
|**EventClass**|**int**|Il tipo di evento è 213.|27|no|  
|**EventSequence**|**int**|Sequenza della classe di evento nel batch.|51|no|  
|**SPID**|**int**|ID dell'attività [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ha rilevato la pagina sospetta.|12|Sì|  
|**StartTime**|**datetime**|Ora in cui si è verificato l'evento.|14|Sì|  
|**ObjectID**|**int**|ID del file di database contenente la pagina sospetta. Corrisponde alla colonna **file_id** della tabella **suspect_pages** .|22|Sì|  
|**ObjectID2**|**int**|ID della pagina sospetta nel file. Corrisponde alla colonna **page_id** della tabella **suspect_pages** .|56|Sì|  
|**Errore**|**int**|Tipo di errore rilevato. Questo valore corrisponde al valore **event_type** per la pagina nella tabella **suspect_pages** .|31|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Gestione della tabella suspect_pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
