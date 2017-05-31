---
title: Risolvere i problemi di memoria insufficiente | Microsoft Docs
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d6eef790f729a3270c0ba046d6a60114ae2da8dc
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="resolve-out-of-memory-issues"></a>Risolvere i problemi di memoria insufficiente
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] usa più memoria e in modi diversi rispetto a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile che la quantità di memoria installata e allocata per [!INCLUDE[hek_2](../../includes/hek-2-md.md)] diventi inadeguata con l'aumentare delle esigenze. In tal caso, è possibile che la memoria risulti insufficiente. In questo argomento viene descritto come risolvere una situazione di memoria insufficiente. Per le linee guida che consentono di evitare molte situazioni di memoria insufficiente, vedere [Monitorare e risolvere i problemi relativi all'utilizzo della memoria](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md) .  
  
## <a name="covered-in-this-topic"></a>Sezioni dell'argomento  
  
|Argomento|Panoramica|  
|-----------|--------------|  
|[Risoluzione degli errori di ripristino del database dovuti a memoria insufficiente](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_resolveRecoveryFailures)|Operazioni da eseguire se viene visualizzato il messaggio di errore "Operazione di ripristino non riuscita per il database '*\<NomeDatabase>*'. Memoria insufficiente nel pool di risorse '*\<NomePoolRisorse>*'."|  
|[Risoluzione dell'impatto delle condizioni di memoria insufficiente sul carico di lavoro](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_recoverFromOOM)|Operazioni da eseguire nel caso in cui i problemi di memoria insufficiente incidono negativamente sulle prestazioni.|  
|[Risoluzione degli errori di allocazione della pagina dovuti a memoria insufficiente quando è disponibile memoria sufficiente](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_PageAllocFailure)|Operazioni da eseguire se viene visualizzato il messaggio di errore "È in corso la disabilitazione delle allocazioni di pagine per il database '*\<NomeDatabase>*'. Memoria insufficiente nel pool di risorse *\<NomePoolRisorse>*'. …" quando è disponibile memoria sufficiente per l'operazione.|  
  
##  <a name="bkmk_resolveRecoveryFailures"></a> Risoluzione degli errori di ripristino del database dovuti a memoria insufficiente  
 Quando si prova a ripristinare un database, è possibile che venga visualizzato il messaggio di errore "L'operazione di ripristino non è riuscita per il database '*\<NomeDatabase>*'. Memoria insufficiente nel pool di risorse *\<NomePoolRisorse>*'." Questo errore indica che la memoria disponibile del server non è sufficiente per il ripristino del database.
   
La memoria disponibile del server in cui viene ripristinato un database deve essere sufficiente per le tabelle con ottimizzazione per la memoria nel backup del database, in caso contrario il database non verrà portato online.  
  
Se la memoria fisica del server è sufficiente, ma viene comunque visualizzato questo errore, altri processi potrebbero star usando troppa memoria oppure un problema di configurazione rende la memoria disponibile insufficiente per il ripristino. Per questo tipo di problemi usare le seguenti misure per aumentare la memoria disponibile per l'operazione di ripristino: 
  
-   Chiudere temporaneamente le applicazioni in esecuzione.   
    Chiudendo una o più applicazioni in esecuzione o arrestando i servizi non necessari al momento, si libera la memoria usata da tali applicazioni rendendola disponibile per l'operazione di ripristino. È possibile riavviarle dopo il completamento del ripristino.  
  
-   Aumentare il valore di MAX_MEMORY_PERCENT.   
    Se il database è [associato a un pool di risorse](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md), che rappresenta la procedura consigliata, la memoria disponibile per il ripristino viene regolata da MAX_MEMORY_PERCENT. Se il valore è troppo basso, il ripristino non riuscirà. Nel frammento di codice seguente il valore di MAX_MEMORY_PERCENT per il pool di risorse PoolHk viene modificato al 70% della memoria installata.  
  
    > [!IMPORTANT]  
    >  Se il server è in esecuzione in una VM e non è dedicato, impostare il valore di MIN_MEMORY_PERCENT sullo stesso valore di MAX_MEMORY_PERCENT.   
    > Per altre informazioni, vedere l'argomento [Procedure consigliate: Uso di OLTP in memoria in un ambiente di VM](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) .  
  
    ```tsql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     Per informazioni sui valori massimi per MAX_MEMORY_PERCENT, vedere la sezione dell'argomento che riporta le [percentuali di memoria disponibile per indici e tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable).  
  
-   Aumentare **max server memory**.  
    Per informazioni sulla configurazione di **max server memory** vedere l'argomento [Ottimizzazione delle prestazioni del server tramite le opzioni di configurazione della memoria](http://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).  
  
##  <a name="bkmk_recoverFromOOM"></a> Risoluzione dell'impatto delle condizioni di memoria insufficiente sul carico di lavoro  
 Ovviamente, è consigliabile non trovarsi in una situazione di memoria insufficiente. Una buona pianificazione e un buon monitoraggio consentono di evitare le situazioni di memoria insufficiente. Tuttavia, nonostante l'accurata pianificazione non sempre è possibile prevedere le effettive esigenze e potrebbero verificarsi situazioni di memoria insufficiente. Sono disponibili due passaggi per risolvere una situazione di memoria insufficiente:  
  
1.  [Aprire una connessione amministrativa dedicata (DAC)](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_openDAC)  
  
2.  [Intraprendere un'azione correttiva](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_takeCorrectiveAction)  
  
###  <a name="bkmk_openDAC"></a> Aprire una connessione amministrativa dedicata (DAC)  
 Microsoft SQL Server fornisce una connessione amministrativa dedicata (DAC). La connessione DAC consente a un amministratore di accedere a un'istanza in esecuzione del motore di database di SQL Server per risolvere i problemi sul server, anche quando il server non risponde ad altre connessioni client. La connessione DAC è disponibile tramite l'utilità `sqlcmd` e SQL Server Management Studio (SSMS).  
  
 Per informazioni sull'uso di `sqlcmd` e della connessione DAC, vedere [Utilizzo di una connessione amministrativa dedicata](http://msdn.microsoft.com/library/ms189595\(v=sql.100\).aspx/css). Per informazioni sull'uso della connessione DAC tramite SSMS, vedere [Procedura: Utilizzo della connessione amministrativa dedicata con SQL Server Management Studio](http://msdn.microsoft.com/library/ms178068.aspx).  
  
###  <a name="bkmk_takeCorrectiveAction"></a> Intraprendere un'azione correttiva  
 Per risolvere la condizione di memoria insufficiente, è necessario liberare la memoria esistente riducendone l'utilizzo o rendere disponibile una maggiore quantità di memoria per le tabelle in memoria.  
  
#### <a name="free-up-existing-memory"></a>Liberare memoria esistente  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a>Eliminare le righe non essenziali delle tabelle con ottimizzazione per la memoria e attendere la procedura di Garbage Collection  
 È possibile rimuovere le righe non essenziali da una tabella con ottimizzazione per la memoria. Il Garbage Collector restituisce la memoria usata da queste righe alla memoria disponibile. . Il motore OLTP in memoria raccoglie rapidamente le righe di Garbage Collection. Tuttavia, una transazione con esecuzione prolungata può impedire il processo di Garbage Collection. Ad esempio, se si dispone di una transazione che viene eseguita per 5 minuti, tutte le versioni di riga create a causa delle operazioni di aggiornamento/eliminazione mentre la transazione è attiva non possono essere sottoposte al processo di Garbage Collection.  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a>Spostare una o più righe in una tabella basata su disco  
 Gli articoli di Technet riportati di seguito offrono istruzioni sullo spostamento di righe da una tabella con ottimizzazione per la memoria a una tabella basata su disco.  
  
-   [Partizionamento a livello di applicazione](http://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)  
  
-   [Modello di applicazione per il partizionamento di tabelle con ottimizzazione per la memoria](http://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)  
  
#### <a name="increase-available-memory"></a>Aumentare la memoria disponibile  
  
##### <a name="increase-value-of-maxmemorypercent-on-the-resource-pool"></a>Aumentare il valore di MAX_MEMORY_PERCENT nel pool di risorse  
 Se non è stato creato un pool di risorse denominato per le tabelle in memoria, è consigliabile eseguire tale operazione e associare al pool i database di [!INCLUDE[hek_2](../../includes/hek-2-md.md)] . Per istruzioni sulla creazione e l'associazione dei database [a un pool di risorse, vedere l'argomento](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) Associazione di un database con tabelle con ottimizzazione per la memoria a un pool di risorse [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .  
  
 Se il database di [!INCLUDE[hek_2](../../includes/hek-2-md.md)] è associato a un pool di risorse, è possibile aumentare la percentuale di memoria a cui il pool può accedere. Per informazioni sulla modifica del valore di MIN_MEMORY_PERCENT e MAX_MEMORY_PERCENT per un pool di risorse, vedere l'argomento secondario [Cambiare MIN_MEMORY_PERCENT e MAX_MEMORY_PERCENT in un pool esistente](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation) .  
  
 Aumentare il valore di MAX_MEMORY_PERCENT.   
Nel frammento di codice seguente il valore di MAX_MEMORY_PERCENT per il pool di risorse PoolHk viene modificato al 70% della memoria installata.  
  
> [!IMPORTANT]  
>  Se il server è in esecuzione in una VM e non è dedicato, impostare il valore di MIN_MEMORY_PERCENT e MAX_MEMORY_PERCENT sullo stesso valore.   
> Per altre informazioni, vedere l'argomento [Procedure consigliate: Uso di OLTP in memoria in un ambiente di VM](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) .  
  
```tsql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 Per informazioni sui valori massimi per MAX_MEMORY_PERCENT, vedere la sezione dell'argomento che riporta le [percentuali di memoria disponibile per indici e tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable).  
  
##### <a name="install-additional-memory"></a>Installare memoria aggiuntiva  
 Infine, la soluzione migliore, se possibile, prevede l'installazione di ulteriore memoria fisica. In questo caso, tenere presente che probabilmente sarà possibile aumentare anche il valore di MAX_MEMORY_PERCENT (vedere l'argomento secondario [Cambiare MIN_MEMORY_PERCENT e MAX_MEMORY_PERCENT in un pool esistente](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation)) poiché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe non richiedere ulteriore memoria, consentendo di rendere disponibile la maggior parte se non tutta la memoria appena installata per il pool di risorse.  
  
> [!IMPORTANT]  
>  Se il server è in esecuzione in una VM e non è dedicato, impostare il valore di MIN_MEMORY_PERCENT e MAX_MEMORY_PERCENT sullo stesso valore.   
> Per altre informazioni, vedere l'argomento [Procedure consigliate: Uso di OLTP in memoria in un ambiente di VM](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) .  
  
##  <a name="bkmk_PageAllocFailure"></a> Risoluzione degli errori di allocazione della pagina dovuti a memoria insufficiente quando è disponibile memoria sufficiente  
 Se viene visualizzato il messaggio di errore "È in corso la disabilitazione delle allocazioni di pagine per il database '*\<NomeDatabase>*'. Memoria insufficiente nel pool di risorse '*\<NomePoolRisorse>*'. Per altre informazioni, vedere 'http://go.microsoft.com/fwlink/?LinkId=330673' nel log degli errori quando la memoria fisica disponibile è sufficiente per allocare pagina, il problema può essere dovuto a Resource Governor disabilitato. Quando Resource Governor è disabilitato MEMORYBROKER_FOR_RESERVE genera richieste di memoria artificiali.  
  
 Per risolvere questo problema, è necessario abilitare Resource Governor.  
  
 Per informazioni sui limiti e sulle restrizioni e per istruzioni sull'abilitazione di Resource Governor usando Esplora oggetti, proprietà di Resource Governor o Transact-SQL, vedere [Abilitare Resource Governor](http://technet.microsoft.com/library/bb895149.aspx) .  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione della memoria per OLTP in memoria](http://msdn.microsoft.com/library/d82f21fa-6be1-4723-a72e-f2526fafd1b6)   
 [Monitorare e risolvere i problemi relativi all'utilizzo della memoria](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)   
 [a un pool di risorse, vedere l'argomento](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [Procedure consigliate: Uso di OLTP in memoria in un ambiente di VM](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9)  
  
  

