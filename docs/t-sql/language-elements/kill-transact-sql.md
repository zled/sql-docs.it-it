---
title: KILL (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/31/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KILL_TSQL
- KILL
dev_langs:
- TSQL
helpviewer_keywords:
- WITH STATUSONLY option
- terminating distributed transactions
- distributed transactions [SQL Server], terminating
- in-doubt transactions
- IDs [SQL Server], user processes
- ending distributed transactions [SQL Server]
- stopping distributed transactions
- session IDs [SQL Server]
- system process termination [SQL Server]
- stopping processes
- ending processes [SQL Server]
- UOW [SQL Server]
- orphaned transactions [SQL Server]
- unit of work [SQL Server]
- process termination [SQL Server]
- KILL statement
- terminating process
ms.assetid: 071cf260-c794-4b45-adc0-0e64097938c0
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: a96601a65e413d4990e9acb77f49c4724bf7b85c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="kill-transact-sql"></a>KILL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Termina un processo utente in base all'ID di sessione o all'unità di lavoro (UOW, Unit Of Work). Se la sessione specificata, ID o del valore UOW è di lavoro da annullare, l'istruzione KILL potrebbe richiedere parecchio tempo, soprattutto quando implica il rollback di una transazione lunga.  
  
 È possibile utilizzare KILL per terminare una connessione normale, operazione che determina internamente la fine delle transazioni associate all'ID di sessione specificato. Questa istruzione può inoltre essere utilizzata per terminare transazioni distribuite orfane e in dubbio quando [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) è in uso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
KILL { session ID | UOW } [ WITH STATUSONLY ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
KILL 'session_id'  
[;]   
```  
  
## <a name="arguments"></a>Argomenti  
 *ID di sessione*  
 ID di sessione del processo da terminare. *ID di sessione* è un integer univoco (**int**) che viene assegnato a ogni connessione utente quando viene stabilita la connessione. Il valore dell'ID di sessione rimane associato alla connessione per tutta la durata della connessione. Al termine della connessione, il valore intero viene rilasciato ed è possibile riassegnarlo a una nuova connessione.  
La query seguente consente di identificare il `session_id` che si desidera eliminare:  
 ```sql  
 SELECT conn.session_id, host_name, program_name,
     nt_domain, login_name, connect_time, last_request_end_time 
FROM sys.dm_exec_sessions AS sess
JOIN sys.dm_exec_connections AS conn
    ON sess.session_id = conn.session_id;
```  
  
*UOW*  
**Si applica a**: ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Identifica l'ID dell'unità di lavoro delle transazioni distribuite. *UOW* è un GUID che è possibile ottenere dalla colonna request_owner_guid della vista a gestione dinamica sys.dm tran_locks. *UOW* può anche essere ottenuto dal log degli errori o tramite il monitoraggio MS DTC. Per ulteriori informazioni sul monitoraggio di transazioni distribuite, vedere la documentazione di MS DTC.  
  
 Utilizzare KILL *UOW* per terminare le transazioni distribuite orfane. Queste transazioni non sono associate a un ID di sessione effettivo, ma sono invece associate in modo artificiale all'ID di sessione -2. Questo ID di sessione consente di semplificare l'identificazione delle transazioni orfane tramite l'esecuzione di una query sulla colonna dell'ID di sessione nelle viste a gestione dinamica sys.dm_tran_locks, sys.dm_exec_sessions o sys.dm_exec_requests.  
  
 WITH STATUSONLY  
 Genera un report di stato su un oggetto specificato *ID sessione* o *UOW* che è in fase di rollback a causa di un'istruzione KILL precedente. Comando KILL WITH STATUSONLY non termina o il rollback di *ID sessione* o *UOW*; il comando Visualizza solo lo stato corrente del rollback.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione KILL viene comunemente utilizzata per terminare un processo che blocca altri processi importanti con blocchi oppure un processo che esegue una query in cui sono utilizzate risorse di sistema che è necessario liberare. I processi di sistema e i processi che eseguono una stored procedure estesa non possono essere terminati.  
  
 Utilizzo di KILL con cautela, soprattutto quando i processi critici sono in esecuzione. Non è possibile terminare un proprio processo ed è consigliabile non terminare i processi seguenti:  
  
-   AWAITING COMMAND  
-   CHECKPOINT SLEEP  
-   LAZY WRITER  
-   LOCK MONITOR  
-   SIGNAL HANDLER  
  
Utilizzare @@SPID per visualizzare il valore di ID di sessione per la sessione corrente.  
  
 Per ottenere un report dei valori di ID della sessione attiva, è possibile eseguire una query sulla colonna session_id delle viste a gestione dinamica sys.dm_tran_locks, sys.dm_exec_sessions e sys.dm_exec_requests. È inoltre possibile visualizzare la colonna SPID restituita dalla stored procedure di sistema sp_who. Se un'operazione di rollback è in corso per uno SPID specifico, nella relativa colonna cmd nel risultato sp_who impostato che SPID indicato KILLED/ROLLBACK.  
  
 Quando una determinata connessione mantiene attivo un blocco su una risorsa del database e blocca l'avanzamento di un'altra connessione, l'ID di sessione della connessione di blocco viene visualizzato nella colonna `blocking_session_id` di `sys.dm_exec_requests` o nella colonna `blk` restituita da `sp_who`.  
  
 È possibile utilizzare il comando KILL per risolvere le transazioni distribuite in dubbio. Queste sono le transazioni distribuite non risolte che si verificano in seguito a riavvii non pianificati del server di database o di MS DTC. Per ulteriori informazioni sulle transazioni in dubbio, vedere la sezione "Commit a due fasi" in [usare transazioni contrassegnate per recuperare coerentemente i database correlati &#40; Modello di recupero con registrazione completa &#41; ](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
## <a name="using-with-statusonly"></a>Utilizzo di WITH STATUSONLY  
 Comando KILL WITH STATUSONLY genera un report solo se l'ID di sessione o del valore UOW è attualmente in fase di rollback a causa di un'istruzione KILL *ID sessione*|*UOW* istruzione. Nel report di stato è indicata la percentuale di rollback completata e il periodo di tempo rimanente, espresso in secondi, nel formato seguente:  
  
 `Spid|UOW <xxx>: Transaction rollback in progress. Estimated rollback completion: <yy>% Estimated time left: <zz> seconds`  
  
 Se il rollback dell'ID di sessione o UOW è terminata quando il comando KILL *ID sessione*|*UOW* viene eseguita l'istruzione WITH STATUSONLY, o se nessun ID di sessione o del valore UOW è in fase di rollback, KILL *ID sessione*|*UOW* WITH STATUSONLY restituirà l'errore seguente:  
  
 ```
"Msg 6120, Level 16, State 1, Line 1"  
"Status report cannot be obtained. Rollback operation for Process ID <session ID> is not in progress."
```  
  
 Per ottenere lo stesso report di stato ripetendo la stessa istruzione KILL *ID sessione*|*UOW* istruzione senza utilizzare l'opzione WITH STATUSONLY; tuttavia, non è consigliabile in questo modo. Ripetizione di un comando KILL *ID sessione* istruzione potrebbe terminare un nuovo processo se il rollback dopo il completamento e l'ID di sessione è stato riassegnato a una nuova attività prima di eseguita la nuova istruzione KILL. L'utilizzo della clausola WITH STATUSONLY consente di evitare questo tipo di problema.  
  
## <a name="permissions"></a>Autorizzazioni  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:** Richiede l'autorizzazione ALTER ANY CONNECTION. L'autorizzazione ALTER ANY CONNECTION viene concessa mediante l'appartenenza al ruolo server predefinito sysadmin o processadmin.  
  
 **[!INCLUDE[ssSDS](../../includes/sssds-md.md)]:** Richiede l'autorizzazione KILL DATABASE CONNECTION. L'account di accesso a livello di server principale è la connessione al DATABASE KILL.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-kill-to-terminate-a-session"></a>A. Utilizzo di KILL per terminare una sessione  
 Nell'esempio seguente viene illustrato come terminare l'ID di sessione `53`.  
  
```sql  
KILL 53;  
GO  
```  
  
### <a name="b-using-kill-session-id-with-statusonly-to-obtain-a-progress-report"></a>B. Utilizzo di KILL session ID WITH STATUSONLY per ottenere un report di stato  
 Nell'esempio seguente viene generato un report di stato del processo di rollback per l'ID di sessione specifico.  
  
```sql  
KILL 54;  
KILL 54 WITH STATUSONLY;  
GO  
  
--This is the progress report.  
spid 54: Transaction rollback in progress. Estimated rollback completion: 80% Estimated time left: 10 seconds.  
```  
  
### <a name="c-using-kill-to-terminate-an-orphaned-distributed-transaction"></a>C. Utilizzo di KILL per terminare una transazione distribuita orfana  
 Nell'esempio seguente viene illustrato come terminare una transazione distribuita orfana (ID sessione = -2) con un *UOW* di `D5499C66-E398-45CA-BF7E-DC9C194B48CF`.  
  
```sql  
KILL 'D5499C66-E398-45CA-BF7E-DC9C194B48CF';  
```  

  
## <a name="see-also"></a>Vedere anche  
 [KILL STATS JOB &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-stats-job-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [SHUTDOWN &#40;Transact-SQL&#41;](../../t-sql/language-elements/shutdown-transact-sql.md)   
 [@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  
