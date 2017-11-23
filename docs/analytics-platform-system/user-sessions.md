---
title: Sessioni utente (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0425cef2-de4d-4f42-91c5-cb1cd4bb1265
caps.latest.revision: "15"
ms.openlocfilehash: 11c9325b6a16f92ca4d39438fef2a829af3c14b3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="user-sessions"></a>Sessioni utente
Un account di accesso con le autorizzazioni appropriate per gestire le sessioni di tutti gli account di accesso in un dispositivo di SQL Server PDW, inclusa l'esecuzione di queste azioni:  
  
-   Consente di visualizzare le sessioni correnti nel dispositivo, incluse le sessioni sia attive e inattive.  
  
-   Visualizzare le query attive e recente per una sessione.  
  
-   Terminare le sessioni attive.  
  
Queste azioni possono essere eseguite utilizzando il [monitorare il dispositivo tramite la Console di amministrazione](monitor-the-appliance-by-using-the-admin-console.md) o [viste di sistema](tsql-system-views.md) tramite i comandi SQL, come illustrato di seguito.  
  
Le autorizzazioni necessarie per gestire le sessioni utilizzando uno dei metodi sono gli stessi e sono descritte [concedere autorizzazioni per gestire gli account di accesso, utenti e ruoli del Database](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles).  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>Gestire le sessioni tramite la Console di amministrazione  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>Per visualizzare le sessioni correnti tramite la Console di amministrazione  
  
1.  Nel menu in alto, fare clic su **sessioni**.  
  
2.  L'elenco risultante consente di visualizzare tutte le sessioni recenti. Per visualizzare solo le sessioni 'Active' o 'tempo di inattività, fare clic su di **stato** intestazione di colonna per ordinare i risultati in base allo stato.  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>Per visualizzare le query attive e recenti per una sessione utilizzando la Console di amministrazione  
  
1.  Nel menu in alto, fare clic su **sessioni**.  
  
2.  Nell'elenco dei risultati, fare clic sull'ID di sessione della sessione desiderata.  
  
3.  L'elenco di query risultante mostra le query recenti per la sessione. Per informazioni sulla visualizzazione dei dettagli della query, vedere [monitoraggio delle query attive](monitoring-active-queries.md).  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>Per terminare le sessioni tramite la Console di amministrazione  
  
1.  Nel menu in alto, fare clic su **sessioni**.  
  
2.  Trovare l'ID di sessione per la sessione da annullare.  
  
3.  Fare clic su rosso **X** a sinistra dell'ID di sessione per terminare la sessione. Solo le sessioni con stato 'Active' o 'Inattiva' avrà rossa **X**; solo le sessioni possono essere arrestate.  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>Gestire le sessioni tramite viste di sistema e i comandi SQL  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>Per visualizzare le sessioni correnti tramite le viste di sistema  
Utilizzare [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) per generare un elenco delle sessioni correnti.  
  
In questo esempio restituisce il session_id login_name e stato per tutte le sessioni con stato 'Active' o 'Inattivo'.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>Per visualizzare le query attive e recente per una sessione utilizzando viste di sistema  
Consente di visualizzare le query attive e completate di recente associate a una sessione, il [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) e [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) viste. Questa query restituisce un elenco di tutte le sessioni attive o inattive, oltre a qualsiasi query active o recente associata a ogni ID di sessione.  
  
```sql  
SELECT es.session_id, es.login_name, es.status AS sessionStatus,   
er.request_id, er.status AS requestStatus, er.command   
FROM sys.dm_pdw_exec_sessions es   
LEFT OUTER JOIN sys.dm_pdw_exec_requests er   
ON (es.session_id=er.session_id)   
WHERE (es.status='Active' OR es.status='Idle') AND   
(er.status!= 'Completed' AND er.status!= 'Failed' AND er.status!= 'Cancelled');  
```  
  
### <a name="to-end-sessions-by-using-sql-commands"></a>Per terminare le sessioni tramite i comandi SQL  
Utilizzare il [KILL](../t-sql/language-elements/kill-transact-sql.md) comando per terminare una sessione corrente. È necessario l'ID di sessione del processo da terminare, che può essere ottenuto utilizzando il [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) visualizzazione.  
  
In questo esempio, selezionare i login_name, session_id e valori di stato per individuare una sessione in base al nome di account di accesso.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
È possibile terminare le sessioni con stato 'Active' o 'Tempo di inattività' utilizzando il comando KILL.  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
