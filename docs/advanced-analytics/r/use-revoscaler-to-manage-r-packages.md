---
title: Come utilizzare le funzioni RevoScaleR per trovare o installare R pacchetti in SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: 65bfbe18ddc6a39bb1d27bf4babab1d4dd3cf0de
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Come utilizzare le funzioni RevoScaleR per trovare o installare pacchetti R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Versione di Microsoft R Server 9.0.1 introdotte nuove funzioni RevoScaleR che supportano l'utilizzo dei pacchetti installati in un contesto di calcolo di SQL Server. Queste nuove funzioni semplificano un esperto di dati eseguire il codice R e installare i pacchetti in SQL Server senza accesso diretto al server.

## <a name="how-does-it-work"></a>Come funziona

Se si dispone di R Server 9.0.1 o versioni successive, è possibile utilizzare il [rxInstallPackages](https://docs.microsoft.com/en-us/machine-learning-server/r-reference/revoscaler/rxinstallpackages) funzione da un client remoto R per installare i pacchetti in un contesto di calcolo di SQL Server. Per utilizzare questa opzione, è necessario aver attivato la gestione di pacchetti nel server e database. Questa funzionalità richiede anche una versione equivalente di R Services o i servizi di Machine Learning necessario installare nel server.

La nuova versione di RevoScaleR include anche queste funzioni: 

+ Il [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) funzione Ottiene il percorso di uno o più pacchetti nel contesto di calcolo specificato.

    È possibile utilizzare una combinazione di utenti e ambito per trovare i pacchetti o aggiungere pacchetti a un database specifico:

+ Il [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) funzione Ottiene un elenco di pacchetti installati nel contesto di calcolo specificato.

+ Il [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) funzione Installa i pacchetti in un contesto di calcolo, da un repository specifico o leggendo salvato localmente compresso pacchetti.

    Questa funzione controlla le dipendenze e assicura che tutti i pacchetti correlati è possibile installare SQL Server, esattamente come l'installazione del pacchetto R nel contesto di calcolo locale.

+ Il [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) funzione rimuove i pacchetti da un contesto di calcolo specificato.

    Inoltre, consente di calcolare le dipendenze e assicura che vengano rimossi i pacchetti che non vengono più utilizzati da altri pacchetti in SQL Server, per liberare risorse.

+ Utilizzare il [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) funzione per copiare le informazioni su una raccolta di pacchetti tra il file system e un database, per il contesto di calcolo specificato.

+ Utilizzare il [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) contesto di calcolo di funzione per determinare il percorso della libreria di istanza in un Server SQL.

**Si applica a:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]. Supportato anche nelle [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] con un aggiornamento a R Server 9.0 o versioni successive. Altre limitazioni.

## <a name="requirements"></a>Requisiti

+ Per eseguire queste funzioni, è necessario disporre dell'autorizzazione per connettersi al server e un database e per eseguire i comandi di R.

+ Quando si utilizzano queste funzioni da un client remoto di R, è necessario creare un oggetto di contesto di calcolo in primo luogo, utilizzando il [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) (funzione). Successivamente, per ogni funzione di gestione di pacchetto in uso, passare il contesto di calcolo come argomento.

+ Se non si specifica un nome utente e una password quando si crea il contesto di calcolo, viene utilizzata l'identità dell'utente che esegue il codice R.

+ È anche possibile eseguire le funzioni di gestione di pacchetto all'interno di `sp_execute_external_script`. Quando si esegue questa operazione, la funzione viene eseguita utilizzando il contesto di sicurezza del chiamante stored procedure.

+ Pacchetti in **ambito condiviso** possono essere installate dagli utenti che appartengono al `rpkgs-shared` ruolo in un database specificato. Tutti gli utenti in questo ruolo è possono disinstallare pacchetti condivisi.

+ Pacchetti in **ambito privato** possono essere installate da qualsiasi utente appartenente al `rpkgs-private` ruolo in un database. Tuttavia, gli utenti possono vedere e disinstallare solo i propri pacchetti.

+ I proprietari del database possono utilizzare i pacchetti condivisi o privati.

## <a name="package-installation-from-machine-learning-server-or-remote-r-client"></a>Installazione del pacchetto da Machine Learning Server o client remoti di R

Prima di iniziare, verificare che siano soddisfatte queste condizioni:

+ Il client ha RevoScale 9.0.1 o versione successiva.
+ Una versione equivalente di RevoScaleR installata nell'istanza di SQL Server.
+ Il [funzionalità di gestione pacchetti](..\r\r-package-how-to-enable-or-disable.md) è stata abilitata nell'istanza.
+ Si è un membro di un ruolo del database che consente di installare i pacchetti nel database e istanza specificata. In futuro, i ruoli supporterà l'installazione di pacchetti a uno un percorso condiviso o privato. Per il momento, è possibile installare pacchetti, se dispone di un database.

1. Dalla riga di comando R, definire una stringa di connessione per l'istanza e database.
2. Utilizzare il [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) costruttore per definire un contesto di calcolo di SQL Server, usando la stringa di connessione.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Creare un elenco dei pacchetti che si desidera installare e salvare l'elenco in una variabile di stringa.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Chiamare [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) e passare il contesto di calcolo e la variabile di stringa che contiene i nomi dei pacchetti.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Se sono necessari i pacchetti dipendenti, essi vengono installati anche, presupponendo che una connessione internet sia disponibile nel client.
    
    I pacchetti vengono installati utilizzando le credenziali dell'utente che effettua la connessione, nell'ambito predefinito per tale utente.

## <a name="examples"></a>Esempi

In questa sezione vengono forniti esempi di come utilizzare queste funzioni da un client remoto durante la connessione a un database come contesto di calcolo o un'istanza di SQL Server.

Per tutti gli esempi, è necessario fornire una stringa di connessione o un contesto di calcolo, che richiede una stringa di connessione. In questo esempio viene illustrato un modo per creare un contesto di calcolo per SQL Server:

```R
instance_name <- "Machine name/Instance name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

A seconda di dove si trova il server e il modello di sicurezza, potrebbe essere necessario fornire una specifica del dominio e la subnet nella stringa di connessione oppure utilizzare un account di accesso SQL. Esempio:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"


### Get package path on a remote SQL Server compute context

This example gets the path for the **RevoScaleR** package on the compute context, `sqlcc`.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Risultati**

"C: o programma file/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/libreria/RevoScaleR"

> [!TIP]
> Se è stata abilitata l'opzione visualizzare l'output di console SQL, è possibile ottenere i messaggi di stato dalla funzione che precede il `print` istruzione. Dopo aver completato il test del codice, impostare `consoleOutput` su FALSE nel costruttore di contesto di calcolo per eliminare i messaggi.

### <a name="get-locations-for-multiple-packages"></a>Ottenere i percorsi per più pacchetti

Nell'esempio seguente ottiene i percorsi per il **RevoScaleR** e **reticolato** pacchetti, nel contesto di calcolo, `sqlcc`. Per ottenere informazioni più pacchetti, è possibile passare un vettore di stringhe contenente i nomi dei pacchetti.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Ottenere versioni del pacchetto in un contesto di calcolo remoto

Eseguire questo comando in una console di R per ottenere il numero di build e i numeri di versione per i pacchetti installati nel contesto di calcolo, *sqlServer*.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**Risultati**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>Installare un pacchetto in SQL Server

Questo esempio viene installato il **previsione** pacchetto e le relative dipendenze nel contesto di calcolo.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Rimuovere un pacchetto da SQL Server

Questo esempio viene rimossa la **previsione** pacchetto e le relative dipendenze nel contesto di calcolo.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
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
