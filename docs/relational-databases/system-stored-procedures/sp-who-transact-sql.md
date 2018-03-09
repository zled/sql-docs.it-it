---
title: sp_who (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_who_TSQL
- sp_who
dev_langs:
- TSQL
helpviewer_keywords:
- sp_who
ms.assetid: 132dfb08-fa79-422e-97d4-b2c4579c6ac5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 99f8ff7ccfee468c0e9b3598167d6d9823e2bd61
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spwho-transact-sql"></a>sp_who (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fornisce informazioni su utenti correnti, le sessioni e i processi in un'istanza del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. È possibile filtrare tali informazioni in modo da ottenere solo i processi che non sono inattivi, che appartengono a un utente specifico o che sono associati a una determinata sessione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_who [ [ @loginame = ] 'login' | session ID | 'ACTIVE' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@loginame =** ] **'***accesso***'** | *ID sessione*  |  **'ACTIVE'**  
 Viene utilizzato per filtrare il set di risultati.  
  
 *account di accesso* è **sysname** che identifica i processi appartenenti a un account di accesso.  
  
 *ID di sessione* è un numero identificativo di sessione appartenente al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza. *ID di sessione* è **smallint**.  
  
 **Attiva** esclude le sessioni in attesa per il comando successivo da parte dell'utente.  
  
 Se non si specifica alcun valore, vengono restituite tutte le sessioni appartenenti all'istanza.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 **sp_who** restituisce un set di risultati con le informazioni seguenti.  
  
|Colonna|Tipo di dati|Description|  
|------------|---------------|-----------------|  
|**SPID**|**smallint**|ID di sessione.|  
|**ECID**|**smallint**|ID del contesto di esecuzione di un determinato thread associato a un ID di sessione specifico.<br /><br /> ECID = {0 1, 2, 3,...  *n* }, dove 0 rappresenta sempre principale o thread padre e {1, 2, 3,...  *n* } rappresenta i thread secondari.|  
|**status**|**nchar(30)**|Stato del processo. I valori possibili sono:<br /><br /> **inattivo**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sta reimpostando la sessione.<br /><br /> **esecuzione**. Nella sessione vengono eseguiti uno o più batch. Se si abilita la funzionalità MARS (Multiple Active Result Sets), una sessione può eseguire più batch. Per ulteriori informazioni, vedere [utilizzando Multiple Active Result Set &#40; MARS &#41; ](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).<br /><br /> **sfondo**. Nella sessione viene eseguita un'attività in background, ad esempio il rilevamento dei deadlock.<br /><br /> **Rollback**. Nella sessione è in corso il rollback di una transazione.<br /><br /> **in sospeso**. La sessione è in attesa che un thread di lavoro diventi disponibile.<br /><br /> **eseguibile**. L'attività della sessione si trova nella coda eseguibile di un'utilità di pianificazione in attesa di un quantum temporale.<br /><br /> **spinloop**. L'attività della sessione è in attesa che venga liberato uno spinlock.<br /><br /> **sospeso**. La sessione è in attesa del completamento di un evento, ad esempio di I/O.|  
|**loginame**|**nchar(128)**|Nome dell'account di accesso associato a un particolare processo.|  
|**nome host**|**nchar(128)**|Nome host o di computer per ogni processo.|  
|**BLK**|**Char (5)**|ID di sessione del processo di blocco, se esistente. In caso contrario, il valore di questa colonna è zero.<br /><br /> Quando una transazione associata a un ID di sessione specificato viene bloccata da una transazione distribuita orfana, questa colonna restituirà il valore -2 per tale transazione.|  
|**dbname**|**nchar(128)**|Database utilizzato dal processo.|  
|**cmd**|**nchar(16)**|Comando [!INCLUDE[ssDE](../../includes/ssde-md.md)] (istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)], processo interno [!INCLUDE[ssDE](../../includes/ssde-md.md)] e così via) in esecuzione per il processo.|  
|**request_id**|**int**|ID per le richieste in esecuzione in una sessione specifica.|  
  
 In caso di elaborazione parallela, vengono creati thread secondari per l'ID di sessione specifico. Il thread principale è indicato da `spid = <xxx>` e `ecid =0`. Agli altri thread secondari hanno lo stesso `spid = <xxx>`, ma con **ecid** > 0.  
  
## <a name="remarks"></a>Osservazioni  
 Con il termine processo di blocco si indica un processo che mantiene bloccate, potenzialmente con un blocco esclusivo, risorse necessarie per un altro processo.  
  
 A tutte le transazioni distribuite orfane viene assegnato il valore di ID di sessione -2. Le transazioni distribuite orfane sono transazioni distribuite non associate a un ID di sessione. Per altre informazioni, vedere [Usare transazioni contrassegnate per recuperare coerentemente i database correlati &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
 Query di **is_user_process** colonna di Sys.dm exec_sessions per separare i processi di sistema dai processi utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server per visualizzare tutte le sessioni in esecuzione nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In caso contrario, sarà possibile visualizzare solo la sessione corrente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-all-current-processes"></a>A. Elenco di tutti i processi correnti  
 Nell'esempio seguente la stored procedure `sp_who` viene eseguita senza parametri in modo che vengano restituiti tutti gli utenti correnti.  
  
```  
USE master;  
GO  
EXEC sp_who;  
GO  
```  
  
### <a name="b-listing-a-specific-users-process"></a>B. Visualizzazione del processo di un utente specifico  
 Nell'esempio seguente viene illustrato come visualizzare le informazioni su un singolo utente corrente in base al nome dell'account di accesso.  
  
```  
USE master;  
GO  
EXEC sp_who 'janetl';  
GO  
```  
  
### <a name="c-displaying-all-active-processes"></a>C. Visualizzazione di tutti i processi attivi  
  
```  
USE master;  
GO  
EXEC sp_who 'active';  
GO  
```  
  
### <a name="d-displaying-a-specific-process-identified-by-a-session-id"></a>D. Visualizzazione di un processo specifico identificato da un ID di sessione  
  
```  
USE master;  
GO  
EXEC sp_who '10' --specifies the process_id;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_lock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [Sys. sysprocesses &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
