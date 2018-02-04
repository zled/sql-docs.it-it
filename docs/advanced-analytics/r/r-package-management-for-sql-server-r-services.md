---
title: Gestione dei pacchetti R per SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: cebafeabd73260f166244e963754a2bd740bfe0f
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="r-package-management-for-sql-server"></a>Gestione dei pacchetti R per SQL Server

Questo articolo descrive le funzionalità per la gestione di pacchetti R in SQL Server 2017 e in SQL Server 2016.

+ Metodi consigliati per la gestione dei pacchetti R 
+ Modifiche nella gestione dei pacchetti tra SQL Server 2016 e 2017

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="recommended-methods-for-package-management"></a>Metodi consigliati per la gestione dei pacchetti

In SQL Server 2016 e SQL Server 2017, un amministratore del computer possa installare i pacchetti per ogni istanza in cui è stato attivato l'apprendimento. 

Pacchetti installati nel file system, utilizzando le librerie di istanza e non possono essere condivisa tra più istanze. Questo è il metodo consigliato per SQL Server 2016 e SQL Server 2017.

+ [Installare pacchetti R aggiuntivi su SQL Server](install-additional-r-packages-on-sql-server.md)
+ [Determinare i pacchetti che vengono installati in SQL Server](determine-which-packages-are-installed-on-sql-server.md)

Inoltre, se dispone di **dbo** l'appartenenza al ruolo in un'istanza di SQL Server in cui è stato attivato l'apprendimento, è possibile installare pacchetti R da un client remoto, utilizzando le nuove funzioni RevoScaleR.

+ [Nuove funzioni di R per l'installazione del pacchetto](#bkmk_remoteInstall)

### <a name="installation-on-servers-with-no-internet-access"></a>Installazione in un server senza accesso a Internet

Per rendere più semplice determinare le versioni del pacchetto R necessari e fornire tutte le dipendenze del pacchetto, è possibile utilizzare [miniCRAN](https://mran.microsoft.com/package/miniCRAN). Il pacchetto R accetta un elenco di pacchetti di destinazione e crea un repository locale che contiene i pacchetti di destinazione insieme a tutte le relative dipendenze, in formato compresso. È possibile quindi copiare che il server offline o condividere tra più istanze del repository.

Per ulteriori informazioni, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="python-packages"></a>Pacchetti di Python

Installazione di nuovi pacchetti Python segue le stesse linee guida: 

+ Esaminare i pacchetti Python in anticipo per determinare la compatibilità con la versione corrente di Python
+ Valutare l'idoneità di pacchetto di Python per un ambiente protezione avanzato di SQL Server
+ Utilizzare gli strumenti Python per installare i pacchetti come amministratore
+ Installare i pacchetti che devono essere eseguito nel contesto di SQL Server solo nella libreria di istanza. 
+ Se si utilizzano più ambienti di test, produzione e così via, verificare che la stessa versione del pacchetto Python sia installata nella libreria di istanza.

Per i passaggi di installazione, vedere [installare i nuovi pacchetti Python in SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="features-for-package-management-in-sql-server-2016-and-sql-server-2017"></a>Funzionalità per la gestione dei pacchetti in SQL Server 2016 e SQL Server 2017

SQL Server 2017 aggiunte alcune nuove funzionalità per supportare semplifica la gestione dei pacchetti R (e Python) dagli amministratori di database. Queste nuove funzionalità includono:

+ La possibilità di installare o gestire le librerie di pacchetto utilizzando T-SQL
+ Gestione delle autorizzazioni a livello di database tramite i ruoli del database. 

Nelle versioni future queste funzionalità devono fornire il metodo principale per la gestione dei pacchetti dagli amministratori di database e rendono più semplice per gli esperti di dati installare le librerie che necessarie.

Nello stesso momento, Microsoft R Server e Server di Machine Learning aggiunte nuove funzioni di R per rendere più semplice installare e condividere i pacchetti in un contesto di calcolo di SQL Server. Queste funzioni operano indipendentemente dalle funzionalità di SQL Server in base a T-SQL e sono destinate a essere eseguiti da un client remoto di R.

In questa sezione viene fornita una panoramica di queste funzionalità.

### <a name="bkmk_remoteInstall"></a>Nuove funzioni RevoScaleR per l'installazione del pacchetto 

Gli utenti con una versione recente di R Server o Server di Machine Learning possono inoltre utilizzare le nuove funzioni in [ **RevoScaleR** ](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) per installare i pacchetti in un'istanza specificata come contesto di calcolo di SQL Server.

+ L'esperto di dati è possibile installare pacchetti R necessari su SQL Server senza accedere direttamente al computer SQL Server. Tuttavia, l'utente deve essere un membro del proprietario del database (**dbo**) ruolo.

+ L'utente può condividere i pacchetti con altri utenti, installando i pacchetti con ambito condiviso. Altri utenti autorizzati dello stesso database di SQL Server possono accedere al pacchetto.

+ Gli utenti possono installare pacchetti privati che non sono visibili ad altri utenti, creazione di una sandbox privata per i pacchetti R.

+ Sincronizzazione del pacchetto consente semplice copia di backup e ripristino dei pacchetti

#### <a name="package-installation-functions"></a>Funzioni di installazione del pacchetto

Le funzioni di gestione pacchetti seguenti sono disponibili in RevoScaleR, per l'installazione e la rimozione dei pacchetti in un contesto di calcolo specificata:

-   [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages): trovare informazioni sui pacchetti installati nel contesto di calcolo specificato.

-   [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages): installare i pacchetti in un contesto di calcolo, da un repository specifico o leggendo salvato localmente compressi pacchetti.

-   [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages): rimuovere i pacchetti installati da un contesto di calcolo.

-   [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage): ottenere il percorso di uno o più pacchetti nel contesto di calcolo specificato.

-   [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages): copia di una libreria di pacchetti tra il file system e i database nei contesti di calcolo specificato.

-   [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths): ottenere il percorso di ricerca per gli alberi di libreria per i pacchetti durante l'esecuzione all'interno del Server SQL.

Per utilizzare queste funzioni, connettersi a un'istanza di SQL Server in cui si dispone delle autorizzazioni necessarie, utilizzando un contesto di calcolo di SQL Server. 

> [!IMPORTANT]
> Le credenziali utilizzate nella connessione di determinare se è possibile completare l'operazione nel server.

Queste funzioni di installazione del pacchetto verificare le dipendenze e assicurarsi che tutti i pacchetti correlati è possibile installare SQL Server, esattamente come l'installazione del pacchetto R nel contesto di calcolo locale. La funzione per la disinstallazione dei pacchetti calcola inoltre le dipendenze e verifica che i pacchetti che non sono più usati da altri pacchetti in SQL Server vengano rimossi, per liberare risorse.

Queste nuove funzioni sono incluse nella versione di RevoScaleR che viene installato in SQL Server 2017. È inoltre possibile ottenere queste funzioni [l'aggiornamento dell'istanza di SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) per utilizzare una versione recente di [Microsoft R Server o Server di Machine Learning](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server). Richiede la versione 9.0.1 o versione successiva.

#### <a name="package-synchronization-functions"></a>Funzioni di sincronizzazione di pacchetto

Sincronizzazione del pacchetto è una nuova funzionalità per solo i pacchetti R. Il motore di database rileva i pacchetti che vengono utilizzati da un proprietario specifico e un gruppo e scrivere tali pacchetti nel file System, se necessario. In genere si usa la sincronizzazione di pacchetto in questi scenari:

+ Si desidera spostare pacchetti R tra istanze di SQL Server.
+ È necessario reinstallare i pacchetti per un utente specifico o un gruppo dopo il ripristino di un database.

Per ulteriori informazioni su come abilitare e usare questa funzionalità, vedere [sincronizzazione del pacchetto R per SQL Server](package-install-uninstall-and-sync.md).

### <a name="package-management-using-t-sql"></a>Gestione dei pacchetti utilizzando T-SQL

SQL Server 2017 aggiunte nuove istruzioni T-SQL per consentire all'amministratore di database maggiore controllo sui pacchetti R a livello di database. L'amministratore di database non necessario per imparare a usare R o Python tools, ma deve essere in grado di fornire agli utenti di R o Python la possibilità di installare i pacchetti necessari e condividerli con altri utenti.

Questa caratteristica può semplificare la gestione di collaborazione e la versione negli ambienti multiutente: ad esempio:

+ Si desidera condividere i pacchetti che è stata sviluppata con altri utenti del team.
+ Gli analisti più funzionino nello stesso database e debbano utilizzare versioni diverse dello stesso pacchetto.
+ Si desidera spostare pacchetti e le relative autorizzazioni allo stesso tempo che si sposta un database o quando si esegue il backup e le operazioni di ripristino.

Gestione dei pacchetti in SQL Server 2017 si basa su questi nuovi oggetti di database e funzionalità:

+ [Nuovi ruoli del database](#bkmk_roles), per la gestione dei pacchetti di accesso e usare
+ [Creazione libreria esterna](#bkmk_createExternalLibrary) istruzione per il caricamento delle librerie del pacchetto nel server

Utilizzo di queste funzionalità richiede alcune attività di preparazione aggiuntive all'istanza e il livello di database: 

+  L'amministratore del database è necessario abilitare esplicitamente la funzionalità di gestione del pacchetto eseguendo uno script che crea gli oggetti di database necessari. Per ulteriori informazioni, vedere [come abilitare la gestione dei pacchetti R](r-package-how-to-enable-or-disable.md).

+ Gli utenti devono essere assegnati ai ruoli a livello di database. Questi ruoli consentono agli utenti di installare pacchetti condivisi o privati.

+ Librerie del pacchetto possono essere installate utilizzando la nuova istruzione T-SQL, creare libreria esterna. Tuttavia, tutte le dipendenze del pacchetto devono essere preparate in anticipo e installate come parte di un singolo file compresso.

> [!NOTE]
> Anche se le funzionalità descritte di seguito sono completamente funzionali in questa fase, le versioni future contengono ulteriori miglioramenti per rendere più semplice per preparare le librerie di pacchetto e per gestire le dipendenze. Se si ha familiarità con l'installazione del pacchetto R, è consigliabile continuare a utilizzare gli strumenti R per ora.

#### <a name="bkmk_createExternalLibrary"></a>CREARE UNA LIBRERIA ESTERNA 

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

Per garantire che tutte le dipendenze dei pacchetti disponibili, è consigliabile utilizzare [miniCRAN](create-a-local-package-repository-using-minicran.md) per creare un repository locale. È quindi possibile utilizzare tale file compresso per installare il pacchetto di destinazione e le relative dipendenze.

#### <a name="bkmk_roles"></a>Ruoli predefiniti del database per la gestione dei pacchetti 

I nuovi ruoli disponibili in SQL Server per la gestione dei pacchetti non sono inclusi per impostazione predefinita, anche nelle istanze in cui è stato installato e attivato l'apprendimento. È necessario aggiungere i ruoli eseguendo uno script come descritto qui: [abilitare o disabilitare la gestione dei pacchetti](r-package-how-to-enable-or-disable.md).

Dopo aver eseguito questo script, verrà visualizzato i seguente nuovi ruoli del database:

+ `rpkgs-users`: I membri di questo ruolo possono utilizzare qualsiasi pacchetto condiviso che è stato installato da un altro `rpkgs-shared` membro del ruolo.

+ `rpkgs-private`: I membri di questo ruolo hanno accesso ai pacchetti condivisi con le stesse autorizzazioni dei membri del `rpkgs-users` ruolo. Membri di questo ruolo possono inoltre installare, rimuovere e utilizzare pacchetti privatamente con ambiti.

+ `rpkgs-shared`: I membri di questo ruolo dispongono delle stesse autorizzazioni dei membri del `rpkgs-private` ruolo. Inoltre, i membri di questo ruolo possono installare o rimuovere pacchetti condivisi.

+ `db_owner`: I membri di questo ruolo dispongono delle stesse autorizzazioni dei membri del `rpkgs-shared` ruolo. Inoltre, i membri di questo ruolo possono **concedere** altri utenti il diritto di installare o rimuovere entrambi condivisi e pacchetti privati.

L'amministratore di database possono aggiungere utenti a ruoli di un singolo database.



## <a name="next-steps"></a>Passaggi successivi

[Gestione dei pacchetti per l'apprendimento automatico di SQL Server](r-package-management-for-sql-server-r-services.md)
