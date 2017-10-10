---
title: Gestione dei pacchetti R per SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 10/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 7
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: e0c6725ff2c0c541e2546858dc02f1021812bbc5
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="r-package-management-for-sql-server"></a>Gestione dei pacchetti R per SQL Server

Questo articolo descrive le funzionalità per la gestione di pacchetti R in SQL Server 2017 e SQL Server 2016.

+ Modifiche nei metodi di installazione del pacchetto R tra 2016 e 2017
+ Metodi consigliati per la gestione dei pacchetti R
+ Nuovi ruoli del database per la gestione di pacchetti in SQL Server 2017
+ Nuova istruzione T-SQL per la gestione di pacchetti in SQL Server 2017

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="differences-in-package-management-between-sql-server-2016-and-sql-server-2017"></a>Differenze nella gestione dei pacchetti di SQL Server 2016 e SQL Server 2017

In **SQL Server 2017**, è possibile abilitare la gestione dei pacchetti a livello di istanza e gestire le autorizzazioni utente per aggiungere o utilizzare i pacchetti a livello di database.

È necessario che l'amministratore del database attiva la funzionalità di gestione del pacchetto eseguendo uno script che crea gli oggetti di database necessari. Per ulteriori informazioni, vedere [come abilitare la gestione dei pacchetti R](r-package-how-to-enable-or-disable.md).

In **SQL Server 2016**, un amministratore deve installare pacchetti R nella libreria R associata all'istanza. Tutti gli utenti di eseguire il codice R nell'istanza di utilizzano questi pacchetti. Il codice R in esecuzione in SQL server non è possibile utilizzare pacchetti installati nelle librerie utente. Tuttavia, l'amministratore può concedere singoli utenti la possibilità di eseguire gli script R in un database specifico.

**Riepilogo delle differenze e vantaggi**

+ Se si utilizza servizi di Machine Learning in SQL Server 2017, è possibile gestire e installare pacchetti R utilizzando il metodo tradizionale, basato su strumenti di R oppure utilizzando i nuovi ruoli del database e le istruzioni T-SQL.

+ È consigliabile che il secondo metodo, perché fornisce un controllo più accurato dagli amministratori, è associata una maggiore libertà per gli utenti. Ad esempio, gli utenti possono installare i propri pacchetti, tramite una stored procedure o tramite codice R e pacchetti di condivisione con altri utenti. 

    Poiché i pacchetti possono essere limitati a un database e ogni utente disponga di una sandbox pacchetto isolato, risulta più semplice installare le versioni diverse dello stesso pacchetto R. È possibile anche copiare o spostare gli utenti e dei relativi pacchetti tra database. 

+ Uso della funzionalità di gestione di pacchetti in SQL Server rende molto più semplice le operazioni di backup e ripristino. Quando si esegue la migrazione di database di lavoro in un nuovo server, è possibile utilizzare la funzione di sincronizzazione del pacchetto per leggere un elenco di tutti i pacchetti e installarli in un database nel nuovo server.

+ Può risultare più semplice installare i pacchetti R come amministratore nel computer, utilizzando gli strumenti R tradizionali, se si è l'unica persona che utilizza il server per i processi di machine learning.

+ Se si utilizza SQL Server 2016 R Services, è necessario continuare a installare pacchetti R usati dall'istanza utilizzando gli strumenti di R > Assicurarsi di utilizzare la libreria di R associata all'istanza.

Nelle sezioni seguenti forniscono ulteriori dettagli su come gestione dei pacchetti viene eseguita tramite queste due opzioni.

## <a name="r-package-management-using-t-sql"></a>Gestione dei pacchetti R utilizzando T-SQL

SQL Server 2017 include nuove istruzioni T-SQL che consentono all'amministratore di database maggiore controllo sui pacchetti R a livello di database. Allo stesso tempo, l'amministratore di database consentono agli utenti la possibilità di installare i pacchetti necessari e condividerli con altri utenti.

Se è necessario condividere i pacchetti con altri utenti oppure se è necessario eseguire i processi di machine learning nel server di più persone, è consigliabile abilitare gestione dei pacchetti, assegnare utenti a ruoli del database e carica i pacchetti in modo che gli utenti possano condividerli.

Gestione dei pacchetti in SQL Server 2017 si basa su questi nuovi oggetti di database e funzionalità:

+ Nuovi ruoli del database, per la gestione di utilizzo e accesso ai pacchetti
+ Ambito del pacchetto, per separare condiviso e pacchetti privati
+ Istruzione CREATE libreria esterna, per il caricamento di nuove librerie di codice per il server
+ Contesto di calcolo di nuove funzioni di R in RevoScaleR, per il supporto di installazione dei pacchetti in SQL Server
+ Sincronizzazione del pacchetto, per garantire una semplice copia di backup e ripristino dei pacchetti

### <a name="database-roles-for-package-management"></a>Ruoli di database per la gestione dei pacchetti

L'amministratore del database è necessario creare i ruoli utilizzati per la gestione dei pacchetti eseguendo uno script come descritto qui: [abilitare o disabilitare la gestione dei pacchetti](r-package-how-to-enable-or-disable.md).

Dopo aver eseguito questo script, verrà visualizzato i seguente nuovi ruoli del database:

+ `rpkgs-users`: I membri di questo ruolo possono utilizzare qualsiasi pacchetto condiviso che è stato installato da un altro `rpkgs-shared` membro del ruolo.

+ `rpkgs-private`: I membri di questo ruolo hanno accesso ai pacchetti condivisi con le stesse autorizzazioni dei membri del `rpkgs-users` ruolo. Membri di questo ruolo possono inoltre installare, rimuovere e utilizzare pacchetti privatamente con ambiti.

+ `rpkgs-shared`: I membri di questo ruolo dispongono delle stesse autorizzazioni dei membri del `rpkgs-private` ruolo. Inoltre, i membri di questo ruolo possono installare o rimuovere pacchetti condivisi.

+ `db_owner`: I membri di questo ruolo dispongono delle stesse autorizzazioni dei membri del `rpkgs-shared` ruolo. Inoltre, i membri di questo ruolo possono **concedere** altri utenti il diritto di installare o rimuovere entrambi condivisi e pacchetti privati.

L'amministratore di database consente di aggiungere utenti ai ruoli di base, per ogni database per controllare il possibilità di installare i pacchetti.

### <a name="package-scope"></a>Ambito del pacchetto

La nuova funzionalità di gestione di pacchetti distinguere i pacchetti dal fatto che sono private o può essere condiviso da più utenti.

+ **Ambito condiviso**

    *Ambito condiviso* significa che gli utenti che dispone dell'autorizzazione per il ruolo di ambito condiviso (`rpkgs-shared`) può installare e disinstallare i pacchetti a un database specificato. Un pacchetto installato in una libreria di ambito condiviso può essere usato da altri utenti del database in SQL Server, purché tali utenti siano autorizzati a usare pacchetti R installati.

+ **Ambito privato**

    *Ambito privato* significa che gli utenti che sono stato assegnato l'appartenenza al ruolo di ambito privato (`rpkgs-private`) possono installare o disinstallare pacchetti in un percorso di libreria privato definito per ogni utente. Pertanto, i pacchetti installati nell'ambito privato possono essere usati solo dall'utente che li ha installati. In altre parole, un utente di SQL Server non può usare pacchetti privati che sono stati installati da un altro utente.

Questi modelli per ambito *condiviso* e *privato* possono essere combinati per sviluppare sistemi di sicurezza personalizzati per distribuire e gestire pacchetti in SQL Server.

Ad esempio, in un ambito condiviso, al responsabile di un gruppo di analisti di dati può essere concessa l'autorizzazione per installare i pacchetti e tali pacchetti possono quindi essere usati da tutti gli altri utenti o analisti di dati nella stessa istanza di SQL Server.

Un altro scenario può richiedere maggiore isolamento tra gli utenti o l'uso di diverse versioni dei pacchetti. In tal caso, è possibile usare l'ambito privato per concedere autorizzazioni individuali agli analisti di dati, che saranno responsabili dell'installazione e dell'uso dei soli pacchetti di cui hanno bisogno. Poiché l'installazione dei pacchetti viene eseguita per singolo utente, i pacchetti installati da un utente non influiscono sul lavoro degli altri utenti dello stesso database di SQL Server.

### <a name="create-external-library"></a>CREARE UNA LIBRERIA ESTERNA

Il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) è una nuova istruzione T-SQL introdotta in SQL Server 2017 che consentono all'amministratore del database con i pacchetti senza dover strumenti utente R. 

Utilizzare il **creare libreria esterna** istruzione di caricare librerie esterne a un'istanza nel formato di file compresso. Gli utenti autorizzati possono quindi accedere alle librerie e installarli per uso personale.

Ad esempio, è possibile creare più copie del progetto R, ciascuno di essi per una versione diversa. Caricamento come librerie separate consente di mantenere alcune versioni private e alcune versioni di condividere con altri utenti.

Fondamentalmente, "library" è una raccolta di pacchetti esterni che si desidera rendere disponibili agli utenti in un unico nome. Ad esempio, si può pubblicare i seguenti a SQL Server come una libreria esterna:

+ Un singolo pacchetto R che scritti, senza dipendenze
+ Un pacchetto che si desidera installare e dipendenze necessari per l'installazione
+ Una raccolta di pacchetti R correlati a un'attività specifica o il progetto, con le relative dipendenze

Il nome della libreria consente di gestire il pacchetto o la raccolta di pacchetti in SQL Server e può essere indipendente dei pacchetti installati. Tuttavia, i nomi delle librerie deve essere univoci in tutta l'istanza.

Per utilizzare questa istruzione, la funzionalità di gestione del pacchetto deve essere abilitata nell'istanza. Per ulteriori informazioni, vedere [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

> [!NOTE]
> Attualmente è possibile utilizzare questa istruzione per creare raccolte basate solo su Windows per previsto il supporto di R. in futuro per i pacchetti Python e per i pacchetti eseguiti su altre piattaforme, ad esempio Linux.

Dopo la libreria esterna è stata caricata nel server, è necessario installarlo nella libreria di pacchetti R associati all'istanza. Esistono diversi modi per eseguire questa operazione:

+ Eseguire il comando standard di R `install.packages` in sp_execute_external_script. Assicurarsi di connettersi utilizzando un account che disponga delle autorizzazioni per installare i pacchetti.

+ Connettersi a SQL Server da un client remoto di R ed eseguire [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) nel contesto di calcolo di SQL Server. Nuovamente, è necessario disporre delle autorizzazioni necessarie per installare i pacchetti in un ambito privato o condiviso per eseguire questa operazione.

Per esempi di installazione con R e T-SQL, vedere [installare pacchetti aggiuntivi su SQL Server](install-additional-r-packages-on-sql-server.md).

### <a name="new-r-functions-for-package-installation"></a>Nuove funzioni di R per l'installazione del pacchetto

Dopo che sono stati abilitati i ruoli del database per la gestione dei pacchetti, gli utenti possono anche utilizzare le nuove funzioni in [ **RevoScaleR** ](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) per installare i pacchetti nell'istanza specificata come contesto di calcolo di SQL Server.

+ L'esperto di dati è possibile installare pacchetti R necessari su SQL Server senza accedere direttamente al computer SQL Server.

+ Un utente può installare un pacchetto e condividere con altri utenti, installando il pacchetto con ambito condiviso. Quindi ad altri utenti autorizzati dello stesso database di SQL Server possono accedere al pacchetto.

+ Gli utenti possono installare pacchetti privati che non sono visibili ad altri utenti, creazione di una sandbox privata per i pacchetti R.

Le funzioni di gestione pacchetti seguenti sono disponibili in RevoScaleR, per l'installazione e la rimozione dei pacchetti in un contesto di calcolo specificata:

-   [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): trovare informazioni sui pacchetti installati nel contesto di calcolo specificato.

-   [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): installare i pacchetti in un contesto di calcolo, da un repository specifico o leggendo salvato localmente compressi pacchetti.

-   [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): rimuovere i pacchetti installati da un contesto di calcolo.

-   [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): ottenere il percorso di uno o più pacchetti nel contesto di calcolo specificato.

-   [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): copia di una libreria di pacchetti tra il file system e i database nei contesti di calcolo specificato.

-   [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): ottenere il percorso di ricerca per gli alberi di libreria per i pacchetti durante l'esecuzione all'interno del Server SQL.

Per utilizzare queste funzioni, connettersi a un'istanza di SQL Server in cui si dispone delle autorizzazioni necessarie, utilizzando un contesto di calcolo di SQL Server. Quando ci si connette, le credenziali di determinano se è possibile completare l'operazione nel server.

Le funzioni per l'installazione dei pacchetti verificano se sono presenti dipendenze e se eventuali pacchetti correlati possono essere installati in SQL Server, in modo analogo all'installazione di pacchetti R nel contesto di calcolo locale. La funzione per la disinstallazione dei pacchetti calcola inoltre le dipendenze e verifica che i pacchetti che non sono più usati da altri pacchetti in SQL Server vengano rimossi, per liberare risorse.

> [!NOTE]
> 
> Queste nuove funzioni sono inclusi per impostazione predefinita in SQL Server 2017. È possibile aggiornare la versione di RevoScaleR per ottenere queste funzioni per l'aggiornamento dell'istanza per l'utilizzo di una versione successiva di Microsoft R Server, ad esempio Microsoft R Server 9.0.1.
> 
> Per ulteriori informazioni, vedere [utilizzando SqlBindR.exe a upgradeR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="synchronization-of-r-package-libraries"></a>Sincronizzazione delle librerie del pacchetto R

La versione CTP 2.0 di SQL Server 2017 (e la versione di aprile 2017 di Microsoft R Server) include nuove funzioni di R per *sincronizzazione pacchetti*.

La sincronizzazione di pacchetto indica che il motore di database rileva i pacchetti che vengono utilizzati da un proprietario specifico e un gruppo e scrivere tali pacchetti nel file System, se necessario. È possibile utilizzare la sincronizzazione di pacchetto in questi scenari:

+ Si desidera spostare pacchetti R tra istanze di SQL Server.
+ È necessario reinstallare i pacchetti per un utente specifico o un gruppo dopo il ripristino di un database.

Per ulteriori informazioni su come abilitare e usare questa funzionalità, vedere [sincronizzazione del pacchetto R per SQL Server](package-install-uninstall-and-sync.md).

## <a name="r-package-management-using-traditional-r-tools"></a>Gestione dei pacchetti R utilizzando gli strumenti tradizionali R

Il metodo tradizionale per la gestione dei pacchetti R in un'istanza è per l'installazione e l'elenco dei pacchetti utilizzando i comandi e gli strumenti di R. 

+ Questa opzione potrebbe essere l'unica opzione se si utilizza una versione preliminare di SQL Server 2016.  
+ Questa opzione potrebbe inoltre risultare utile se si sono l'unico utente di pacchetti R e si dispone dell'accesso amministrativo al server.
+ Per semplificare la gestione delle versioni del pacchetto R, è possibile utilizzare [miniCRAN](create-a-local-package-repository-using-minicran.md) per creare un repository locale e condividere che tra le istanze.

Per informazioni dettagliate, vedere i seguenti articoli:

+ [Installare pacchetti R aggiuntivi su SQL Server](install-additional-r-packages-on-sql-server.md)
+ [Determinare i pacchetti che vengono installati in SQL Server](determine-which-packages-are-installed-on-sql-server.md)

Per SQL Server 2017, è consigliabile utilizzare Crea raccolta esterni e i ruoli del database fornisce per gestire utenti e i relativi pacchetti R.

## <a name="next-steps"></a>Passaggi successivi

[Come abilitare o disabilitare la gestione dei pacchetti R](../r/r-package-how-to-enable-or-disable.md)

