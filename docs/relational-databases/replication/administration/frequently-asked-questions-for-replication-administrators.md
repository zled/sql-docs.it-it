---
title: "Domande frequenti per gli amministratori di replica | Microsoft Docs"
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
  - "amministrazione della replica, domande frequenti"
  - "replica [SQL Server], amministrazione"
ms.assetid: 5a9e4ddf-3cb1-4baf-94d6-b80acca24f64
caps.latest.revision: 59
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 59
---
# Domande frequenti per gli amministratori di replica
  Le domande e risposte seguenti offrono indicazioni su una vasta gamma di attività svolte dagli amministratori dei database replicati.  
  
## Configurazione della replica  
  
### È necessario arrestare l'attività su un database quando questo viene pubblicato?  
 No. Durante la creazione di una pubblicazione l'attività sul database può proseguire. Tenere presente che la produzione di uno snapshot può impegnare una grande quantità di risorse, per questo conviene generare gli snapshot durante i periodi di minore attività sul database. Per impostazione predefinita, viene generato uno snapshot al termine della Creazione guidata nuova pubblicazione.  
  
### Durante la generazione dello snapshot le tabelle sono bloccate?  
 La durata dei blocchi dipende dal tipo di replica utilizzata:  
  
-   Per le pubblicazioni di tipo merge, l'agente snapshot non imposta alcun blocco.  
  
-   Per le pubblicazioni transazionali, l'agente snapshot per impostazione predefinita registra i blocchi solo durante la fase iniziale della generazione dello snapshot.  
  
-   Per le pubblicazioni snapshot, l'agente snapshot registra i blocchi durante l'intero processo di generazione dello snapshot.  
  
 Dato tuttavia che il blocco impedisce l'aggiornamento delle tabelle da parte di altri utenti, è consigliabile pianificare l'esecuzione dell'agente snapshot durante gli orari di minore attività del database, specialmente per le pubblicazioni snapshot.  
  
### Quando è disponibile una sottoscrizione? Quando è possibile utilizzare il database di sottoscrizione?  
 Una sottoscrizione è disponibile dopo che al database di sottoscrizione è stato applicato lo snapshot. Anche se il database di sottoscrizione è accessibile prima di questo momento, non dovrebbe essere utilizzato prima che sia stato applicato lo snapshot. Utilizzare Monitoraggio replica per verificare lo stato della generazione e dell'applicazione dello snapshot.  
  
-   Lo snapshot viene generato dall'agente snapshot. Visualizzare lo stato della generazione dello snapshot sul **agenti** scheda per una pubblicazione in Monitoraggio replica. Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
-   Lo snapshot viene applicato dall'agente di distribuzione o dall'agente di merge. Visualizzare lo stato dell'applicazione dello snapshot nel **agente di distribuzione** o **agente di Merge** pagina di monitoraggio replica. Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
### Cosa accade se l'agente snapshot non ha concluso la propria attività quando viene avviato l'agente di distribuzione o l'agente di merge?  
 L'esecuzione dell'agente di distribuzione o di merge in contemporanea con quella dell'agente snapshot non genera un errore. Tuttavia, è necessario considerare quanto segue:  
  
-   Se l'agente di distribuzione o di merge è configurato per essere eseguito in modo continuato, lo snapshot verrà applicato automaticamente al termine dell'esecuzione dell'agente snapshot.  
  
-   Se l'agente di distribuzione o di merge è configurato per essere eseguito in base a una pianificazione o su richiesta e quando viene eseguito non è disponibile alcuno snapshot, l'agente verrà chiuso e invierà un messaggio indicante che ancora non vi è uno snapshot disponibile. È necessario ripetere l'esecuzione dell'agente per applicare lo snapshot dopo l'esecuzione dell'agente snapshot. Per ulteriori informazioni sull'esecuzione degli agenti, vedere [sincronizzare una sottoscrizione Push](../../../relational-databases/replication/synchronize-a-push-subscription.md), [sincronizzare una sottoscrizione Pull](../../../relational-databases/replication/synchronize-a-pull-subscription.md), e [i concetti di file eseguibili dell'agente replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
### È necessario creare lo script della configurazione di replica?  
 Sì. La creazione dello script della configurazione di replica è un elemento fondamentale di qualunque piano di ripristino di emergenza per una topologia di replica. Per ulteriori informazioni sulla creazione di script, vedere [script di replica](../../../relational-databases/replication/scripting-replication.md).  
  
### Quale modello di recupero è necessario su un database replicato?  
 Le funzioni di replica che utilizzano correttamente uno dei modelli di recupero: con registrazione minima, con registrazione minima delle operazioni bulk o con registrazione completa. La replica di tipo merge tiene traccia delle modifiche archiviando le informazioni in tabelle di metadati. La replica transazionale tiene traccia delle modifiche contrassegnando il log delle transazioni, ma il modello di recupero non influisce su questo processo di contrassegno.  
  
### Perché la replica aggiunge una colonna alle tabelle replicate? Tale colonna viene rimossa se la tabella non viene pubblicata?  
 Per tener traccia delle modifiche, la replica di tipo merge e la replica transazionale con sottoscrizioni ad aggiornamento in coda devono essere in grado di identificare in modo univoco ogni riga di ogni tabella pubblicata. A tale scopo:  
  
-   Replica di tipo merge aggiunge la colonna **rowguid** a ogni tabella, a meno che la tabella include già una colonna di tipo di dati **uniqueidentifier** con il **ROWGUIDCOL** impostata (nel qual caso viene utilizzata in questa colonna). Se la tabella viene rimossa dalla pubblicazione, il **rowguid** colonna viene rimossa; se per il rilevamento è stata utilizzata una colonna esistente, la colonna non viene rimosso.  
  
-   Se una pubblicazione transazionale supporta le sottoscrizioni ad aggiornamento in coda, la replica aggiunge la colonna **msrepl_tran_version** a ogni tabella. Se la tabella viene rimossa dalla pubblicazione, il **msrepl_tran_version** colonna non viene rimosso.  
  
-   Non deve includere un filtro di **rowguidcol** utilizzata dalla replica per identificare le righe. Per impostazione predefinita la colonna aggiunta in fase di impostare la replica di tipo merge ed è denominato **rowguid**.  
  
### Come si gestiscono i vincoli sulle tabelle pubblicate?  
 Riguardo ai vincoli sulle tabelle pubblicate, è necessario considerare diversi elementi:  
  
-   La replica transazionale richiede un vincolo di chiave primaria in ogni tabella pubblicata. La replica di tipo merge non richiede una chiave primaria ma se ne contiene una è necessario che venga replicata. La replica snapshot non richiede una chiave primaria.  
  
-   Per impostazione predefinita i vincoli di chiave primaria, gli indici e i vincoli CHECK vengono replicati nei Sottoscrittori.  
  
-   Per impostazione predefinita, l'opzione NOT FOR REPLICATION viene specificata per i vincoli di chiave esterna e per i vincoli CHECK; questi vincoli vengono imposti per le operazioni dell'utente ma non per quelle dell'agente.  
  
 Per informazioni sull'impostazione delle opzioni di schema che consentono di controllare se i vincoli vengono replicati, vedere [specificare le opzioni dello Schema](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
### Come si gestiscono le colonne Identity?  
 La replica offre la gestione automatica dell'intervallo di valori Identity per le topologie di replica che includono aggiornamenti nel Sottoscrittore. Per ulteriori informazioni, vedere [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
### È possibile pubblicare gli stessi oggetti in pubblicazioni diverse?  
 Sì, ma con alcune restrizioni. Per ulteriori informazioni, vedere la sezione "Pubblicazione le tabelle in più pubblicazioni" nell'argomento [pubblicare dati e oggetti di Database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
### È possibile l'utilizzo dello stesso database di distribuzione da parte di più pubblicazioni?  
 Sì. Non vi sono restrizioni al numero o ai tipi di pubblicazioni che possono utilizzare lo stesso database di distribuzione. Tutte le pubblicazioni di un dato server di pubblicazione devono utilizzare lo stesso server di distribuzione e database di distribuzione.  
  
 Se si dispone di più pubblicazioni, è possibile configurare più database di distribuzione nel server di distribuzione per garantire che il flusso di dati che attraversa ogni database di distribuzione provenga da una sola pubblicazione. Utilizzare la **proprietà server di distribuzione** la finestra di dialogo o [sp_adddistributiondb & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) Per aggiungere un database di distribuzione. Per ulteriori informazioni sull'accesso nella finestra di dialogo, vedere [visualizzare e modificare server di distribuzione e le proprietà server di pubblicazione](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### In che modo è possibile reperire informazioni sul server di distribuzione e sul quello di pubblicazione, ad esempio per sapere quali oggetti di un database vengono pubblicati?  
 Queste informazioni sono disponibili tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e diverse stored procedure di replica. Per ulteriori informazioni, vedere [server di distribuzione e server di pubblicazione informazioni Script](../../../relational-databases/replication/administration/distributor-and-publisher-information-script.md).  
  
### La replica crittografa i dati?  
 No. La replica non crittografa i dati archiviati nel database o trasferiti nella rete. Per ulteriori informazioni, vedere la sezione "Crittografia" dell'argomento [Cenni preliminari sulla sicurezza & #40; Replica & #41;](../../../relational-databases/replication/security/security-overview-replication.md).  
  
### Come si replicano i dati su Internet?  
 È possibile replicare i dati su Internet utilizzando:  
  
-   Una rete privata virtuale (VPN). Per ulteriori informazioni, vedere [pubblicare dati su Internet utilizzando VPN](../../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md).  
  
-   L'opzione di sincronizzazione Web per la replica di tipo merge. Per ulteriori informazioni, vedere [sincronizzazione Web per la replica di tipo Merge](../../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Tutti i tipi di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la replica può replicare dati in una rete VPN, ma è consigliabile considerare la sincronizzazione Web se si utilizza la replica di tipo merge.  
  
### La replica viene ripresa in caso di interruzione della connessione?  
 Sì. L'elaborazione della replica viene ripresa dal punto in cui si era arrestata per interruzione della connessione. Se si utilizza la replica di tipo merge in una rete inaffidabile, è consigliabile considerare l'utilizzo dei record logici, che garantisce che le modifiche correlate vengano elaborate come una unità. Per ulteriori informazioni, vedere [modifiche a un gruppo di righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
### La replica funziona su connessioni a larghezza di banda ridotta? Utilizza la compressione?  
 Sì, la replica funziona su connessioni a larghezza di banda ridotta. Per le connessioni TCP/IP, utilizza la compressione offerta dal protocollo ma non offre una compressione aggiuntiva. Per le connessioni con sincronizzazione Web in HTTPS, utilizza la compressione offerta dal protocollo e la compressione aggiuntiva dei file XML utilizzati per replicare le modifiche.  
  
## Account di accesso e proprietà degli oggetti  
  
### Gli account di accesso e le password vengono replicati?  
 No. Per trasferire account di accesso e password da un server di pubblicazione a uno o più Sottoscrittori, si potrebbe creare un pacchetto DTS.  
  
### Cosa sono gli schemi e in che modo vengono replicati?  
 A partire da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], *schema* ha due significati:  
  
-   La definizione di un oggetto, come un'istruzione CREATE TABLE. Per impostazione predefinita, la replica copia le definizioni di tutti gli oggetti replicati nel Sottoscrittore.  
  
-   Lo spazio dei nomi in cui viene creato un oggetto: \< Database>. \< Schema>. \< oggetto>. Gli schemi vengono definiti utilizzando l'istruzione CREATE SCHEMA.  
  
-   In relazione agli schemi e alla proprietà degli oggetti, la replica ha il seguente comportamento predefinito nella Creazione guidata nuova pubblicazione:  
  
-   Per gli articoli di pubblicazioni di tipo merge con un livello di compatibilità 90 o superiore, per le pubblicazioni snapshot e quelle transazionali: per impostazione predefinita, il proprietario dell'oggetto nel Sottoscrittore è uguale al proprietario dell'oggetto corrispondente nel server di pubblicazione. Se nel Sottoscrittore non esistono gli schemi che possiedono gli oggetti, vengono creati automaticamente.  
  
-   Per gli articoli delle pubblicazioni di tipo merge con un livello di compatibilità inferiore a 90: per impostazione predefinita, il proprietario viene lasciato vuoto e viene specificato come **dbo** durante la creazione dell'oggetto nel Sottoscrittore.  
  
-   Per gli articoli delle pubblicazioni Oracle: per impostazione predefinita, il proprietario è specificato come **dbo**.  
  
-   Per articoli di pubblicazioni che usano snapshot in modalità carattere (usati per Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e Sottoscrittori [!INCLUDE[ssEW](../../../includes/ssew-md.md)]): per impostazione predefinita, il proprietario rimane vuoto. Il proprietario viene impostato sul proprietario associato all'account utilizzato dall'agente di distribuzione o dall'agente di merge per la connessione al Sottoscrittore.  
  
 Il proprietario dell'oggetto può essere modificato tramite la **Proprietà articolo - \<***articolo***>** la finestra di dialogo e tramite le stored procedure: **sp_addarticle**, **sp_addmergearticle**, **sp_changearticle**, e **sp_changemergearticle**. Per ulteriori informazioni, vedere [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md), [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md), e [visualizzare e modificare le proprietà di articolo](../../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
### In che modo è possibile configurare le concessioni del database di sottoscrizione per ottenere la corrispondenza con quelle del database di pubblicazione?  
 Per impostazione predefinita, la replica non esegue istruzioni GRANT nel database di sottoscrizione. Se si desidera che le autorizzazioni del database di sottoscrizione corrispondano a quelle del database di pubblicazione, utilizzare uno dei seguenti metodi.  
  
-   Eseguire le istruzioni GRANT direttamente nel database di sottoscrizione.  
  
-   Per eseguire le istruzioni, utilizzare uno script post-snapshot. Per ulteriori informazioni, vedere [eseguire script prima e dopo l'applicazione dello Snapshot](../../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Utilizzare la stored procedure [sp_addscriptexec](../../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md) per eseguire le istruzioni.  
  
### Cosa accade alle autorizzazioni concesse in un database di sottoscrizione se una sottoscrizione viene reinizializzata?  
 Per impostazione predefinita, gli oggetti nel Sottoscrittore vengono eliminati e ricreati quando viene reinizializzata una sottoscrizione, cosa che provoca l'eliminazione di tutte le autorizzazioni concesse per tali oggetti. Questa operazione può essere gestita in due modi:  
  
-   Riapplicare le concessioni dopo la reinizializzazione utilizzando le tecniche descritte nella sezione precedente.  
  
-   Specificare che gli oggetti non devono essere eliminati alla reinizializzazione della sottoscrizione. Prima della reinizializzazione, eseguire una delle seguenti operazioni:  
  
    -   Eseguire [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) o [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare il valore 'pre_creation_cmd' (**sp_changearticle**) o 'pre_creation_command' (**sp_changemergearticle**) per il parametro **@property** e il valore 'none', 'delete' o 'truncate' per il parametro **@value**.  
  
    -   Nel **Proprietà articolo - \< articolo>** nella finestra di dialogo di **oggetto di destinazione** selezionare un valore di **mantenere invariata oggetto esistente**, **eliminare dati. Se l'articolo contiene un filtro di riga, Elimina solo i dati che corrisponde al filtro.** o **Tronca tutti i dati nell'oggetto esistente** per l'opzione **azione se il nome è in uso**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
## Manutenzione database  
  
### Per quale motivo non è possibile eseguire TRUNCATE TABLE su una tabella pubblicata?  
 TRUNCATE TABLE è un'operazione non registrata che non attiva i trigger. Non è consentita perché la replica non può tener traccia delle modifiche provocate dall'operazione: la replica transazionale tiene traccia delle modifiche tramite il log delle transazioni, la replica di tipo merge tramite i trigger sulle tabelle pubblicate.  
  
### Quale è l'effetto dell'esecuzione di un comando BULK INSERT su un database replicato?  
 Per la replica transazionale, gli inserimenti bulk vengono rilevati e replicati come gli altri inserimenti. Per la replica di tipo merge, è necessario verificare che i metadati di rilevamento delle modifiche vengano aggiornati correttamente.  
  
### Il backup e il ripristino presentano delle considerazioni relativamente alla replica?  
 Sì. I database interessati alla replica richiedono alcune considerazioni speciali per i database. Per ulteriori informazioni, vedere [eseguire il backup e ripristino dei database replicati](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md).  
  
### La replica influisce sulla dimensione del log delle transazioni?  
 A differenza della replica di tipo merge e della replica snapshot, la replica transazionale può influire sulla dimensione del log delle transazioni. Se un database include una o più pubblicazioni transazionali, il log non viene troncato finché tutte le transazioni significative per le pubblicazioni non sono state recapitate al database di distribuzione. Se la dimensione del log delle transazioni aumenta in modo eccessivo e l'agente di lettura log viene eseguito in base a una pianificazione, è consigliabile ridurre l'intervallo tra le esecuzioni oppure impostare l'esecuzione in modalità continua. Se l'agente viene impostato per l'esecuzione in modalità continua (impostazione predefinita) verificare che venga eseguito. Per ulteriori informazioni sulla verifica dello stato di agente di lettura Log, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
 Inoltre, se nel database di pubblicazione o in quello di distribuzione è stata impostata l'opzione 'sync with backup', il troncamento del log delle transazioni avviene solo dopo il backup di tutte le transazioni. Se la dimensione del log delle transazioni sta aumentando in modo eccessivo e questa azione è stata impostata, è consigliabile accorciare l'intervallo tra l'esecuzione di operazioni di backup di tale log. Per ulteriori informazioni sul backup e ripristino dei database coinvolti nella replica transazionale, vedere [strategie di backup e ripristino di Snapshot e transazionali](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
### Come si ricompilano gli indici o le tabelle nei database replicati?  
 Per la ricompilazione degli indici esistono diversi meccanismi. Possono essere utilizzati tutti, senza considerazioni speciali per la replica, con la seguente eccezione: le chiavi primarie sono necessarie nelle tabelle delle pubblicazioni transazionali, pertanto non è possibile eliminare e ricreare le chiavi primarie su queste tabelle.  
  
### Come si aggiungono o si modificano gli indici nei database di pubblicazione e di sottoscrizione?  
 È possibile aggiungere gli indici nel server di pubblicazione o nei Sottoscrittori senza particolari considerazioni per la replica. Ricordare che gli indici possono influire sulle prestazioni. CREATE INDEX e ALTER INDEX non vengono replicati, pertanto se si aggiunge o si modifica un indice, ad esempio, nel server di pubblicazione, è necessario eseguire la stessa aggiunta o modifica nel Sottoscrittore se si desidera che venga riflessa in quest'ultimo.  
  
### Come si spostano o si rinominano i file per i database interessati alla replica?  
 Nelle versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prima di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], lo spostamento o la ridenominazione dei file di database richiede lo scollegamento e ricollegamento del database. Poiché un database replicato non può essere scollegato, innanzitutto era necessario rimuovere la replica da questi database. A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], è possibile spostare o rinominare i file senza scollegare e ricollegare il database, senza alcun effetto sulla replica. Per ulteriori informazioni sullo spostamento e ridenominazione di file, vedere [ALTER DATABASE & #40; Transact-SQL & #41;](../../../t-sql/statements/alter-database-transact-sql.md).  
  
### Come si elimina una tabella in corso di replica?  
 Prima di eliminare l'articolo dalla pubblicazione utilizzando [sp_droparticle](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md), [sp_dropmergearticle](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md), o **Proprietà pubblicazione - \< pubblicazione>** finestra di dialogo casella e quindi eliminarlo dal database utilizzando `DROP <Object>`. Dopo l'aggiunta di sottoscrizioni non è possibile eliminare articoli dalle pubblicazioni snapshot o transazionali: è necessario eliminare prima le sottoscrizioni. Per ulteriori informazioni, vedere [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### Come si aggiungono o si eliminano colonne in una tabella pubblicata?  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta un'ampia gamma di modifiche dello schema negli oggetti pubblicati, inclusa l'aggiunta e l'eliminazione di colonne. Ad esempio, se si esegue ALTER TABLE … DROP COLUMN nel server di pubblicazione, l'istruzione viene replicata ai Sottoscrittori e poi eseguita per eliminare la colonna. I sottoscrittori che eseguono versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prima di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] supporta l'aggiunta e l'eliminazione di colonne tramite le stored procedure [sp_repladdcolumn](../../../relational-databases/system-stored-procedures/sp-repladdcolumn-transact-sql.md) e [sp_repldropcolumn](../../../relational-databases/system-stored-procedures/sp-repldropcolumn-transact-sql.md). Per ulteriori informazioni, vedere [apportare le modifiche dello Schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
## Manutenzione della replica  
  
### Come si stabilisce se i dati nei Sottoscrittori sono sincronizzati con quelli nel server di pubblicazione?  
 Utilizzando la convalida. La convalida segnala se uno specifico Sottoscrittore è sincronizzato con il server di pubblicazione. Per ulteriori informazioni, vedere [convalidare i dati replicati](../../../relational-databases/replication/validate-replicated-data.md). Convalida non vengono fornite informazioni su quali righe se uno non sono sincronizzato correttamente, ma il [utilità tablediff](../../../tools/tablediff-utility.md) viene.  
  
### Come si aggiunge una tabella a una pubblicazione esistente?  
 Per aggiungere una tabella o un altro oggetto, non è necessario arrestare l'attività sui database di pubblicazione o di sottoscrizione. Aggiungere una tabella a una pubblicazione tramite il **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo o le stored procedure [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) e [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Per ulteriori informazioni, vedere [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### Come si rimuove una tabella da una pubblicazione?  
 Rimuovere una tabella dalla pubblicazione utilizzando [sp_droparticle](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md), [sp_dropmergearticle](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md), o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Dopo l'aggiunta di sottoscrizioni non è possibile eliminare articoli dalle pubblicazioni snapshot o transazionali: è necessario eliminare prima le sottoscrizioni. Per ulteriori informazioni, vedere [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### Quali azioni richiedono la reinizializzazione delle sottoscrizioni?  
 La reinizializzazione delle sottoscrizioni è necessaria per diverse modifiche degli articoli e delle pubblicazioni. Per ulteriori informazioni, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
### Quali azioni rendono non validi gli snapshot?  
 Vi sono diverse modifiche degli articoli e delle pubblicazioni che rendono non validi gli snapshot e richiedono la generazione di un nuovo snapshot. Per ulteriori informazioni, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
### Come si rimuove la replica?  
 Le azioni necessarie per rimuovere la replica da un database dipendono dalla funzione del database come database di pubblicazione, di sottoscrizione o entrambi.  
  
### In che modo è possibile determinare se vi sono transazioni o righe da replicare?  
 Per la replica transazionale, utilizzare le stored procedure o **comandi non distribuiti** scheda in Monitoraggio replica. Per ulteriori informazioni, vedere [Visualizza i comandi replicati e altre informazioni nel Database di distribuzione & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/monitor/view replicated commands and information in distribution database.md) e [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
 Per la replica di tipo merge, utilizzare la stored procedure **sp_showpendingchanges**. Per ulteriori informazioni, vedere [sp_showpendingchanges & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md).  
  
### Quanto rimane indietro l'agente di distribuzione? È necessario ripetere l'inizializzazione?  
 Utilizzare il **sp_replmonitorsubscriptionpendingcmds** stored procedure o **comandi non distribuiti** scheda in Monitoraggio replica. La stored procedure e la scheda mostrano:  
  
-   Numero di comandi nel database di distribuzione che non sono stati recapitati al Sottoscrittore selezionato. Un comando è composto da un'istruzione DDL (Data Definition Language) o da un'istruzione DML (Data Manipulation Language) Transact-SQL.  
  
-   Tempo stimato per il recapito dei comandi al Sottoscrittore. Se questo valore è maggiore del tempo necessario per generare uno snapshot e applicarlo al Sottoscrittore, potrebbe risultare conveniente reinizializzare il Sottoscrittore. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
 Per ulteriori informazioni, vedere [sp_replmonitorsubscriptionpendingcmds & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replmonitorsubscriptionpendingcmds-transact-sql.md) e [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Replica e altre funzionalità del database  
  
### La replica funziona insieme al log shipping e al mirroring del database?  
 Sì. Per ulteriori informazioni, vedere [Log Shipping e replica & #40; SQL Server & #41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md) e [il mirroring del Database e la replica e 40 #; SQL Server & #41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
### La replica funziona insieme al clustering?  
 Sì. Non vi sono considerazioni speciali, poiché tutti i dati vengono archiviati su un solo set di dischi nel cluster.  
  
## Vedere anche  
 [Amministrazione & #40; Replica & #41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Procedure consigliate per l'amministrazione della replica](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)  
  
  