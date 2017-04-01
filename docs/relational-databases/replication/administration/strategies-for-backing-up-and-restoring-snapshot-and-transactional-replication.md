---
title: "Strategie per il backup e il ripristino della replica snapshot e della replica transazionale | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backup [replica di SQL Server], replica snapshot"
  - "ripristino [replica di SQL Server], replica transazionale"
  - "replica snapshot [SQL Server], backup e ripristino"
  - "ripristino [replica di SQL Server], replica snapshot"
  - "recupero [replica di SQL Server], replica transazionale"
  - "replica transazionale, backup e ripristino"
  - "recupero [replica di SQL Server], replica snapshot"
  - "sincronizzazione con backup [replica di SQL Server]"
  - "backup [replica di SQL Server], replica transazionale"
ms.assetid: a8afcdbc-55db-4916-a219-19454f561f9e
caps.latest.revision: 59
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 59
---
# Strategie per il backup e il ripristino della replica snapshot e della replica transazionale
  Quando si progetta una strategia di backup e ripristino per la replica snapshot e la replica transazionale, è necessario considerare le tre aree di fattori seguenti:  
  
-   Database di cui eseguire il backup.  
  
-   Impostazioni di backup per la replica transazionale.  
  
-   Passaggi richiesti per ripristinare un database, i quali variano in base al tipo di replica e alle opzioni scelte.  
  
 In questo argomento vengono illustrate le tre aree elencate in precedenza. Per informazioni sul backup e ripristino per la pubblicazione Oracle, vedere [di Backup e ripristino per server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/backup-and-restore-for-oracle-publishers.md).  
  
## Backup di database  
 Per la replica snapshot e la replica transazionale è necessario effettuare a intervalli regolari il backup dei database seguenti:  
  
-   Database di pubblicazione nel server di pubblicazione.  
  
-   Database di distribuzione nel database di distribuzione.  
  
-   Database di sottoscrizione in ogni Sottoscrittore.  
  
-   Database di sistema **master** e **msdb** nel server di pubblicazione, nel database di distribuzione e in tutti i Sottoscrittori. È necessario che il backup di questi database venga eseguito contemporaneamente e che venga inoltre eseguito nello stesso momento di quello del relativo database di replica. Ad esempio, eseguire il backup di **master** e **msdb** database nel server di pubblicazione allo stesso tempo che il backup del database di pubblicazione. Se il database di pubblicazione viene ripristinato, verificare che il **master** e **msdb** database siano coerenti con il database di pubblicazione in termini di impostazioni e configurazione della replica.  
  
 Se si eseguono backup regolari del log, le eventuali modifiche correlate alla replica dovrebbero essere incluse nei backup del log. Se non si eseguono i backup del log, è necessario eseguire un backup ogni volta che un'impostazione relativa alla replica viene modificata. Per altre informazioni, vedere [Common Actions Requiring an Updated Backup](../../../relational-databases/replication/administration/common-actions-requiring-an-updated-backup.md).  
  
## Impostazioni di backup per la replica transazionale  
 La replica transazionale sono inclusi l'utilizzo di **sincronizzazione con backup** opzione, che può essere impostata nel database di distribuzione e nel database di pubblicazione:  
  
-   Si consiglia di impostare sempre questa opzione nel database di distribuzione.  
  
     L'impostazione di questa opzione nel database di distribuzione impedisce che le transazioni nel log del database di pubblicazione vengano troncate fino al relativo backup nel database di distribuzione. È possibile ripristinare lo stato del database di distribuzione al momento dell'ultimo backup. Eventuali transazioni mancanti verranno recapitate dal database di pubblicazione al database di distribuzione. La replica continua senza interruzioni.  
  
     L'impostazione di questa opzione nel database di distribuzione non influisce sulla latenza di replica. L'opzione ritarderà tuttavia il troncamento del log nel database di pubblicazione fino a quando non viene eseguito il backup delle transazioni corrispondenti nel database di distribuzione. Ciò può comportare la creazione di un log delle transazioni di dimensioni maggiori nel database di pubblicazione.  
  
-   Si consiglia di impostare questa opzione nel database di pubblicazione se l'applicazione in uso tollera un'ulteriore latenza.  
  
     L'impostazione di questa opzione nel database di pubblicazione garantisce che le transazioni vengano recapitate al database di distribuzione solo dopo che è stato eseguito il backup nel database di pubblicazione. Nel server di pubblicazione è quindi possibile ripristinare il backup più recente del database di pubblicazione, evitando che il database di distribuzione disponga di transazioni che risultino mancanti nel database di pubblicazione ripristinato.  
  
     La latenza e la velocità effettiva sono interessate da questo aspetto, in quanto le transazioni possono essere recapitate al database di distribuzione solo dopo che ne è stato eseguito il backup nel server di pubblicazione. Se ad esempio viene eseguito un backup del log delle transazioni ogni cinque minuti, si verifica un'ulteriore latenza di cinque minuti tra l'esecuzione del commit di una transazione nel server di pubblicazione e il recapito della transazione al database di distribuzione e successivamente al Sottoscrittore.  
  
    > [!NOTE]  
    >  Il **sincronizzazione con backup** opzione assicura la coerenza tra il database di pubblicazione e il database di distribuzione, ma l'opzione non comporta la perdita di dati. Se ad esempio il log delle transazioni viene perso, le transazioni di cui è stato eseguito il commit dopo l'ultimo backup del log non saranno disponibili nel database di pubblicazione o nel database di distribuzione. Questo comportamento è identico a quello di un database non replicato.  
  
 **Per impostare l'opzione sync with backup**  
  
-   Replica [!INCLUDE[tsql](../../../includes/tsql-md.md)] di programmazione: [abilitare i backup coordinati per la replica transazionale e 40 #; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/administration/enable coordinated backups for transactional replication.md)  
  
## Ripristino di database interessati da una replica  
 È possibile ripristinare tutti i database in una topologia di replica se sono disponibili backup recenti e viene eseguita la procedura appropriata. La procedura di ripristino per il database di pubblicazione dipende dal tipo di replica e dalle opzioni utilizzate, mentre quella per tutti gli altri database è indipendente da tali fattori.  
  
 La replica supporta il ripristino dei database replicati nello stesso server e nello stesso database da cui è stato creato il backup. Se si ripristina un backup di un database replicato in un altro server o database, le impostazioni di replica non potranno essere mantenute. In questo caso, è necessario ricreare tutte le pubblicazioni e le sottoscrizioni dopo il ripristino dei backup.  
  
### Server di pubblicazione  
 Sono disponibili procedure di ripristino per i tipi di replica seguenti:  
  
-   Replica snapshot  
  
-   Replica transazionale di sola lettura  
  
-   Replica transazionale con sottoscrizioni aggiornabili  
  
-   Replica transazionale peer-to-peer  
  
 Il ripristino di **msdb** e **master** database, vengono inoltre trattati in questa sezione, è lo stesso per tutti i quattro tipi.  
  
#### Database di pubblicazione: replica snapshot  
  
1.  Ripristinare il backup più recente del database di pubblicazione. Andare al passaggio 2.  
  
2.  Il backup del database di pubblicazione contiene la configurazione più recente per tutte le pubblicazioni e le sottoscrizioni? In caso affermativo, il ripristino viene completato. In caso contrario, andare al passaggio 3.  
  
3.  Rimuovere la configurazione della replica dal server di pubblicazione, dal database di distribuzione e dai Sottoscrittori, quindi ricreare la configurazione. Il ripristino viene completato.  
  
     Per ulteriori informazioni su come rimuovere la replica, vedere [sp_removedbreplication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md).  
  
#### Database di pubblicazione: replica transazionale di sola lettura  
  
1.  Ripristinare il backup più recente del database di pubblicazione. Andare al passaggio 2.  
  
2.  È stato il **sincronizzazione con backup** impostazione è abilitata nel database di pubblicazione prima dell'errore? In caso affermativo, andare al passaggio 3. In caso contrario, andare al passaggio 5.  
  
     Se l'opzione è abilitata, la query `SELECT DATABASEPROPERTYEX('<PublicationDatabaseName>', 'IsSyncWithBackup')` restituisce "1".  
  
3.  Il backup ripristinato è completo e aggiornato? Contiene la configurazione più recente per tutte le pubblicazioni e le sottoscrizioni? In caso affermativo, il ripristino viene completato. In caso contrario, andare al passaggio 4.  
  
4.  Le informazioni di configurazione nel database di pubblicazione ripristinato non sono aggiornate. È pertanto necessario assicurarsi che i Sottoscrittori dispongano di tutti i comandi in sospeso nel database di distribuzione, quindi eliminare e ricreare la configurazione della replica.  
  
    1.  Eseguire l'agente di distribuzione fino a completare la sincronizzazione in tutti i Sottoscrittori dei comandi in sospeso nel database di distribuzione. Verificare che tutti i comandi vengano recapitati ai sottoscrittori tramite il **comandi non distribuiti** scheda in Monitoraggio replica oppure eseguendo una query di [MSdistribution_status](../../../relational-databases/system-views/msdistribution-status-transact-sql.md) vista nel database di distribuzione. Andare al passaggio b.  
  
         Per ulteriori informazioni su come eseguire l'agente di distribuzione, vedere [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [concetti eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
         Per ulteriori informazioni su come verificare i comandi, vedere [Visualizza i comandi replicati e altre informazioni nel Database di distribuzione & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/monitor/view replicated commands and information in distribution database.md) e [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
    2.  Rimuovere la configurazione della replica dal server di pubblicazione, dal database di distribuzione e dai Sottoscrittori, quindi ricreare la configurazione. Quando si ricreano le sottoscrizioni, specificare che i dati sono già disponibili nel Sottoscrittore. Il ripristino viene completato.  
  
         Per ulteriori informazioni su come rimuovere la replica, vedere [sp_removedbreplication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md).  
  
         Per ulteriori informazioni su come specificare che il sottoscrittore dispone già dei dati, vedere [inizializzare una sottoscrizione manualmente](../../../relational-databases/replication/initialize-a-subscription-manually.md).  
  
5.  Il **sincronizzazione con backup** opzione non è stato impostato nel database di pubblicazione. Le transazioni che non sono state incluse nel backup ripristinato potrebbero pertanto essere state recapitate al database di distribuzione e ai Sottoscrittori. È a questo punto necessario assicurarsi che i Sottoscrittori dispongano di tutti i comandi in sospeso nel database di distribuzione, quindi applicare manualmente al database di pubblicazione eventuali transazioni non incluse nel backup ripristinato.  
  
    > [!IMPORTANT]  
    >  Questo processo può comportare il ripristino delle tabelle pubblicate in base a una temporizzazione più recente rispetto a quella di altre tabelle non pubblicate ripristinate dal backup.  
  
    1.  Eseguire l'agente di distribuzione fino a completare la sincronizzazione in tutti i Sottoscrittori dei comandi in sospeso nel database di distribuzione. Verificare che tutti i comandi vengano recapitati ai sottoscrittori tramite il **comandi non distribuiti** scheda in Monitoraggio replica oppure eseguendo una query di [MSdistribution_status](../../../relational-databases/system-views/msdistribution-status-transact-sql.md) vista nel database di distribuzione. Andare al passaggio b.  
  
         Per ulteriori informazioni su come eseguire l'agente di distribuzione, vedere [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [concetti eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
         Per ulteriori informazioni su come verificare i comandi, vedere [Visualizza i comandi replicati e altre informazioni nel Database di distribuzione & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/monitor/view replicated commands and information in distribution database.md) e [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
    2.  Utilizzare il [utilità tablediff](../../../tools/tablediff-utility.md) o un altro strumento per sincronizzare manualmente il server di pubblicazione con il sottoscrittore. Questa operazione consente di recuperare i dati del database di sottoscrizione non inclusi nel backup del database di pubblicazione. Andare al passaggio c.  
  
         Per ulteriori informazioni sui **tablediff** utilità, vedere [confrontare tabelle replicate per differenze & #40; Programmazione della replica & #41;](../../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
    3.  Il backup ripristinato è completo e aggiornato? Contiene la configurazione più recente per tutte le pubblicazioni e le sottoscrizioni? In caso affermativo, eseguire il [sp_replrestart](../../../relational-databases/system-stored-procedures/sp-replrestart-transact-sql.md) stored procedure per risincronizzare i metadati del server di pubblicazione con i metadati del server di distribuzione. Il ripristino viene completato. In caso contrario, andare al passaggio d.  
  
    4.  Rimuovere la configurazione della replica dal server di pubblicazione, dal database di distribuzione e dai Sottoscrittori, quindi ricreare la configurazione. Quando si ricreano le sottoscrizioni, specificare che i dati sono già disponibili nel Sottoscrittore. Il ripristino viene completato.  
  
         Per ulteriori informazioni su come rimuovere la replica, vedere [sp_removedbreplication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md).  
  
         Per ulteriori informazioni su come specificare che il sottoscrittore dispone già dei dati, vedere [inizializzare una sottoscrizione manualmente](../../../relational-databases/replication/initialize-a-subscription-manually.md).  
  
#### Database di pubblicazione: replica transazionale con sottoscrizioni aggiornabili  
  
1.  Ripristinare il backup più recente del database di pubblicazione. Andare al passaggio 2.  
  
2.  Eseguire l'agente di distribuzione fino a completare la sincronizzazione in tutti i Sottoscrittori dei comandi in sospeso nel database di distribuzione. Verificare che tutti i comandi vengano recapitati ai sottoscrittori tramite il **comandi non distribuiti** scheda in Monitoraggio replica oppure eseguendo una query di [MSdistribution_status](../../../relational-databases/system-views/msdistribution-status-transact-sql.md) vista nel database di distribuzione. Andare al passaggio 3.  
  
     Per ulteriori informazioni su come eseguire l'agente di distribuzione, vedere [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [concetti eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
     Per ulteriori informazioni su come verificare i comandi, vedere [Visualizza i comandi replicati e altre informazioni nel Database di distribuzione & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/monitor/view replicated commands and information in distribution database.md) e [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
3.  Se si utilizza in coda di sottoscrizioni aggiornabili, connettersi a ogni sottoscrittore ed eliminare tutte le righe di [MSreplication_queue & #40; Transact-SQL & #41;](../../../relational-databases/system-tables/msreplication-queue-transact-sql.md) tabella nel database di sottoscrizione. Andare al passaggio 4.  
  
    > [!NOTE]  
    >  Se si utilizzano sottoscrizioni ad aggiornamento in coda e le tabelle contengono colonne Identity, è necessario assicurarsi che dopo un ripristino vengano assegnati gli intervalli di valori Identity corretti. Per ulteriori informazioni, vedere [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
4.  È a questo punto necessario assicurarsi che i Sottoscrittori dispongano di tutti i comandi in sospeso nel database di distribuzione, quindi applicare manualmente al database di pubblicazione eventuali transazioni non incluse nel backup ripristinato.  
  
    > [!IMPORTANT]  
    >  Questo processo può comportare il ripristino delle tabelle pubblicate in base a una temporizzazione più recente rispetto a quella di altre tabelle non pubblicate ripristinate dal backup.  
  
    1.  Eseguire l'agente di distribuzione fino a completare la sincronizzazione in tutti i Sottoscrittori dei comandi in sospeso nel database di distribuzione. Verificare che tutti i comandi vengano recapitati ai sottoscrittori tramite Monitoraggio replica oppure eseguendo una query di [MSdistribution_status](../../../relational-databases/system-views/msdistribution-status-transact-sql.md) vista nel database di distribuzione. Andare al passaggio b.  
  
    2.  Utilizzare il [utilità tablediff](../../../tools/tablediff-utility.md) o un altro strumento per sincronizzare manualmente il server di pubblicazione con il sottoscrittore. Questa operazione consente di recuperare i dati del database di sottoscrizione non inclusi nel backup del database di pubblicazione. Andare al passaggio c.  
  
         Per ulteriori informazioni sui **tablediff** utilità, vedere [confrontare tabelle replicate per differenze & #40; Programmazione della replica & #41;](../../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
    3.  Il backup ripristinato è completo e aggiornato? Contiene la configurazione più recente per tutte le pubblicazioni e le sottoscrizioni? In caso affermativo, eseguire il [sp_replrestart](../../../relational-databases/system-stored-procedures/sp-replrestart-transact-sql.md) stored procedure per risincronizzare i metadati del server di pubblicazione con i metadati del server di distribuzione. Il ripristino viene completato. In caso contrario, andare al passaggio d.  
  
    4.  Rimuovere la configurazione della replica dal server di pubblicazione, dal database di distribuzione e dai Sottoscrittori, quindi ricreare la configurazione. Quando si ricreano le sottoscrizioni, specificare che i dati sono già disponibili nel Sottoscrittore. Il ripristino viene completato.  
  
         Per ulteriori informazioni su come rimuovere la replica, vedere e [sp_removedbreplication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md).  
  
         Per ulteriori informazioni su come specificare che il sottoscrittore dispone già dei dati, vedere [inizializzare una sottoscrizione manualmente](../../../relational-databases/replication/initialize-a-subscription-manually.md).  
  
#### Database di pubblicazione: replica transazionale peer-to-peer  
 Nei passaggi seguenti, i database di pubblicazione **A**, **B**, e **C** in una topologia di replica transazionale peer-to-peer. Database **A** e **C** database; sono online e funziona correttamente **B** è il database da ripristinare. Il processo descritto, specialmente i passaggi 7, 10 e 11, è molto simile al processo per l'aggiunta di un nodo a una topologia peer-to-peer. Il modo più semplice per eseguire questi passaggi consiste nell'utilizzare la Configurazione guidata topologia peer-to-peer, ma è possibile utilizzare anche stored procedure.  
  
1.  Eseguire gli agenti di distribuzione per sincronizzare le sottoscrizioni nei database **A** e **C**. Andare al passaggio 2.  
  
     Per ulteriori informazioni su come eseguire l'agente di distribuzione, vedere [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [concetti eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
2.  Se il database di distribuzione che **B** utilizza è ancora disponibile, eseguire gli agenti di distribuzione per sincronizzare le sottoscrizioni tra database **B** e **A** e i database e B e **C**. Andare al passaggio 3.  
  
3.  Rimuovere i metadati dalla distribuzione di database che **B** utilizza eseguendo [sp_removedistpublisherdbreplication](../../../relational-databases/system-stored-procedures/sp-removedistpublisherdbreplication-transact-sql.md) nel database di distribuzione per **B**. Andare al passaggio 4.  
  
4.  Nei database **A** e **C**, eliminare le sottoscrizioni della pubblicazione nel database **B**. Andare al passaggio 5.  
  
     Per ulteriori informazioni su come eliminare le sottoscrizioni, vedere [sottoscrivere pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md).  
  
5.  Eseguire un backup del log o backup completo del database **A**. Andare al passaggio 6.  
  
6.  Ripristinare il backup del database **A** nel database **B**. Database **B** contiene ora i dati dal database **A**, ma non la configurazione della replica. Quando si ripristina un backup in un altro server, la replica viene rimosso; Pertanto, la replica è stato rimosso dal database **B**. Andare al passaggio 7.  
  
7.  Ricreare la pubblicazione nel database **B**, e quindi ricreare le sottoscrizioni tra database **A** e **B**. (Le sottoscrizioni che interessano il database **C** vengono gestite in una fase successiva.).  
  
    1.  Ricreare la pubblicazione nel database **B**. Andare al passaggio b.  
  
    2.  Ricreare la sottoscrizione nel database **B** della pubblicazione nel database **A**, specificando che la sottoscrizione deve essere inizializzata con un backup (un valore di **inizializzazione con backup** per il **@sync_type** parametro [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)). Andare al passaggio c.  
  
    3.  Ricreare la sottoscrizione nel database **A** della pubblicazione nel database **B**, specificando che il server di sottoscrizione sono già disponibili i dati (un valore di **solo supporto replica** per il **@sync_type** parametro [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)). Andare al passaggio 8.  
  
8.  Eseguire gli agenti di distribuzione per sincronizzare le sottoscrizioni nei database **A** e **B**. In presenza di eventuali colonne Identity nelle tabelle pubblicate, andare al passaggio 9. In caso contrario, andare al passaggio 10.  
  
9. Dopo il ripristino, l'intervallo di valori identity assegnato per ogni tabella nel database **A** verrà utilizzato anche nel database **B**. Assicurarsi che il database ripristinato **B** abbia ricevuto tutte le modifiche dal database non riuscito **B** che sono state distribuite al database **A** e database **C**; quindi reinizializzare l'intervallo di valori identity per ogni tabella.  
  
    1.  Eseguire [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) database **B** e recuperare il parametro di output **@request_id**. Andare al passaggio b.  
  
    2.  Per impostazione predefinita, l'agente di distribuzione è impostato per l'esecuzione continua. I token dovrebbero pertanto essere inviati automaticamente a tutti i nodi. Se l'agente di distribuzione non viene eseguito in modalità continua, eseguire l'agente. Per ulteriori informazioni, vedere [concetti eseguibili agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) o [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md). Andare al passaggio c.  
  
    3.  Eseguire [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md), specificando il **@request_id** valore recuperato nel passaggio b. Attendere finché tutti i nodi indicano di avere ricevuto la richiesta peer. Andare al passaggio d.  
  
    4.  Utilizzare [DBCC CHECKIDENT](../../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md) per reinizializzare ogni tabella nel database **B** per assicurarsi che venga utilizzato un intervallo appropriato. Andare al passaggio 10.  
  
     Per ulteriori informazioni sulla gestione di intervalli di valori identity, vedere la sezione "Assegnazione di intervalli per la gestione manuale" di [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
10. A questo punto, database **B** e database **C** non sono direttamente connessi, ma riceveranno le modifiche tramite database **A**. Se la topologia contiene nodi in cui è eseguito [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], andare al passaggio 11. Altrimenti, andare al passaggio 12.  
  
11. Arresto del sistema e quindi ricreare la sottoscrizione tra database **B** e **C**. Mettere in stato di inattività un sistema significa arrestare le attività sulle tabelle pubblicate in tutti i nodi e verificare che ogni nodo abbia ricevuto tutte le modifiche dagli altri nodi:  
  
    1.  Arrestare qualsiasi attività sulle tabelle pubblicate nella topologia peer-to-peer. Andare al passaggio b.  
  
    2.  Eseguire [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) database **B** e recuperare il parametro di output **@request_id**. Andare al passaggio c.  
  
    3.  Per impostazione predefinita, l'agente di distribuzione è impostato per l'esecuzione continua. I token dovrebbero pertanto essere inviati automaticamente a tutti i nodi. Se l'agente di distribuzione non viene eseguito in modalità continua, eseguire l'agente. Andare al passaggio d.  
  
    4.  Eseguire [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md), specificando il **@request_id** valore recuperato nel passaggio b. Attendere finché tutti i nodi indicano di avere ricevuto la richiesta peer. Andare al passaggio e.  
  
    5.  Ricreare la sottoscrizione nel database **B** della pubblicazione nel database **C**, specificando che il server di sottoscrizione sono già disponibili i dati. Andare al passaggio b.  
  
    6.  Ricreare la sottoscrizione nel database **C** della pubblicazione nel database **B**, specificando che il server di sottoscrizione sono già disponibili i dati. Andare al passaggio 13.  
  
12. Ricreare la sottoscrizione tra database **B** e **C**:  
  
    1.  Nel database **B**, query di [MSpeer_lsns](../../../relational-databases/system-tables/mspeer-lsns-transact-sql.md) tabella per recuperare il numero di sequenza log (LSN) della transazione più recente di tale database **B** ha ricevuto dal database **C**.  
  
    2.  Ricreare la sottoscrizione nel database **B** della pubblicazione nel database **C**, specificando che è necessario inizializzare la sottoscrizione in base al numero LSN (un valore di **inizializzazione da lsn** per il **@sync_type** parametro [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)). Andare al passaggio b.  
  
    3.  Ricreare la sottoscrizione nel database **C** della pubblicazione nel database **B**, specificando che il server di sottoscrizione sono già disponibili i dati. Andare al passaggio 13.  
  
13. Eseguire gli agenti di distribuzione per sincronizzare le sottoscrizioni nei database **B** e **C**. Il ripristino viene completato.  
  
#### Database msdb (server di pubblicazione)  
  
1.  Ripristinare il backup più recente del **msdb** database.  
  
2.  Il backup ripristinato è completo e aggiornato? Contiene la configurazione più recente per tutte le pubblicazioni e le sottoscrizioni? In caso affermativo, il recupero viene completato. In caso contrario, andare al passaggio 3.  
  
3.  Ricreare il processo di pulizia dei riferimenti alle sottoscrizioni dagli script di replica. Il recupero viene completato.  
  
#### Database master (server di pubblicazione)  
  
1.  Ripristinare il backup più recente di **master** database.  
  
2.  Assicurarsi che il database sia consistente con il database di pubblicazione in termini di impostazioni e configurazione della replica.  
  
### Database nel database di distribuzione  
  
#### Database di distribuzione  
  
1.  Ripristinare il backup più recente del database di distribuzione.  
  
2.  È stato il **sincronizzazione con backup** abilitata nel database di distribuzione prima dell'errore? In caso affermativo, andare al passaggio 3. In caso contrario, andare al passaggio 4.  
  
     Se l'opzione è abilitata, la query `SELECT DATABASEPROPERTYEX('<DistributionDatabaseName>', 'IsSyncWithBackup')` restituisce "1".  
  
3.  Il backup ripristinato è completo e aggiornato? Contiene la configurazione più recente per tutte le pubblicazioni e le sottoscrizioni? In caso affermativo, il recupero viene completato. In caso contrario, andare al passaggio 4.  
  
4.  Le informazioni di configurazione nel database di distribuzione ripristinato non sono aggiornate o **sincronizzazione con backup** opzione non è stato impostato nel database di distribuzione. Dopo il ripristino, è possibile che nel database di distribuzione manchino le transazioni di cui è stato eseguito il commit nel server di pubblicazione, ma che non sono state ancora recapitate ai Sottoscrittori. Eliminare e ricreare la replica, quindi eseguire la convalida.  
  
    1.  Rimuovere la configurazione della replica dal server di pubblicazione, dal database di distribuzione e dai Sottoscrittori, quindi ricreare la configurazione. Quando si ricreano le sottoscrizioni, specificare che i dati sono già disponibili nel Sottoscrittore. Andare al passaggio b.  
  
         Per ulteriori informazioni su come rimuovere la replica, vedere [sp_removedbreplication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md).  
  
         Per ulteriori informazioni su come specificare che il sottoscrittore dispone già dei dati, vedere [inizializzare una sottoscrizione manualmente](../../../relational-databases/replication/initialize-a-subscription-manually.md).  
  
    2.  Contrassegnare tutte le pubblicazioni per la convalida. Reinizializzare eventuali sottoscrizioni che non superano la convalida. Il recupero viene completato.  
  
         Per ulteriori informazioni sulla convalida, vedere [convalidare i dati replicati](../../../relational-databases/replication/validate-replicated-data.md). Per ulteriori informazioni sulla reinizializzazione, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Database msdb (database di distribuzione)  
  
1.  Ripristinare il backup più recente del **msdb** database.  
  
2.  Il backup ripristinato è completo e aggiornato? Contiene la configurazione più recente per tutte le pubblicazioni e le sottoscrizioni? In caso affermativo, il recupero viene completato. In caso contrario, andare al passaggio 3.  
  
3.  Rimuovere la configurazione della replica dal server di pubblicazione, dal database di distribuzione e dai Sottoscrittori, quindi ricreare la configurazione. Quando si ricreano le sottoscrizioni, specificare che i dati sono già disponibili nel Sottoscrittore. Andare al passaggio 4.  
  
     Per ulteriori informazioni su come rimuovere la replica, vedere [sp_removedbreplication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md).  
  
     Per ulteriori informazioni su come specificare che il sottoscrittore dispone già dei dati, vedere [inizializzare una sottoscrizione manualmente](../../../relational-databases/replication/initialize-a-subscription-manually.md).  
  
4.  Contrassegnare tutte le pubblicazioni per la convalida. Reinizializzare eventuali sottoscrizioni che non superano la convalida. Il recupero viene completato.  
  
     Per ulteriori informazioni sulla convalida, vedere [convalidare i dati replicati](../../../relational-databases/replication/validate-replicated-data.md). Per ulteriori informazioni sulla reinizializzazione, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Database master (database di distribuzione)  
  
1.  Ripristinare il backup più recente di **master** database.  
  
2.  Assicurarsi che il database sia consistente con il database di pubblicazione in termini di impostazioni e configurazione della replica.  
  
### Database nel Sottoscrittore  
  
#### Database di sottoscrizione  
  
1.  L'ultimo backup del database di sottoscrizione è più recente dell'impostazione minima relativa alla memorizzazione per la distribuzione nel database di distribuzione? Questo aspetto determina se il database di distribuzione disponga ancora di tutti i comandi necessari per aggiornare il Sottoscrittore. In caso affermativo, andare al passaggio 2. In caso contrario, reinizializzare la sottoscrizione. Il recupero viene completato.  
  
     Per determinare l'impostazione di memorizzazione massimo per la distribuzione, eseguire [sp_helpdistributiondb](../../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md) e recuperare il valore di **max_distretention** colonna (questo valore è espresso in ore).  
  
     Per ulteriori informazioni su come reinizializzare una sottoscrizione, vedere [reinizializzare una sottoscrizione](../../../relational-databases/replication/reinitialize-a-subscription.md).  
  
2.  Ripristinare il backup del database di sottoscrizione più recente. Andare al passaggio 3.  
  
3.  Se il database di sottoscrizione contiene solo sottoscrizioni push, andare al passaggio 4. Se il database di sottoscrizione contiene sottoscrizioni pull, determinare quanto segue: le informazioni sulla sottoscrizione sono aggiornate? Nel database sono incluse tutte le tabelle e le opzioni impostate al momento dell'errore? In caso affermativo, andare al passaggio 4. In caso contrario, reinizializzare la sottoscrizione. Il recupero viene completato.  
  
4.  Per sincronizzare il Sottoscrittore, eseguire l'agente di distribuzione. Il recupero viene completato.  
  
     Per ulteriori informazioni su come eseguire l'agente di distribuzione, vedere [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [concetti eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
#### Database msdb (Sottoscrittore)  
  
1.  Ripristinare il backup più recente del **msdb** database. Nel Sottoscrittore vengono utilizzate sottoscrizioni pull? In caso di risposta negativa, il ripristino viene completato. In caso affermativo, andare al passaggio 2.  
  
2.  Il backup ripristinato è completo e aggiornato? Contiene la configurazione più recente per tutte le sottoscrizioni pull? In caso affermativo, il recupero viene completato. In caso contrario, andare al passaggio 3.  
  
3.  Eliminare e ricreare le sottoscrizioni pull. Quando si ricreano le sottoscrizioni, specificare che i dati sono già disponibili nel Sottoscrittore. Il ripristino viene completato.  
  
     Per ulteriori informazioni su come eliminare le sottoscrizioni, vedere [sottoscrivere pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md).  
  
     Per ulteriori informazioni su come specificare che il sottoscrittore dispone già dei dati, vedere [inizializzare una sottoscrizione manualmente](../../../relational-databases/replication/initialize-a-subscription-manually.md).  
  
#### Database master (Sottoscrittore)  
  
1.  Ripristinare il backup più recente di **master** database.  
  
2.  Assicurarsi che il database sia consistente con il database di pubblicazione in termini di impostazioni e configurazione della replica.  
  
## Vedere anche  
 [Backup e ripristino di database SQL Server](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Backup e ripristino di database replicati](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Configurazione della distribuzione](../../../relational-databases/replication/configure-distribution.md)   
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Sottoscrizione delle pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md)   
 [Inizializzazione di una sottoscrizione](../../../relational-databases/replication/initialize-a-subscription.md)   
 [Sincronizzare i dati](../../../relational-databases/replication/synchronize-data.md)  
  
  