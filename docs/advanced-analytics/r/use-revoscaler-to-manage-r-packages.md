---
title: Come utilizzare le funzioni RevoScaleR per trovare o installare R pacchetti in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 6b8b3e3f50483d51b5e8f7533055d982b6bc6ab3
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Come utilizzare le funzioni RevoScaleR per trovare o installare pacchetti R in SQL Server

Versione di Microsoft R Server 9.0.1 introdotte nuove funzioni RevoScaleR che supportano l'utilizzo dei pacchetti installati in un contesto di calcolo di SQL Server. Queste nuove funzioni semplificano un esperto di dati eseguire il codice R in SQL Server senza accesso diretto al server.

Ogni esperto di dati è possibile installare pacchetti privati che non sono visibili ad altri utenti. Poiché i pacchetti possono essere limitati a un database e ogni utente disponga di una sandbox pacchetto isolato in ogni database, è più facile da installare versioni diverse dello stesso pacchetto R.

Se si esegue la migrazione di database di lavoro in un nuovo server, è inoltre possibile utilizzare la funzione di sincronizzazione del pacchetto per leggere un elenco di tutti i pacchetti e installarli in un database nel nuovo server.

In questo articolo vengono descritte queste funzioni e vengono forniti esempi dell'utilizzo della funzione.

## <a name="requirements"></a>Requisiti

+ Per eseguire queste funzioni, è necessario disporre dell'autorizzazione per eseguire i comandi di R nell'istanza.

+ Se non si specifica un nome utente e una password quando si crea il contesto di calcolo, viene utilizzata l'identità dell'utente che esegue il codice R.

+ Quando si utilizzano queste funzioni da un client remoto di R, è necessario creare un oggetto di contesto di calcolo in primo luogo, utilizzando la funzione RxInSQLServer. Successivamente, per ogni funzione di gestione di pacchetto in uso, passare il contesto di calcolo come argomento.

+ È possibile eseguire le funzioni di gestione di pacchetti tramite `sp_execute_external_script`. Quando si esegue questa operazione, la funzione viene eseguita utilizzando il contesto di sicurezza del chiamante stored procedure.

## <a name="list-of-package-management-functions"></a>Elenco di funzioni di gestione pacchetti

Le funzioni di gestione pacchetti seguenti sono disponibili in RevoScaleR, per l'installazione e la rimozione dei pacchetti in un contesto di calcolo specificata:

+ [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): trovare informazioni sui pacchetti installati nel contesto di calcolo specificato.

+ [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): installare i pacchetti in un contesto di calcolo, da un repository specifico o leggendo salvato localmente compressi pacchetti.

+ [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): rimuovere i pacchetti installati da un contesto di calcolo.

+ [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): ottenere il percorso di uno o più pacchetti nel contesto di calcolo specificato.

+ [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): copia di una libreria di pacchetti tra il file system e i database nei contesti di calcolo specificato.

+ [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): ottenere il percorso di ricerca per gli alberi di libreria per i pacchetti durante l'esecuzione all'interno del Server SQL.

Questi pacchetti sono inclusi per impostazione predefinita in SQL Server 2017. Per informazioni su queste funzioni, vedere le pagine di riferimento di funzione RevoScaleR: (https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

> [!NOTE]
> Funzioni di R per la gestione dei pacchetti sono disponibili a partire da Microsoft R Server 9.0.1. Se è possibile trovare le funzioni in RevoScaleR, è probabilmente necessario eseguire l'aggiornamento alla versione più recente. 
## <a name="examples"></a>Esempi

In questa sezione contiene esempi di come utilizzare le funzioni di gestione di pacchetto con un database o istanza di SQL Server. 

+ Le funzioni per l'installazione dei pacchetti verificano se sono presenti dipendenze e se eventuali pacchetti correlati possono essere installati in SQL Server, in modo analogo all'installazione di pacchetti R nel contesto di calcolo locale.

+ La funzione che _Disinstalla_ pacchetti anche calcola le dipendenze e assicura che vengano rimossi i pacchetti che non vengono più utilizzati da altri pacchetti in SQL Server, per liberare risorse.

+ È possibile utilizzare una combinazione di utenti e ambito per trovare i pacchetti o aggiungere pacchetti a un database specifico:

    + Pacchetti in **ambito condiviso** possono essere installate dagli utenti che appartengono al `rpkgs-shared` ruolo in un database specificato. Tutti gli utenti in questo ruolo è possono disinstallare pacchetti condivisi.
    + Pacchetti in **ambito privato** possono essere installate da qualsiasi utente appartenente al `rpkgs-private` ruolo in un database. Tuttavia, gli utenti possono vedere e disinstallare solo i propri pacchetti.
    + I proprietari del database possono utilizzare i pacchetti condivisi o privati.

**Dal codice R**

Se si dispone dell'autorizzazione per installare i pacchetti, eseguire un pacchetto di funzioni di gestione dal client di R e specificare il contesto di calcolo in pacchetti devono essere aggiunti o rimossi.  Il contesto di calcolo può essere il computer locale o un database nell'istanza di SQL Server. Le credenziali di determinano se è possibile completare l'operazione nel server.

**Da Transact-SQL**

Per eseguire funzioni di gestione dei pacchetti da una stored procedure, eseguirne il wrapping in una chiamata a `sp_execute_external_script`.

### <a name="get-list-of-packages-in-a-sql-server-compute-context"></a>Ottenere l'elenco dei pacchetti in un contesto di calcolo di SQL Server

Questo esempio viene verificata per i pacchetti che sono stati installati nell'istanza `myServer`, nel database `TestDB`. Gestione dei pacchetti di ambito è un database specifico e un utente. Se l'utente non è specificato, viene utilizzato l'utente che esegue la chiamata di contesto di calcolo. Per ulteriori informazioni, vedere [Scoping dei pacchetti dal ruolo](#bkmk_scope).

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;");
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerCompute);
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Ottenere il percorso di pacchetto in un contesto di calcolo di SQL Server remoto

Questo esempio ottiene il percorso del pacchetto **RevoScaleR** nel contesto di calcolo, *sqlServer*.

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```

### <a name="get-locations-for-multiple-packages"></a>Ottenere i percorsi per più pacchetti

Questo esempio ottiene i percorsi per i pacchetti **RevoScaleR** e **lattice** nel contesto di calcolo, *sqlServer*. Per ottenere informazioni più pacchetti, è possibile passare un vettore di stringhe contenente i nomi dei pacchetti.

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```


### <a name="get-package-versions-on-a-remote-compute-context"></a>Ottenere versioni del pacchetto in un contesto di calcolo remoto

Eseguire questo comando in una console di R per ottenere il numero di build e i numeri di versione per i pacchetti installati nel contesto di calcolo, *sqlServer*.

  ```R
  sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

### <a name="install-a-package-on-sql-server"></a>Installare un pacchetto in SQL Server

Questo esempio viene installato il **previsione** pacchetto e le relative dipendenze nel contesto di calcolo *sqlServer*.

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

### <a name="synchronize-packages-between-database-and-file-system"></a>Sincronizzare i pacchetti tra database e file system

L'esempio seguente verifica il database **TestDB**e determina se tutti i pacchetti vengono installati nel file system. Se mancano alcuni pacchetti, vengono installate nel file system.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Sincronizzazione del pacchetto funziona su una per ogni database e ogni singolo utente. Per ulteriori informazioni, vedere [sincronizzazione del pacchetto R per SQL Server](../r/package-install-uninstall-and-sync.md).

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

Il `rxSqlLibPaths` funzione può essere utilizzata per determinare la libreria active usata da servizi di SQL Server Machine Learning. Questo script può restituire solo il percorso di libreria per il server corrente. 

```SQL
declare @instance_name nvarchar(100) = @@SERVERNAME, @database_name nvarchar(128) = db_name();
exec sp_execute_external_script 
  @language = N'R',
  @script = N'
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    .libPaths(rxSqlLibPaths(connStr));
    print(.libPaths());
  ', 
  @input_data_1 = N'', 
  @params = N'@instance_name nvarchar(100), @database_name nvarchar(128)',
  @instance_name = @instance_name, 
  @database_name = @database_name;
```
