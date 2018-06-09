---
title: Come utilizzare le funzioni RevoScaleR per trovare o installare R pacchetti in SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d92b3e993968ce48d7489b0c17d6bdba005809a3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707529"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Come utilizzare le funzioni RevoScaleR per trovare o installare pacchetti R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR 9.0.1 e successivamente inclusione funzioni per la gestione dei pacchetti R un contesto di calcolo di SQL Server. Queste funzioni sono utilizzabile da remoti, utenti non amministratori per installare i pacchetti in SQL Server senza accesso diretto al server.

Servizi di SQL Server 2017 Machine Learning include già una versione più recente di RevoScaleR. I clienti di SQL Server 2016 R Services è necessario eseguire una [aggiornamento del componente](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) per ottenere le funzioni di gestione del pacchetto RevoScaleR. Per istruzioni su come recuperare pacchetto versione e il contenuto, vedere [ottenere informazioni sul pacchetto](determine-which-packages-are-installed-on-sql-server.md).

## <a name="revoscaler-functions-for-package-management"></a>Funzioni RevoScaleR per la gestione dei pacchetti

Nella tabella seguente vengono descritte le funzioni utilizzate per la gestione e installazione del pacchetto R.

| Funzione | Description |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Determinare il percorso della libreria di istanza nel Server SQL remoto. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) | Ottiene il percorso per uno o più pacchetti nel Server SQL remoto. |
| [rxInstallPackages](https://docs.microsoft.com/en-us/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Chiamare questa funzione da un client remoto R per installare i pacchetti in un contesto di calcolo di SQL Server, da un repository specifico o leggendo salvati in locale i pacchetti compressi. Questa funzione controlla le dipendenze e assicura che tutti i pacchetti correlati è possibile installare SQL Server, esattamente come l'installazione del pacchetto R nel contesto di calcolo locale. Per utilizzare questa opzione, è necessario aver attivato la gestione di pacchetti nel server e database. Ambienti client e server devono avere la stessa versione di RevoScaleR. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) | Ottiene un elenco di pacchetti installati nel contesto di calcolo specificato. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Copiare informazioni su una libreria di pacchetti tra il file system e un database, per il contesto di calcolo specificato. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Rimuove i pacchetti da un contesto di calcolo specificato. Inoltre, consente di calcolare le dipendenze e assicura che vengano rimossi i pacchetti che non vengono più utilizzati da altri pacchetti in SQL Server, per liberare risorse. |

## <a name="prerequisites"></a>Prerequisiti

+ [Abilitare la gestione remota di pacchetto R in SQL Server](r-package-how-to-enable-or-disable.md)

+ Versioni di RevoScaleR devono essere gli stessi in ambienti client e server. Per altre informazioni, vedere [ottenere informazioni sul pacchetto](determine-which-packages-are-installed-on-sql-server.md).

+ Autorizzazione per connettersi al server e un database ed eseguire i comandi di R. È necessario essere un membro di un ruolo del database che consente di installare i pacchetti nel database e istanza specificata.

+ Pacchetti in **ambito condiviso** possono essere installate dagli utenti che appartengono al `rpkgs-shared` ruolo in un database specificato. Tutti gli utenti in questo ruolo è possono disinstallare pacchetti condivisi.

+ Pacchetti in **ambito privato** possono essere installate da qualsiasi utente appartenente al `rpkgs-private` ruolo in un database. Tuttavia, gli utenti possono vedere e disinstallare solo i propri pacchetti.

+ I proprietari del database possono utilizzare i pacchetti condivisi o privati.

## <a name="client-connections"></a>Connessioni client

Una workstation client può essere [Client di Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) o una [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (gli esperti di dati spesso usano l'edizione developer gratuito) nella stessa rete.

Quando si chiama le funzioni di gestione di pacchetti da un client remoto di R, è necessario creare un oggetto di contesto di calcolo in primo luogo, usando il [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) (funzione). Successivamente, per ogni funzione di gestione di pacchetto in uso, passare il contesto di calcolo come argomento.

Identità dell'utente viene in genere specificato quando si imposta il contesto di calcolo. Se non si specifica un nome utente e una password quando si crea il contesto di calcolo, viene utilizzata l'identità dell'utente che esegue il codice R.

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

## <a name="call-package-management-functions-in-stored-procedures"></a>Chiamare le funzioni di gestione di pacchetti nelle stored procedure

Si può eseguire funzioni di gestione di pacchetto all'interno di `sp_execute_external_script`. Quando si esegue questa operazione, la funzione viene eseguita utilizzando il contesto di sicurezza del chiamante stored procedure.

## <a name="examples"></a>Esempi

In questa sezione vengono forniti esempi di come utilizzare queste funzioni da un client remoto durante la connessione a un database come contesto di calcolo o un'istanza di SQL Server.

Per tutti gli esempi, è necessario fornire una stringa di connessione o un contesto di calcolo, che richiede una stringa di connessione. In questo esempio viene illustrato un modo per creare un contesto di calcolo per SQL Server:

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

A seconda di dove si trova il server e il modello di sicurezza, potrebbe essere necessario fornire una specifica del dominio e la subnet nella stringa di connessione oppure utilizzare un account di accesso SQL. Esempio:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Ottenere il percorso di pacchetto in un contesto di calcolo di SQL Server remoto

Questo esempio mostra come ottenere il percorso per il **RevoScaleR** pacchetto nel contesto di calcolo, `sqlcc`.

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

## <a name="see-also"></a>Vedere anche

+ [Abilitare la gestione remota dei pacchetti R](r-package-how-to-enable-or-disable.md)
+ [Sincronizzare i pacchetti R](package-install-uninstall-and-sync.md)
+ [Suggerimenti per l'installazione di pacchetti R](packages-installed-in-user-libraries.md)
+ [Pacchetti predefiniti](installing-and-managing-r-packages.md)