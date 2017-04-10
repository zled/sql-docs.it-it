---
title: "Gestione dei pacchetti R per SQL Server R Services | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 7
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# Gestione dei pacchetti R per SQL Server R Services
Per semplificare la gestione dei pacchetti R eseguiti su un'istanza di SQL Server, il pacchetto **RevoScaleR** include ora funzioni per supportare l'installazione e la gestione dei pacchetti R. 

Questa nuova funzionalità supporta diversi scenari:

- Un analista di dati può installare i pacchetti R necessari in SQL Server senza disporre dell'accesso amministrativo al computer con SQL Server. I pacchetti vengono installati per singolo database.
- È facile condividere pacchetti con altri utenti. Basta definire un repository di pacchetti locale e chiedere a ogni analista di dati di installare i pacchetti nei singoli database.
- L'amministratore del database non deve saper eseguire i comandi R né comprendere le dipendenze dei pacchetti. L'amministratore del database usa i ruoli di database per controllare gli utenti di SQL Server autorizzati a installare, disinstallare o usare i pacchetti.
 
**Funzionamento**

* L'amministratore del database è responsabile della configurazione dei ruoli e dell'aggiunta di utenti ai ruoli, per controllare gli utenti che dispongono dell'autorizzazione per aggiungere o rimuovere pacchetti R nell'ambiente di SQL Server.
* Se si dispone dell'autorizzazione per installare i pacchetti, eseguire una delle funzioni di gestione dei pacchetti del codice R e specificare il contesto di calcolo in cui i pacchetti devono essere aggiunti o rimossi. Il contesto di calcolo può essere il computer locale o un database nell'istanza di SQL Server. 
* Se viene eseguita la chiamata per installare i pacchetti in SQL Server, le credenziali determinano se l'operazione può essere completata sul server. 
- Le funzioni per l'installazione dei pacchetti verificano se sono presenti dipendenze e se eventuali pacchetti correlati possono essere installati in SQL Server, in modo analogo all'installazione di pacchetti R nel contesto di calcolo locale.
- La funzione per la disinstallazione dei pacchetti calcola inoltre le dipendenze e verifica che i pacchetti che non sono più usati da altri pacchetti in SQL Server vengano rimossi, per liberare risorse.
- Ogni analista di dati può installare pacchetti privati che non sono visibili ad altri utenti, specificando una sandbox isolata per gestire i propri pacchetti R.
-  Poiché l'ambito dei pacchetti può essere limitato a un database e ogni utente ottiene una sandbox per pacchetti isolata in ogni database, è più facile installare e usare versioni diverse dello stesso pacchetto R. 

> [!NOTE]
> Attualmente questa funzionalità è stata rilasciata solo per l'uso con [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]. 

## <a name="database-roles-and-database-scoping"></a>Definizione dell'ambito del database e dei ruoli di database

Le nuove funzioni di gestione dei pacchetti forniscono due ambiti per l'installazione e l'uso di pacchetti in SQL Server in uno specifico database:

- **Ambito condiviso**

  In un *ambito condiviso* gli utenti che dispongono dell'autorizzazione per il ruolo di ambito condiviso (**rpkgs-shared**) possono installare e disinstallare i pacchetti in un database specificato. Un pacchetto installato in una libreria di ambito condiviso può essere usato da altri utenti del database in SQL Server, purché tali utenti siano autorizzati a usare pacchetti R installati. 

- **Ambito privato** 

  In un *ambito privato* gli utenti a cui è stata concessa l'appartenenza al ruolo di ambito privato (**rpkgs-private**) possono installare o disinstallare i pacchetti in un percorso di libreria privato definito per singolo utente. Pertanto, i pacchetti installati nell'ambito privato possono essere usati solo dall'utente che li ha installati. In altre parole, un utente di SQL Server non può usare pacchetti privati che sono stati installati da un altro utente. 

Questi modelli per ambito *condiviso* e *privato* possono essere combinati per sviluppare sistemi di sicurezza personalizzati per distribuire e gestire pacchetti in SQL Server. 

Ad esempio, in un ambito condiviso, al responsabile di un gruppo di analisti di dati può essere concessa l'autorizzazione per installare i pacchetti e tali pacchetti possono quindi essere usati da tutti gli altri utenti o analisti di dati nella stessa istanza di SQL Server. 

Un altro scenario può richiedere maggiore isolamento tra gli utenti o l'uso di diverse versioni dei pacchetti. In tal caso, è possibile usare l'ambito privato per concedere autorizzazioni individuali agli analisti di dati, che saranno responsabili dell'installazione e dell'uso dei soli pacchetti di cui hanno bisogno. Poiché l'installazione dei pacchetti viene eseguita per singolo utente, i pacchetti installati da un utente non influiscono sul lavoro degli altri utenti dello stesso database di SQL Server. 

### <a name="database-roles-for-package-management"></a>Ruoli di database per la gestione dei pacchetti

I nuovi ruoli di database seguenti garantiscono la sicurezza dell'installazione e della gestione dei pacchetti per SQL R Services: 

- **rpkgs-users** consente agli utenti di usare i pacchetti condivisi installati dai membri del ruolo **rpkgs-shared**.

- **rpkgs-private** fornisce l'accesso ai pacchetti condivisi con le stesse autorizzazioni del ruolo **rpkgs-users**. I membri di questo ruolo possono anche installare, rimuovere e usare pacchetti con ambito privato.

-  **rpkgs-shared** fornisce le stesse autorizzazioni del ruolo **rpkgs-private**. Gli utenti membri di questo ruolo possono anche installare o rimuovere i pacchetti condivisi. 
 
- **db_owner** ha le stesse autorizzazioni del ruolo **rpkgs-shared**. Può inoltre concedere agli utenti il diritto di installare o rimuovere pacchetti sia condivisi che privati.



## <a name="new-package-management-functions"></a>Nuove funzioni di gestione dei pacchetti


+ `rxInstalledPackages`: trova informazioni sui pacchetti installati nel contesto di calcolo specificato.

+ `rxInstallPackages`: installa i pacchetti in un contesto di calcolo, da un repository specificato o leggendo i pacchetti compressi salvati in locale.

+ `rxRemovePackages`: rimuove i pacchetti installati da un contesto di calcolo.

+ `rxFindPackage`: ottiene il percorso per uno o più pacchetti nel contesto di calcolo specificato.

+ `rxSqlLibPaths`: ottiene il percorso di ricerca dei pacchetti negli alberi delle librerie durante l'esecuzione all'interno di SQL Server.

## <a name="examples"></a>Esempi

### <a name="get-package-location-on-sql-server-compute-context"></a>Ottenere il percorso del pacchetto nel contesto di calcolo di SQL Server

Questo esempio ottiene il percorso del pacchetto **RevoScaleR** nel contesto di calcolo, *sqlServer*.

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```
  
  ### <a name="get-locations-for-multiple-packages"></a>Ottenere i percorsi per più pacchetti

Questo esempio ottiene i percorsi per i pacchetti **RevoScaleR** e **lattice** nel contesto di calcolo, *sqlServer*. Quando si cercano le informazioni su più pacchetti, passare un vettore di stringhe contenente i nomi dei pacchetti.

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```



### <a name="list-packages-in-specified-compute-context"></a>Elencare i pacchetti nel contesto di calcolo specificato

Questo esempio elenca e quindi visualizza nella console tutti i pacchetti installati nel contesto di calcolo, *sqlServer*.

  ```R
  myPackages <- rxInstalledPackages(computeContext = sqlServer) 
  myPackages
  ```

### <a name="get-package-versions"></a>Ottenere le versioni di un pacchetto

Questo esempio ottiene il numero di build e i numeri di versione per un pacchetto installato nel contesto di calcolo, *sqlServer*.

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

## <a name="see-also"></a>Vedere anche

[Come abilitare o disabilitare la gestione dei pacchetti R](../../advanced-analytics/r-services/how-to-enable-or-disable-r-package-management.md)