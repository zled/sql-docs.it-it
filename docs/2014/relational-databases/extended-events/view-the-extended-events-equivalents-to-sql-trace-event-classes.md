---
title: Visualizzare gli eventi estesi equivalenti alle classi di eventi di Traccia SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, extended events equivalents
- extended events [SQL Server], SQL Trace equivalents
- extended events [SQL Server], user configurable events
ms.assetid: 7f24104c-201d-4361-9759-f78a27936011
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 838a5a3c6b2693ad1d96cab131dd59864ca4788c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123891"
---
# <a name="view-the-extended-events-equivalents-to-sql-trace-event-classes"></a>Visualizzare gli eventi estesi equivalenti alle classi di evento di traccia SQL
  Se si desidera utilizzare gli eventi estesi per raccogliere dati degli eventi equivalenti a colonne e classi di evento di Traccia SQL, è utile comprendere in che modo viene eseguito il mapping degli eventi di Traccia SQL a eventi e azioni degli eventi estesi.  
  
 È possibile utilizzare la procedura seguente per visualizzare gli eventi e le azioni degli eventi estesi equivalenti a ogni evento di Traccia SQL e alle colonne associate.  
  
## <a name="to-view-the-extended-events-equivalents-to-sql-trace-events-using-query-editor"></a>Per visualizzare gli eventi estesi equivalenti agli eventi di Traccia SQL tramite l'editor di query  
  
-   Dall'editor di query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eseguire la query seguente:  
  
    ```  
    USE MASTER;  
    GO  
    SELECT DISTINCT  
       tb.trace_event_id,  
       te.name AS 'Event Class',  
       em.package_name AS 'Package',  
       em.xe_event_name AS 'XEvent Name',  
       tb.trace_column_id,  
       tc.name AS 'SQL Trace Column',  
       am.xe_action_name as 'Extended Events action'  
    FROM (sys.trace_events te LEFT OUTER JOIN sys.trace_xe_event_map em  
       ON te.trace_event_id = em.trace_event_id) LEFT OUTER JOIN sys.trace_event_bindings tb  
       ON em.trace_event_id = tb.trace_event_id LEFT OUTER JOIN sys.trace_columns tc  
       ON tb.trace_column_id = tc.trace_column_id LEFT OUTER JOIN sys.trace_xe_action_map am  
       ON tc.trace_column_id = am.trace_column_id  
    ORDER BY te.name, tc.name  
    ```  
  
 Quando si visualizzano i risultati, notare quanto segue:  
  
-   Se tutte le colonne restituiscono NULL, ad eccezione della colonna Event Class, significa che non è stata eseguita la migrazione della classe di evento da Traccia SQL.  
  
-   Se solo il valore nella colonna azione Extended Events è NULL, significa che una delle condizioni seguenti è vera:  
  
    -   Per la colonna di Traccia SQL viene eseguito il mapping a uno dei campi dati associati con l'evento degli eventi estesi.  
  
        > [!NOTE]  
        >  Ogni evento degli eventi estesi dispone di un set predefinito di campi dati che vengono inclusi automaticamente nel set di risultati.  
  
    -   La colonna relativa all'azione non dispone di un equivalente significativo degli eventi estesi. Ne è un esempio la colonna EventClass in Traccia SQL. Questo colonna non è necessaria negli eventi estesi in quanto il nome dell'evento svolge lo stesso ruolo.  
  
-   Per le classi di eventi di Traccia SQL configurabili dall'utente (da UserConfigurable:1 a UserConfigurable:9), la funzionalità Eventi estesi usa un singolo evento in sostituzione di tali classi. Il nome dell'evento è user_event. Questo evento viene generato usando sp_trace_generateevent, che è la stessa stored procedure usata da Traccia SQL. L'evento user_event viene restituito indipendentemente dall'ID evento passato alla stored procedure. Viene tuttavia restituito un campo event_id come parte dei dati dell'evento. In questo modo, è possibile compilare un predicato basato sull'ID evento. Se, ad esempio, si usa UserConfigurable:0 (event ID = 82) nel codice, è possibile aggiungere l'evento user_event alla sessione e specificare un predicato di 'event_id = 82'. Non è quindi necessario modificare il codice perché la stored procedure sp_trace_generateevent genera l'evento user_event degli eventi estesi e la classe di evento di Traccia SQL equivalente.  
  
-   Se tutte le colonne restituiscono NULL, ad eccezione della colonna Event Class, significa che non è stata eseguita la migrazione della classe di evento da Traccia SQL.  
  
-   Se solo il valore nella colonna azione Extended Events è NULL, significa che una delle condizioni seguenti è vera:  
  
    -   Per la colonna di Traccia SQL viene eseguito il mapping a uno dei campi dati associati con l'evento degli eventi estesi.  
  
        > [!NOTE]  
        >  Ogni evento degli eventi estesi dispone di un set predefinito di campi dati che vengono inclusi automaticamente nel set di risultati.  
  
    -   La colonna relativa all'azione non dispone di un equivalente significativo degli eventi estesi. Ne è un esempio la colonna EventClass in Traccia SQL. Questo colonna non è necessaria negli eventi estesi in quanto il nome dell'evento svolge lo stesso ruolo.  
  
-   Per le classi di eventi di Traccia SQL configurabili dall'utente (da UserConfigurable:1 a UserConfigurable:9), la funzionalità Eventi estesi usa un singolo evento in sostituzione di tali classi. Il nome dell'evento è user_event. Questo evento viene generato usando sp_trace_generateevent, che è la stessa stored procedure usata da Traccia SQL. L'evento user_event viene restituito indipendentemente dall'ID evento passato alla stored procedure. Viene tuttavia restituito un campo event_id come parte dei dati dell'evento. In questo modo, è possibile compilare un predicato basato sull'ID evento. Se, ad esempio, si usa UserConfigurable:0 (event ID = 82) nel codice, è possibile aggiungere l'evento user_event alla sessione e specificare un predicato di 'event_id = 82'. Non è quindi necessario modificare il codice perché la stored procedure sp_trace_generateevent genera l'evento user_event degli eventi estesi e la classe di evento di Traccia SQL equivalente.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_generateevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)  
  
  
