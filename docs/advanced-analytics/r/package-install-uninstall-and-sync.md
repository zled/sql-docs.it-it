---
title: Sincronizzazione del pacchetto R per SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5aa19e54917a421567c5ede2013e019de609d8b6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585227"
---
# <a name="r-package-synchronization-for-sql-server"></a>Sincronizzazione del pacchetto R per SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

La versione di RevoScaleR incluso in SQL Server 2017 include la possibilità di sincronizzare le raccolte di pacchetti R tra il file system e l'istanza e database in cui vengono utilizzati i pacchetti.

Questa funzionalità è stata fornita per renderne più semplice eseguire il backup di raccolte di pacchetti R associate ai database di SQL Server. Utilizzando questa funzionalità, un amministratore può ripristinare non solo il database, ma tutti i pacchetti R utilizzati dai data Scientist utilizzo del database.

Questo articolo descrive la funzionalità di sincronizzazione del pacchetto e come utilizzare il [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) funzione per eseguire le attività seguenti:

+ Sincronizzare un elenco di pacchetti per un intero database di SQL Server

+ Sincronizzare pacchetti utilizzati da un singolo utente, o da un gruppo di utenti

+ Se un utente passa a un altro Server SQL, è possibile eseguire un backup del database di lavoro dell'utente e ripristinarlo nel nuovo server e verranno installati i pacchetti per l'utente in file system nel nuovo server, come richiesto da R.

Ad esempio, è possibile utilizzare la sincronizzazione di pacchetto in questi scenari:

+ L'amministratore del database ripristinato un'istanza di SQL Server in un nuovo computer e richiede agli utenti di connettersi dai rispettivi client R ed eseguire `rxSyncPackages` per aggiornare e ripristinare i pacchetti.

+ Si ritiene che un pacchetto R nel file system è danneggiato per eseguire `rxSyncPackages` in SQL Server.

## <a name="requirements"></a>Requisiti

Prima di poter utilizzare la sincronizzazione di pacchetto, è necessario disporre la versione appropriata di Microsoft R o Server di Machine Learning. Questa funzionalità viene fornita in Microsoft R versione 9.1.0 o versione successiva. 

È inoltre necessario abilitare il [funzionalità di gestione pacchetti](r-package-how-to-enable-or-disable.md) sul server.

### <a name="determine-whether-your-server-supports-package-management"></a>Determinare se il server supporta la gestione dei pacchetti

Questa funzionalità è disponibile in SQL Server 2017 CTP 2 o versione successiva.

Per aggiungere questa funzionalità a un'istanza di SQL Server 2016, l'aggiornamento dell'istanza per utilizzare la versione più recente di Microsoft R. Per ulteriori informazioni, vedere [SqlBindR.exe utilizzare per eseguire l'aggiornamento di SQL Server R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="enable-the-package-management-feature"></a>Abilitare la funzionalità di gestione pacchetti

Per utilizzare la sincronizzazione di pacchetto richiede l'abilitazione di nuove funzionalità di gestione di pacchetto nell'istanza di SQL Server e nei singoli database. Per ulteriori informazioni, vedere [abilitare o disabilitare la gestione dei pacchetti per SQL Server](r-package-how-to-enable-or-disable.md).

1. L'amministratore del server abilita la funzionalità per l'istanza di SQL Server.
2. Per ogni database, l'amministratore concede singoli utenti la possibilità di installare o condividere i pacchetti R, usando i ruoli del database.

Quando questa operazione, è possibile utilizzare le funzioni RevoScaleR, ad esempio [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) per installare i pacchetti in un database.  Informazioni sugli utenti e i pacchetti che possono utilizzare viene archiviate nell'istanza di SQL Server. 

Ogni volta che si aggiunge un nuovo pacchetto utilizzando le funzioni di gestione di pacchetti, entrambi i record in SQL Server e il file system vengono aggiornati. Per ripristinare le informazioni sul pacchetto per l'intero database, è possono utilizzare queste informazioni.

### <a name="permissions"></a>Autorizzazioni

+ La persona che esegue la funzione di sincronizzazione del pacchetto deve essere un'entità in cui l'istanza di SQL Server e database che contiene i pacchetti di sicurezza.

+ Il chiamante della funzione deve essere un membro di uno di questi ruoli di gestione pacchetti: **condiviso rpkgs** o **rpkgs privato**.

+ Per sincronizzare i pacchetti contrassegnati come **condivisa**, la persona che esegue la funzione deve disporre dell'appartenenza al **condiviso rpkgs** ruolo e i pacchetti che vengono spostati sia stato installato per un oggetto condiviso libreria di ambito.

+ Per sincronizzare i pacchetti contrassegnati come **privata**, sia il proprietario del pacchetto o l'amministratore deve eseguire la funzione e i pacchetti devono essere privati.

+ Per sincronizzare i pacchetti per conto di altri utenti, il proprietario deve BA membro il **db_owner** ruolo del database.

## <a name="how-package-synchronization-works"></a>Funzionamento della sincronizzazione di pacchetto

Per utilizzare la sincronizzazione di pacchetto, chiamare [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages), che è una nuova funzione negli [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). 

Per ogni chiamata a `rxSyncPackages`, è necessario specificare un'istanza di SQL Server e database. Quindi, elencare i pacchetti per la sincronizzazione oppure specificare l'ambito del pacchetto.

1. Creare il contesto di calcolo di SQL Server utilizzando il `RxInSqlServer` (funzione). Se non si specifica un contesto di calcolo, viene utilizzato il contesto di calcolo corrente.

2. Specificare il nome di un database nell'istanza nel contesto di calcolo specificato. I pacchetti vengono sincronizzati per ogni database.

3. Specificare i pacchetti per la sincronizzazione tramite l'argomento di ambito.

    Se si utilizza **privata** ambito, solo i pacchetti il proprietario specificato vengono sincronizzati. Se si specifica **condivisa** ambito, tutti i pacchetti non privati nel database sono sincronizzati. 
    
    Se si esegue la funzione senza specificando **privata** o **condivisa** ambito, tutti i pacchetti vengono sincronizzati.

4. Se il comando ha esito positivo, vengono aggiunti i pacchetti esistenti nel file system al database, con l'ambito specificato e il proprietario.

    Se il file system è danneggiato, i pacchetti vengono ripristinati in base all'elenco mantenuta nel database.

    Se la funzionalità di gestione del pacchetto non è disponibile nel database di destinazione, viene generato un errore: "la funzionalità di gestione del pacchetto non è abilitata in SQL Server o è troppo vecchia versione"

### <a name="example-1-synchronize-all-package-by-database"></a>Esempio 1. Sincronizzare tutti i pacchetti dal database

In questo esempio ottiene tutti i nuovi pacchetti dal file system locale e installa i pacchetti nel database [TestDB]. Poiché nessun proprietario specifico, l'elenco include tutti i pacchetti che sono stati installati per gli ambiti privati e condivisi.

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

Nell'esempio seguente viene illustrato come sincronizzare solo i pacchetti che sono stati installati per un utente specifico. In questo esempio, l'utente è identificato dal nome di account di accesso SQL, *user1*.

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

## <a name="related-resources"></a>Risorse correlate

[Gestione dei pacchetti R per SQL Server](install-additional-r-packages-on-sql-server.md)
