---
title: sys.dm_xe_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_xe_sessions_TSQL
- dm_xe_sessions
- sys.dm_xe_sessions_TSQL
- sys.dm_xe_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_sessions dynamic management view
- extended events [SQL Server], views
ms.assetid: defd6efb-9507-4247-a91f-dc6ff5841e17
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5e4e4e6655aeffd54d06cc1cf23aa60208076d18
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34468007"
---
# <a name="sysdmxesessions-transact-sql"></a>sys.dm_xe_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni su una sessione degli eventi estesi attiva. Questa sessione è una raccolta di eventi, azioni e destinazioni.  
    
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|address|**varbinary(8)**|Indirizzo di memoria della sessione. indirizzo è univoco nel sistema locale. Non ammette i valori Null.|  
|name|**nvarchar(256)**|Nome della sessione. nome è univoco nel sistema locale. Non ammette i valori Null.|  
|pending_buffers|**int**|Numero di buffer completi in sospeso per l'elaborazione. Non ammette i valori Null.|  
|total_regular_buffers|**int**|Numero totale di buffer standard associati alla sessione. Non ammette i valori Null.<br /><br /> Nota: I buffer standard vengono utilizzati la maggior parte dei casi. Tali buffer sono di dimensioni sufficienti per contenere molti eventi. In genere, vengono utilizzati tre o più buffer per sessione. Il numero di buffer standard viene determinato automaticamente dal server, in base alla partizione della memoria impostata tramite l'opzione MEMORY_PARTITION_MODE. Le dimensioni dei buffer standard corrispondono al valore dell'opzione MAX_MEMORY (4 MB per impostazione predefinita) diviso per il numero di buffer. Per ulteriori informazioni su MEMORY_PARTITION_MODE e le opzioni di MAX_MEMORY, vedere [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md).|  
|regular_buffer_size|**bigint**|Dimensione in byte dei buffer standard. Non ammette i valori Null.|  
|total_large_buffers|**int**|Numero totale di buffer di grandi dimensioni. Non ammette i valori Null.<br /><br /> Nota: I buffer di grandi dimensioni vengono usati quando un evento è maggiore di un buffer standard. Tali buffer sono riservati in modo esplicito per questo scopo. I buffer di grandi dimensioni vengono allocati all'avvio della sessione degli eventi e vengono ridimensionati in base all'opzione MAX_EVENT_SIZE. Per ulteriori informazioni sull'opzione MAX_EVENT_SIZE, vedere [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md).|  
|large_buffer_size|**bigint**|Dimensione in byte dei buffer di grandi dimensioni. Non ammette i valori Null.|  
|total_buffer_size|**bigint**|Dimensione totale in byte del buffer di memoria utilizzato per archiviare eventi per la sessione. Non ammette i valori Null.|  
|buffer_policy_flags|**int**|Bitmap che indica il comportamento dei buffer di evento della sessione quando tutti i buffer sono completi e viene generato un nuovo evento. Non ammette i valori Null.|  
|buffer_policy_desc|**nvarchar(256)**|Descrizione che indica il comportamento dei buffer di evento della sessione quando tutti i buffer sono completi e viene generato un nuovo evento.  Non ammette i valori Null. buffer_policy_desc può essere uno dei valori seguenti:<br /><br /> Eliminare evento<br /><br /> Non eliminare eventi<br /><br /> Elimina buffer completo<br /><br /> Allocare nuovo buffer|  
|flags|**int**|Bitmap che indica i flag impostata nella sessione. Non ammette i valori Null.|  
|flag_desc|**nvarchar(256)**|Descrizione dei flag impostati nella sessione.  Non ammette i valori Null. flag_desc può essere qualsiasi combinazione delle operazioni seguenti:<br /><br /> Buffer di svuotamento alla chiusura<br /><br /> Dispatcher dedicato<br /><br /> Consentire eventi ricorsivi|  
|dropped_event_count|**int**|Numero di eventi eliminati al completamento dei buffer. Questo valore è **0** se i criteri di buffer sono "Elimina buffer completo" o "Non eliminare eventi". Non ammette i valori Null.|  
|dropped_buffer_count|**int**|Numero di buffer eliminati al completamento dei buffer. Questo valore è **0** se i criteri di buffer sono impostato su "Eliminare evento" o "Non eliminare eventi". Non ammette i valori Null.|  
|blocked_event_fire_time|**int**|Il periodo di tempo in cui è stata bloccata la generazione di eventi quando i buffer erano completi. Questo valore è **0** se i criteri di buffer sono "Elimina buffer completo" o "Eliminare evento". Non ammette i valori Null.|  
|create_time|**datetime**|Ora di creazione della sessione. Non ammette i valori Null.|  
|largest_event_dropped_size|**int**|Dimensione del più grande evento che non si è integrato nel buffer della sessione. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="change-history"></a>Cronologia modifiche  
  
|Contenuto aggiornato|  
|---------------------|  
|Correzione del tipo di dati per le colonne name e blocked_event_fire_time.|  
|Rimozione delle colonne buffer_size e total_buffers.|  
|Aggiungere le colonne delle colonne total_regular_buffers, regular_buffer_size, total_large_buffers, large_buffer_size e total_buffer_size.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

