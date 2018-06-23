---
title: Novità&#39;s New in SQL Server 2014 | Documenti Microsoft
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- database-engine
- integration-services
- master-data-services
- replication
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
caps.latest.revision: 70
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9144eeb653649e36cfed3551e4ec465d403ffdcb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064831"
---
# <a name="what39s-new-in-sql-server-2014"></a>Novità&#39;s New in SQL Server 2014
  In questo argomento riepiloga i collegamenti dettagliati nuove funzionalità disponibili in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] e vengono riepilogati i pacchetti di servizi per [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Per provarlo:** ![macchina virtuale di Azure piccola](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) dispone di un account Azure?  Quindi andare **[qui](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** alla selezione di una macchina virtuale con SQL Server 2014 Service Pack 1 (SP1) già installato. 
  
-   [Novità di &#40;motore di Database&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Novità di Analysis Services e Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md)  
  
-   [Novità relative all'installazione di SQL Server](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] non sono state introdotte nuove funzionalità significative al seguente:**  
  
-   [Novità di &#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Novità di &#40;replica&#41;](../relational-databases/replication/what-s-new-replication.md)  
  
-   [Novità di &#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP1) non è stata introduce nuove funzionalità significative.
-  [Informazioni sulla versione di SQL Server 2014 Service Pack 1 ](https://support.microsoft.com/en-us/kb/3058865).
-  [![Scaricare il Service Pack 1 per Microsoft® SQL Server® 2014](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) [scaricare il Service Pack 1 per Microsoft® SQL Server® 2014](https://www.microsoft.com/en-us/download/details.aspx?id=46694).


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 2 (SP2)
- [Informazioni sulla versione di SQL Server 2014 Service Pack 2](https://support.microsoft.com/en-us/kb/3171021).
-  [![Scaricare il Service Pack 2 per Microsoft® SQL Server® 2014](./media/what-s-new-in-sql-server-2016/download.png)](http://go.microsoft.com/fwlink/?LinkID=821558) [scaricare il Service Pack 2 per Microsoft® SQL Server® 2014](http://go.microsoft.com/fwlink/?LinkID=821558).
-  [![Scaricare SQL Server 2014 SP2 Feature Pack](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [scaricare il Feature Pack SQL Server 2014 SP2](https://www.microsoft.com/en-us/download/details.aspx?id=53164).

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP2) Include i miglioramenti seguenti:

### <a name="performance-and-scalability-improvements"></a>Miglioramenti delle prestazioni e scalabilità 
-   **Il partizionamento automatico soft-NUMA:** con [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2, soft-NUMA automatica è abilitata quando 8079 Flag di traccia è attivata durante l'avvio dell'istanza. Quando 8079 Flag di traccia è abilitato durante l'avvio, [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 verrà interrogare il layout di hardware e configurare soft-NUMA automaticamente nei sistemi reporting 8 o più CPU per nodo NUMA. Il comportamento NUMA automatica, soft è Hyperthread (processore logico/HT) compatibile con. Il partizionamento e la creazione di nodi aggiuntivi ridimensionano l'elaborazione in background aumentando il numero di listener tramite scalabilità e le funzionalità di crittografia e di rete. È preferibile al primo test del carico di lavoro delle prestazioni di Auto-Soft NUMA prima di attivare nell'ambiente di produzione. [Vedere il Blog per altre informazioni](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Ridimensionamento di oggetto memoria dinamica:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 partizioni in modo dinamico gli oggetti di memoria in base a numero di nodi e core di scala moderno hardware. L'obiettivo dell'innalzamento di livello dinamico consiste nel partizionare automaticamente un oggetto di memoria provvisoria thread (CMEMTHREAD) Se però diventa un collo di bottiglia. Gli oggetti di memoria non partizionate possono essere promossa in modo dinamico per essere partizionato per nodo (numero di partizioni è uguale a numero di nodi NUMA), e memoria oggetti partizionati in base al nodo possono ulteriormente alzate di livello per essere partizionata in base (numero di partizioni è uguale a numero di CPU CPU). [Vedere il blog per altre informazioni](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **Hint per MAXDOP per CHECK DBCC\* comandi:** risolve questo miglioramento [commenti (468694) connect](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). È ora possibile eseguire DBCC CHECKDB con un'impostazione di MAXDOP diversa del valore di sp_configure. Se MAXDOP supera il valore configurato con Resource Governor, il motore di database usa il valore MAXDOP di Resource Governor descritto in ALTER WORKLOAD GROUP (Transact-SQL). Quando si utilizza l'hint per la query MAXDOP sono valide tutte le regole semantiche utilizzate con l'opzione di configurazione max degree of parallelism. Per altre informazioni, vedere [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **Abilitare > 8TB per Pool di Buffer:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 consente 128 TB di spazio degli indirizzi virtuali per l'utilizzo del pool di buffer. Questo miglioramento consente Pool di Buffer di SQL Server per scalabilità superiore a 8TB in moderni componenti hardware.
-   **Spinlock SOS_RWLock analisi utilizzo software:** SOS_RWLock il è una primitiva di sincronizzazione usata in vari punti in tutta la codebase di SQL Server.  Come suggerisce il nome, il codice può avere più condivisi (lettori) o la proprietà singolo (writer). Questo miglioramento si elimina la necessità di spinlock per SOS_RWLock e utilizza invece senza blocco tecniche simili a OLTP in memoria. Con questa modifica, numero di thread può leggere una struttura di dati protetta da SOS_RWLock in parallelo senza blocco tra loro e garantendo una maggiore scalabilità. Prima di questa modifica, l'implementazione di spinlock consentito un solo thread di acquisire il SOS_RWLock alla volta, anche per leggere una struttura di dati.  [Vedere il blog per altre informazioni](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Implementazione nativa spaziali:** miglioramenti significativi delle prestazioni di query spaziale sono stato introdotto in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 tramite l'implementazione nativa. Per altre informazioni, vedere la [articolo della knowledge base KB3107399](https://support.microsoft.com/en-us/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Facilità di supporto e miglioramenti della diagnostica
-   **La clonazione del database:** database Clone è un nuovo comando DBCC che migliora la risoluzione dei problemi di database di produzione esistenti clonando lo schema e i metadati senza i dati. Il clone viene creato con il comando `DBCC clonedatabase(‘source_database_name’, ‘clone_database_name’)`.  **Nota:** clonazione database non devono essere utilizzati negli ambienti di produzione. Usare il comando seguente determinare se un database sia stato creato da un database clonato: `select DATABASEPROPERTYEX('clonedb', 'isClone')`. Il valore restituito del **1** indica il database viene creato da clonedatabase durante **0** indica non si tratta di un clone.
-   **Supporto di tempdb:** un nuovo messaggio di log degli errori che indica il numero di file tempdb e le dimensioni/aumento automatico delle dimensioni dei dati di tempdb file presentano all'avvio del server.
-   **Registrazione di inizializzazione File immediata del database:** un nuovo messaggio di log degli errori che indica che nel server statup, lo stato di inizializzazione File immediata dei Database (abilitato/disabilitato).
-   **I nomi dei moduli nello stack chiamate:** sullo stack di chiamate di Xevent ora include i nomi dei moduli + offset anziché indirizzi assoluti.
-   **Nuovo DMF per statistiche incrementali:** affronta questo miglioramento [commenti (797156) connect](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) per consentono di tenere traccia di statistiche incrementali a livello di partizione. Viene introdotto un nuovo sys.dm_db_incremental_stats_properties DMF per esporre le informazioni per ogni partizione per le statistiche incrementali.
-   **Comportamento DMV utilizzo indice aggiornato:** affronta questo miglioramento [commenti (739566) connect](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) dai clienti in cui la ricompilazione dell'indice verrà *non* cancellare qualsiasi voce di riga esistente da sys.dm_db _index_usage_stats per quell'indice. Il comportamento sarà ora uguale a quello di SQL 2008 e SQL Server 2016. [Vedere il blog per altre informazioni](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Migliorate correlazione tra diagnostica XE e viste a gestione dinamica:** affronta questo miglioramento [commenti (1934583) connect](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). Query_hash e query_hash vengono utilizzati per identificare in modo univoco una query. Nelle DMV sono definiti come varbinary (8), mentre in XEvent come UINT64. Poiché SQL server non dispone di "unisigned bigint", eseguire il cast non sempre funziona. Questo miglioramento introduce nuove colonne azione/filtro di XEvent equivalenti ai campi query_hash e query_plan_hash ad eccezione del fatto che tali valori sono definiti come INT64. In questo modo è possibile correlare le query tra XEvent e le viste a gestione dinamica.
-   **Supporto per UTF-8 in BULK INSERT e BCP:** affronta questo miglioramento [commenti (370419) connect](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) in cui il supporto per l'esportazione e importazione di dati codificati nel set di caratteri UTF-8 è ora abilitato in BULK INSERT e BCP.
-   **L'esecuzione di query operatore Lightweight profilatura:** durante la risoluzione dei problemi di prestazioni delle query, anche se showplan fornisce molte informazioni sul piano di esecuzione di query e costo dell'operatore nel piano di ma limita informazioni effettivo statistiche di runtime, ad esempio (CPU, i/o letti, tempo trascorso per thread). SQL 2014 SP2 introduce queste statistiche di runtime aggiuntive per ogni operatore Showplan, nonché un XEvent (query_thread_profile) per facilitare la risoluzione dei problemi delle prestazioni delle query. [Vedere il blog per altre informazioni](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Pulizia di rilevamento delle modifiche:** nuova stored procedure `sp_flush_CT_internal_table_on_demand` è stato introdotto per la pulizia con rilevamento delle tabelle interne su richiesta.
-   **Timeout di Lease AlwaysON registrazione** aggiunte nuove funzionalità di registrazione per i messaggi di Timeout di Lease, in modo che vengono registrati l'ora corrente e gli orari di rinnovo previsto. Anche un nuovo messaggio è stato introdotto in SQL Errorlog riguardanti il valore di timeout. [Vedere il blog per altre informazioni](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **Nuovo DMF per il recupero di input del buffer in SQL Server:** un nuovo DMF per il recupero del buffer di input per una sessione/richiesta (sys.dm_exec_input_buffer) è ora disponibile. Dal punto di vista funzionale equivale a DBCC INPUTBUFFER. [Vedere il blog per altre informazioni](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Riduzione dei rischi per la concessione di memoria inferiori a quelle reali e sopravvalutati:** aggiunti nuovi hint per la query per Resource Governor tramite MIN_GRANT_PERCENT e MAX_GRANT_PERCENT. In questo modo è possibile sfruttare questi hint durante l'esecuzione di query limitando le concessioni di memoria per evitare una contesa di memoria. Per altre informazioni, vedere [articolo della knowledge base KB310740](https://support.microsoft.com/en-us/kb/3107401)
-   **Migliore diagnostica grant/utilizzo della memoria:** un nuovo evento esteso è stato aggiunto all'elenco di funzionalità di traccia in SQL Server (query_memory_grant_usage) per tenere traccia delle concessioni di memoria richiesta e quali è concesso. Fornisce migliori funzionalità di analisi e la traccia per la risoluzione dei problemi di esecuzione di query relativi a concessioni di memoria. Per altre informazioni, vedere [articolo della knowledge base KB3107173](https://support.microsoft.com/en-us/kb/3107173).
-   **Query di diagnostica di esecuzione per tempdb spill:**-avviso di Hash e Sort Warnings ora hanno colonne aggiuntive per tenere traccia delle statistiche i/o fisico, memoria utilizzata e righe interessate. È inoltre introdotto un nuovo evento esteso hash_spill_details. A questo punto è possibile tenere traccia delle informazioni più granulari per gli avvisi di hash e l'ordinamento ([KB3107172](https://support.microsoft.com/en-us/kb/3107172)). Questo miglioramento è inoltre ora esposto tramite i piani di Query XML sotto forma di un nuovo attributo per il tipo complesso SpillToTempDbType ([KB3107400](https://support.microsoft.com/en-us/kb/3107400)). Impostare le statistiche su ora Mostra Ordina le statistiche della tabella di lavoro. ,
-   **Migliorata la diagnostica per i piani di esecuzione di query che implicano la distribuzione del predicato residua:** effettive righe lette saranno ora riportate nei piani di esecuzione per consentire di migliorare la risoluzione dei problemi delle prestazioni di query. Questo deve annullare la necessità per acquisire SET STATISTICS IO separatamente. A questo punto è possibile visualizzare informazioni relative a una distribuzione del predicato residuo in un piano di query. Per altre informazioni, vedere [articolo della knowledge base KB3107397](https://support.microsoft.com/en-us/kb/3107397).


## <a name="additional-information"></a>Informazioni aggiuntive  
 [Risorse di SQL Server 2014](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 Release Notes](http://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [Centro risorse di SQL Server 2014](http://msdn.microsoft.com/sqlserver/dn135309)  
  
 [Sito Web SQLCat](http://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  