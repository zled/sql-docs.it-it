---
title: Gestione dei pacchetti R per SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 08/20/2017
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f19982251b629d12215595685c0633b4c6b61c98
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="r-package-management-for-sql-server"></a>Gestione dei pacchetti R per SQL Server

In questo argomento vengono descritte le funzionalità di gestione di pacchetto che è possibile utilizzare per gestire i pacchetti R vengono eseguiti in un'istanza di SQL Server.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="package-management-using-t-sql"></a>Gestione dei pacchetti utilizzando T-SQL

È possibile continuare a installare pacchetti R come amministratore nel computer, se si dispone di questi privilegi, e se si è l'unica persona che utilizza il server per i processi di machine learning.

Tuttavia, se si desidera condividere i pacchetti con altri utenti o più utenti necessitano di eseguire i processi di machine learning nel server, è più efficiente per configurare una libreria condivisa pacchetto. SQL Server supporta questo tramite i ruoli predefiniti del database.

L'amministratore del database è responsabile della configurazione dei ruoli e aggiungere utenti ai ruoli. Tramite i ruoli, l'amministratore del database è possibile controllare chi dispone dell'autorizzazione per aggiungere o rimuovere pacchetti R dall'ambiente di SQL Server e controllare l'installazione del pacchetto.

### <a name="database-roles-for-package-management"></a>Ruoli di database per la gestione dei pacchetti

I nuovi ruoli del database seguenti supportano l'installazione sicura e gestione di pacchetti R in SQL Server:

- `rpkgs-users`: Consente agli utenti di usare tutti i pacchetti condivisi che sono stati installati da membri del `rpkgs-shared` ruolo.

- `rpkgs-private`: Fornisce l'accesso ai pacchetti condivisi con le stesse autorizzazioni di `rpkgs-users` ruolo. I membri di questo ruolo possono inoltre installare, rimuovere e usare pacchetti con ambito privato.

-  `rpkgs-shared`: Fornisce le stesse autorizzazioni di `rpkgs-private` ruolo. Gli utenti membri di questo ruolo possono anche installare o rimuovere i pacchetti condivisi.

- `db_owner`: Contiene le stesse autorizzazioni di `rpkgs-shared` ruolo. Può inoltre concedere agli utenti il diritto di installare o rimuovere pacchetti sia condivisi che privati.

### <a name="creating-an-external-package-library-using-t-sql"></a>Creazione di una libreria pacchetto esterno utilizzando T-SQL

Inoltre, SQL Server 2017 supporta l'istruzione T-SQL, **creare libreria esterna**, per supportare la gestione di amministratori di database di librerie esterne. Attualmente è possibile utilizzare questa istruzione per creare raccolte basate su Windows per R. aggiuntive previsto il supporto in futuro per i pacchetti Python e per i pacchetti scritti per l'esecuzione su altre piattaforme, ad esempio Linux.

Per ulteriori informazioni, vedere [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="package-management-using-r"></a>Gestione dei pacchetti con R

Il **RevoScaleR** pacchetto ora include funzioni per supportare più facile installazione e la gestione di pacchetti R. Queste nuove funzioni, combinate con i ruoli del database per la gestione dei pacchetti, supporta questi scenari:

- L'esperto di dati è possibile installare pacchetti R necessari su SQL Server senza dover accedere al computer SQL Server.
- I pacchetti vengono installati in un singolo database e quando il database viene spostato, i pacchetti spostati con esso.
- È facile condividere i pacchetti con altri utenti. Se si configura un repository di pacchetti locale, ogni esperto di dati è possibile usare il repository per installare i pacchetti in un proprio database.
- L'amministratore del database di non dover imparare a eseguire i comandi di R e non è necessario tenere traccia delle dipendenze di pacchetto complesso.
- L'amministratore di database è possibile utilizzare ruoli di database familiari per controllare quali utenti di SQL Server è consentiti installare, disinstallare o utilizzare i pacchetti.

### <a name="r-package-management-functions"></a>Funzioni di gestione di pacchetti R

Le funzioni di gestione pacchetti seguenti sono disponibili in RevoScaleR, per l'installazione e la rimozione dei pacchetti in un contesto di calcolo specificata:

+ [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): trovare informazioni sui pacchetti installati nel contesto di calcolo specificato.

+ [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): installare i pacchetti in un contesto di calcolo, da un repository specifico o leggendo salvato localmente compressi pacchetti.

+ [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): rimuovere i pacchetti installati da un contesto di calcolo.

+ [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): ottenere il percorso di uno o più pacchetti nel contesto di calcolo specificato.

+ [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): copia di una libreria di pacchetti tra il file system e i database nei contesti di calcolo specificato.

+ [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): ottenere il percorso di ricerca per gli alberi di libreria per i pacchetti durante l'esecuzione all'interno del Server SQL.

Questi pacchetti sono inoltre inclusi per impostazione predefinita in SQL Server 2017. È possibile aggiungere i pacchetti a un'istanza di SQL Server 2016, se si esegue l'aggiornamento dell'istanza da utilizzare almeno Microsoft R 9.0.1. Per ulteriori informazioni, vedere [SqlBindR.exe utilizzando per eseguire l'aggiornamento R](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

Per informazioni su queste funzioni, vedere le pagine di riferimento di funzione RevoScaleR: (https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

## <a name="how-package-management-works"></a>Funzionamento di gestione dei pacchetti

Se si dispone dell'autorizzazione per installare i pacchetti, eseguire una delle funzioni di gestione dei pacchetti del codice R e specificare il contesto di calcolo in cui i pacchetti devono essere aggiunti o rimossi. Il contesto di calcolo può essere il computer locale o un database nell'istanza di SQL Server. Se viene eseguita la chiamata per installare i pacchetti in SQL Server, le credenziali determinano se l'operazione può essere completata sul server. Le funzioni per l'installazione dei pacchetti verificano se sono presenti dipendenze e se eventuali pacchetti correlati possono essere installati in SQL Server, in modo analogo all'installazione di pacchetti R nel contesto di calcolo locale. La funzione per la disinstallazione dei pacchetti calcola inoltre le dipendenze e verifica che i pacchetti che non sono più usati da altri pacchetti in SQL Server vengano rimossi, per liberare risorse.

Ogni esperto di dati è possibile installare pacchetti privati che non sono visibili ad altri utenti, creazione di una sandbox privata per i pacchetti R. Poiché i pacchetti possono essere limitati a un database e ogni utente disponga di una sandbox pacchetto isolato in ogni database, è più facile da installare versioni diverse dello stesso pacchetto R.

Se si esegue la migrazione di database di lavoro in un nuovo server, è possibile utilizzare la funzione di sincronizzazione del pacchetto per leggere un elenco di tutti i pacchetti e installarli in un database nel nuovo server.

> [!NOTE]
> 
> Le funzioni R per la gestione dei pacchetti disponibili a partire da Microsoft R Server 9.0.1. Se è possibile trovare le funzioni in RevoScaleR, è probabilmente necessario eseguire l'aggiornamento alla versione più recente.

### <a name="bkmk_scope"></a>Definizione dell'ambito dei pacchetti dal ruolo

Le nuove funzioni di gestione dei pacchetti forniscono due ambiti per l'installazione e l'uso di pacchetti in SQL Server in uno specifico database:

- **Ambito condiviso**

  *Ambito condiviso* significa che gli utenti che dispone dell'autorizzazione per il ruolo di ambito condiviso (`rpkgs-shared`) può installare e disinstallare i pacchetti a un database specificato. Un pacchetto installato in una libreria di ambito condiviso può essere usato da altri utenti del database in SQL Server, purché tali utenti siano autorizzati a usare pacchetti R installati.

- **Ambito privato**

  *Ambito privato* significa che gli utenti che sono stato assegnato l'appartenenza al ruolo di ambito privato (`rpkgs-private`) possono installare o disinstallare pacchetti in un percorso di libreria privato definito per ogni utente. Pertanto, i pacchetti installati nell'ambito privato possono essere usati solo dall'utente che li ha installati. In altre parole, un utente di SQL Server non può usare pacchetti privati che sono stati installati da un altro utente.

Questi modelli per ambito *condiviso* e *privato* possono essere combinati per sviluppare sistemi di sicurezza personalizzati per distribuire e gestire pacchetti in SQL Server.

Ad esempio, in un ambito condiviso, al responsabile di un gruppo di analisti di dati può essere concessa l'autorizzazione per installare i pacchetti e tali pacchetti possono quindi essere usati da tutti gli altri utenti o analisti di dati nella stessa istanza di SQL Server.

Un altro scenario può richiedere maggiore isolamento tra gli utenti o l'uso di diverse versioni dei pacchetti. In tal caso, è possibile usare l'ambito privato per concedere autorizzazioni individuali agli analisti di dati, che saranno responsabili dell'installazione e dell'uso dei soli pacchetti di cui hanno bisogno. Poiché l'installazione dei pacchetti viene eseguita per singolo utente, i pacchetti installati da un utente non influiscono sul lavoro degli altri utenti dello stesso database di SQL Server.

### <a name="synchronizing-r-package-libraries"></a>La sincronizzazione delle librerie del pacchetto R

La versione CTP 2.0 di SQL Server 2017 (e la versione di aprile 2017 di Microsoft R Server) include nuove funzioni di R per *sincronizzazione pacchetti*.

La sincronizzazione di pacchetto indica che il motore di database rileva i pacchetti che vengono utilizzati da un proprietario specifico e un gruppo e scrivere tali pacchetti nel file System, se necessario. È possibile utilizzare la sincronizzazione di pacchetto in questi scenari:

+ Si desidera spostare pacchetti R tra istanze di SQL Server
+ È necessario installare nuovamente i pacchetti per un utente specifico o di gruppo dopo il ripristino di un database

Per ulteriori informazioni, vedere [rxSyncPackages](../r/package-install-uninstall-and-sync.md).

## <a name="examples"></a>Esempi

Questi esempi illustrano l'uso di base per le funzioni di gestione del pacchetto. Per eseguire questi comandi è necessario disporre dell'autorizzazione per eseguire i comandi di R nell'istanza.

+ Quando si esegue da un terminale di R remoto, creare un oggetto di contesto di calcolo specifica di un'istanza di SQL Server e quindi eseguire le funzioni, passando il contesto di calcolo come argomento.

+ Per eseguire funzioni di gestione dei pacchetti da una stored procedure, è necessario eseguirne il wrapping in una chiamata a `sp_execute_external_script`.

### <a name="package-scoping"></a>Dell'ambito del pacchetto

Questo esempio viene verificata per i pacchetti che sono stati installati nell'istanza `myServer`, nel database `TestDB`. Gestione dei pacchetti di ambito è un database specifico e un utente. Se l'utente non è specificato, viene utilizzato l'utente che esegue la chiamata di contesto di calcolo. Per ulteriori informazioni, vedere [Scoping dei pacchetti dal ruolo](#bkmk_scope).

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;");
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerCompute);
```

### <a name="get-package-location-on-a-remote-sql-server-compute-context"></a>Ottenere il percorso del pacchetto in un contesto di calcolo di SQL Server remoto

Questo esempio ottiene il percorso del pacchetto **RevoScaleR** nel contesto di calcolo, *sqlServer*.

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```

### <a name="get-locations-for-multiple-packages"></a>Ottenere i percorsi per più pacchetti

Questo esempio ottiene i percorsi per i pacchetti **RevoScaleR** e **lattice** nel contesto di calcolo, *sqlServer*. Per ottenere informazioni più pacchetti, è possibile passare un vettore di stringhe contenente i nomi dei pacchetti.

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Utilizzare una stored procedure per elencare i pacchetti in SQL Server

Eseguire questo comando da Management Studio o un altro strumento che supporta T-SQL, per ottenere un elenco dei pacchetti installati nell'istanza corrente, usando `rxInstalledPackages` in una stored procedure.

```SQL
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Ottenere versioni del pacchetto in un contesto di calcolo remoto

Eseguire questo comando in una console di R per ottenere il numero di build e i numeri di versione per i pacchetti installati nel contesto di calcolo, *sqlServer*.

  ```R
  sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

### <a name="install-a-package-on-sql-server"></a>Installare un pacchetto in SQL Server

Questo esempio installa il pacchetto **ggplot2** e le relative dipendenze nel contesto di calcolo, *sqlServer*.

  ```R
  pkgs <- c("ggplot2")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
  ```

### <a name="remove-a-package-from-sql-server"></a>Rimuovere un pacchetto da SQL Server

Questo esempio rimuove il pacchetto **ggplot2** e le relative dipendenze dal contesto di calcolo, *sqlServer*.

  ```R
  pkgs <- c("ggplot2")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
  ```

### <a name="package-synchronization"></a>Sincronizzazione del pacchetto

Nell'esempio seguente consente di sincronizzare i pacchetti installati nel file system con l'elenco dei pacchetti gestiti nel database. Se mancano alcuni pacchetti, vengono installate nel file system.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

## <a name="next-steps"></a>Passaggi successivi

[Come abilitare o disabilitare la gestione dei pacchetti R](../r/r-package-how-to-enable-or-disable.md)

