---
title: Sincronizzazione del pacchetto R per SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 10/02/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a7530d67c2c74b4918228ea91597f1667c0abbd6
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="r-package-synchronization-for-sql-server"></a>Sincronizzazione del pacchetto R per SQL Server

SQL Server 2017 include la possibilità di sincronizzare le raccolte di pacchetti R tra il file system e l'istanza e database in cui vengono utilizzati i pacchetti.
Questa funzionalità è stata fornita per renderne più semplice eseguire il backup di raccolte di pacchetti R associate ai database di SQL Server. Utilizzando questa funzionalità, un amministratore può ripristinare non solo il database, ma tutti i pacchetti R utilizzati dai data Scientist utilizzo del database.

Questo argomento descrive la funzionalità di sincronizzazione del pacchetto e come utilizzare il [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages) funzione per eseguire le attività seguenti:

+ Sincronizzare un elenco di pacchetti per un intero database di SQL Server

+ Sincronizzare pacchetti utilizzati da un singolo utente, o da un gruppo di utenti

+ Se un utente passa a un altro Server SQL, è possibile eseguire un backup del database di lavoro dell'utente e ripristinarlo nel nuovo server e verranno installati i pacchetti per l'utente in file system nel nuovo server, come richiesto da R.

Ad esempio, è possibile utilizzare la sincronizzazione di pacchetto in questi scenari:

+ L'amministratore del database ripristinato un'istanza di SQL Server in un nuovo computer e richiede agli utenti di connettersi dai rispettivi client R ed eseguire `rxSyncPackages` per aggiornare e ripristinare i pacchetti.

+ Si ritiene che un pacchetto R nel file system è danneggiato per eseguire `rxSyncPackages` in SQL Server.

## <a name="requirements"></a>Requisiti

Prima di poter utilizzare la sincronizzazione di pacchetto, è necessario disporre della versione appropriata di Microsoft R e stata abilitata la funzionalità correlate del database.

### <a name="determine-whether-your-server-supports-package-management"></a>Determinare se il server supporta la gestione dei pacchetti

Questa funzionalità è disponibile in SQL Server 2017 CTP 2 o versione successiva.

Poiché questa funzionalità utilizza le funzioni R in Microsoft R versione 9.1.0, è possibile aggiungere questa funzionalità a un'istanza di SQL Server 2016 per l'aggiornamento dell'istanza per utilizzare la versione più recente di Microsoft R. Per ulteriori informazioni, vedere [SqlBindR.exe utilizzare per eseguire l'aggiornamento di SQL Server R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="enable-the-package-management-feature"></a>Abilitare la funzionalità di gestione pacchetti

Per utilizzare la sincronizzazione di pacchetto richiede l'abilitazione di nuove funzionalità di gestione di pacchetti nell'istanza di SQL Server e nei singoli database utilizzati per eseguire le attività di R.

1. L'amministratore del server abilita la funzionalità per l'istanza di SQL Server.
2. Per ogni database, l'amministratore concede agli utenti la possibilità di installare o condividere i pacchetti R.

Quando questa operazione viene eseguita, informazioni sugli utenti e i pacchetti installati vengono archiviate nell'istanza di SQL Server. Queste informazioni possono quindi essere applicate per aggiornare i pacchetti R nel file system.

Ogni volta che si aggiunge un nuovo pacchetto utilizzando le funzioni di gestione di pacchetti, entrambi i record in SQL Server e il file system vengono aggiornati.

> [!NOTE]
> Se si hanno stato installando i pacchetti R modo tradizionale, con strumenti R per installare i pacchetti direttamente nel file system, è possibile utilizzare la sincronizzazione di pacchetto.
### <a name="permissions"></a>Autorizzazioni

+ La persona che esegue la funzione di sincronizzazione del pacchetto deve essere un'entità in cui l'istanza di SQL Server e database che contiene i pacchetti di sicurezza.

+ Il chiamante della funzione deve essere un membro di uno di questi ruoli di gestione pacchetti: **condiviso rpkgs** o **rpkgs privato**.

+ Per sincronizzare i pacchetti contrassegnati come **condivisa**, la persona che esegue la funzione deve disporre dell'appartenenza al **condiviso rpkgs** ruolo e i pacchetti che vengono spostati sia stato installato per un oggetto condiviso libreria di ambito.

+ Per sincronizzare i pacchetti contrassegnati come **privata**, sia il proprietario del pacchetto o l'amministratore deve eseguire la funzione e i pacchetti devono essere privati.

+ Per sincronizzare i pacchetti per conto di altri utenti, il proprietario deve essere un membro del **db_owner** ruolo del database.

## <a name="how-package-synchronization-works"></a>Funzionamento della sincronizzazione di pacchetto

Per utilizzare la sincronizzazione di pacchetto, chiamare [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages), che è una nuova funzione negli [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler). È possibile chiamare questa funzione da SQL Server tramite sp_execute_external_script oppure è possibile eseguirlo da un client remoto di R e specificare contesto di calcolo di SQL Server. 

Poiché i pacchetti vengono gestiti a livello di database, per ogni chiamata a `rxSyncPackages`, è necessario specificare un'istanza di SQL Server e database ed elencare i pacchetti o specificare l'ambito del pacchetto.

1. Creare il contesto di calcolo di SQL Server utilizzando il `RxInSqlServer` (funzione). Se non si specifica un contesto di calcolo, viene utilizzato il contesto di calcolo corrente.

2. Specificare il nome di un database nell'istanza nel contesto di calcolo specificato. Per ogni database vengono gestiti i pacchetti.

3. Elencare i pacchetti da sincronizzare.

4.  Facoltativamente, utilizzare il *ambito* argomento per indicare se si esegue la sincronizzazione di pacchetti per un singolo utente o per un gruppo di utenti. Se si esegue la funzione senza specificando **privata** o **condivisa** definire l'ambito, l'intero set di pacchetti disponibili per tutti gli ambiti e gli utenti verranno copiati.

Se il comando viene eseguito correttamente, i pacchetti esistenti nel file system vengono aggiunti al database, con l'ambito specificato e il proprietario. Se il file system è danneggiato, i pacchetti vengono ripristinati in base all'elenco mantenuta nel database.

### <a name="example-1-synchronize-all-package-by-database"></a>Esempio 1. Sincronizzare tutti i pacchetti dal database

In questo esempio ottiene tutti i pacchetti installati nel database [TestDB]. Poiché nessun proprietario specifico, l'elenco include tutti i pacchetti che sono stati installati per gli ambiti privati e condivisi.

```R
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

### <a name="example-2-restrict-synchronized-packages-by-scope"></a>Esempio 2. Limitare i pacchetti sincronizzati dall'ambito

Negli esempi seguenti sincronizzare solo i pacchetti nell'ambito specificato.

```R
#Shared scope
rxSyncPackages(computeContext=computeContext, scope="shared", verbose=TRUE)

#Private scope
rxSyncPackages(computeContext=computeContext, scope="private", verbose=TRUE)
```

### <a name="example-3-restrict-synchronized-packages-by-owner"></a>Esempio 3. Limitare i pacchetti sincronizzati dal proprietario

Nell'esempio seguente viene illustrato come ottenere solo i pacchetti che sono stati installati per un utente specifico. In questo esempio, l'utente è identificato dal nome di account di accesso SQL, *user1*.

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

### <a name="example-4-restrict-synchronized-packages-by-owner"></a>Esempio 4. Limitare i pacchetti sincronizzati dal proprietario

Nell'esempio seguente consente di sincronizzare i pacchetti installati nel file system con l'elenco dei pacchetti gestiti nel database. Se qualsiasi pacchetto è manca, verrà installato nel file system.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

## <a name="related-resources"></a>Risorse correlate

[Gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md)
