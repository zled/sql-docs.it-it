---
title: Pacchetto di installazione, disinstallazione e la sincronizzazione | Documenti Microsoft
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 959282395d178a090a3d447769ced4dca8882f89
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---

# <a name="r-package-synchronization-for-sql-server"></a>Sincronizzazione del pacchetto R per SQL Server

SQL Server 2017 CTP 2.0 include una nuova funzione per la sincronizzazione dei pacchetti di R, per il supporto di backup e ripristino di raccolte di pacchetti R associate ai database di SQL Server. Questa funzionalità consente di verificare che non vanno perse e che possono essere facilmente ripristinati set complessi di pacchetti R creati dagli utenti.  

Questo argomento viene descritto il funzionamento della funzionalità di sincronizzazione del pacchetto e come utilizzare il `rxSyncPackages()` funzione per eseguire le attività seguenti:

+  Sincronizzare un elenco di pacchetti per un intero database di SQL Server
+  Sincronizza pacchetti utilizzati da un singolo utente, o da un gruppo di utenti

> [!NOTE]
> Questa funzione viene fornita come parte del software provvisorio e è soggette a modifiche prima della versione finale.

## <a name="what-is-package-synchronization"></a>Che cos'è la sincronizzazione di pacchetto 

Sincronizzazione del pacchetto è contesti di calcolo di una nuova funzionalità che funziona in modo specifico con SQL Server. È progettato per ottenere un elenco di pacchetti R installati in un database specifico, per un particolare utente o gruppo, e assicurarsi che i pacchetti elencati nel sistema corrisponde file quelli presenti nel database. 

Ciò è utile se è necessario spostare un database utente e spostare i pacchetti insieme al database. Eseguire il backup e il ripristino di un database di SQL Server utilizzato per i processi R, è possibile utilizzare anche la sincronizzazione di pacchetto.

Sincronizzazione del pacchetto viene utilizzata una funzione nuova, `rxSyncPackages()`. Per sincronizzare l'elenco dei pacchetti, aprire un prompt dei comandi di R, passare il contesto di calcolo che definisce l'istanza e database che si desidera utilizzare e quindi specificare un ambito del pacchetto o un nome utente o il proprietario. 

### <a name="how-packages-are-managed-in-r-and-sql-server"></a>Come vengono gestiti i pacchetti R e SQL Server

In genere, quando si eseguono gli script R mediante strumenti standard di R, pacchetti R installati nel file system. Se più utenti utilizzano R nello stesso computer, potrebbero esserci più copie degli stessi pacchetti, in cartelle diverse o in librerie utente diverso.

Tuttavia, per utilizzare un pacchetto R da SQL Server, il pacchetto deve essere installato nella libreria R predefinito che viene associata all'istanza. Un computer del server potrebbe ospitare più istanze di SQL Server con R abilitato e in questo caso, ogni istanza può includere un set separato di pacchetti R. 

L'amministratore del database è responsabile per l'installazione dei pacchetti nell'istanza. Tuttavia, con le librerie di gestione del pacchetto, l'amministratore può delegare questa responsabilità agli utenti. 

+ Per ogni database, l'amministratore può concedere agli utenti la possibilità di installare liberamente i pacchetti R che hanno bisogno. Questo meccanismo garantisce che più utenti possono installare versioni diverse di pacchetti R senza provocare conflitti per gli altri utenti del computer SQL Server. Singoli utenti possono installare i pacchetti per uso personale, utilizzando un percorso del file system contrassegnato come **privata**, se appartengono al ruolo del database **rpkgs privato**.

+ L'amministratore può configurare un gruppo di utenti di pacchetto in un database e installare i pacchetti che sono condivisi da tutti gli utenti del gruppo. I pacchetti possono essere condivise tra i membri del ruolo del database **condiviso rpkgs**. Tali utenti possono anche installare pacchetti ai percorsi di ambito privato. 

### <a name="goal-of-package-synchronization"></a>Obiettivo di sincronizzazione del pacchetto

Se un database in un server viene perso o deve essere spostato, mediante la sincronizzazione di pacchetto, è possibile ripristinare i set di pacchetti specifici per un database, l'utente o gruppo. 

Le informazioni sugli utenti e i pacchetti installati viene archiviate nell'istanza di SQL Server e viene utilizzate per aggiornare i pacchetti nel file system. Ogni volta che si aggiunge un nuovo pacchetto utilizzando le funzioni di gestione di pacchetti, entrambi i record in SQL Server e il file system vengono aggiornati. Pertanto, se un utente passa a un altro Server SQL, è possibile eseguire un backup del database di lavoro dell'utente e ripristinarlo nel nuovo server, e i pacchetti per l'utente verranno installati nel file system nel nuovo server, come richiesto da R.


### <a name="supported-versions"></a>Versioni supportate

Questa funzione è inclusa in SQL Server 2017 CTP 2.0.

Poiché questa funzione è parte di Microsoft R versione 9.1.0, è possibile aggiungere questa funzionalità a un'istanza di SQL Server 2016 per l'aggiornamento dell'istanza per utilizzare la versione più recente di Microsoft R. Per ulteriori informazioni, vedere [SqlBindR.exe utilizzare per eseguire l'aggiornamento di SQL Server R Services](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="to-synchronize-packages"></a>Per sincronizzare i pacchetti

Chiamare `rxSyncPackages` dopo il ripristino di un'istanza di SQL Server in un nuovo computer, o se creare un pacchetto nel file system un R sembrano danneggiati.

Se il comando viene eseguito correttamente, vengono aggiunti i pacchetti esistenti nel file system nel database, l'ambito e proprietario specificato. Se il file system è danneggiato, i pacchetti sono restred in base all'elenco mantenuta nel database.

### <a name="syntax"></a>Sintassi
`rxSyncPackages(computeContext = rxGetOption("computeContext"),  scope = c("shared", "private"), owner = c(), verbose = getOption("verbose"))`

+ Contesto di calcolo

    Definire un contesto di calcolo di SQL Server, costituito da un'istanza e il database e i pacchetti per la sincronizzazione. Creare il contesto di SQL Server utilizzando il `RxInSqlServer` (funzione). Se non si specifica un contesto di calcolo, viene utilizzato il contesto di calcolo corrente. 

+ Ambito

  Indicare se si intende installare i pacchetti per un singolo utente o per un gruppo di utenti: 

    + **privato** l'operazione includerà solo i pacchetti che sono stati installati per l'uso da un proprietario specificato.
    + **condiviso** il oepration includerà tutti i pacchetti installati per un gruppo di utenti. 

  Se si esegue la funzione senza specificare l'ambito privato o condiviso, vengono applicati entrambi gli ambiti. Di conseguenza, l'intero set di pacchetti disponibili per tutti gli ambiti e gli utenti verranno copiati.

+ Proprietario 

    Specificare il proprietario dei pacchetti per la sincronizzazione. Il nome del proprietario deve essere un utente del database SQL valido. Se si lascia vuota, viene utilizzato il nome utente dell'account di accesso SQL specificato nella connessione.


### <a name="requirements"></a>Requisiti

+ La persona che esegue la funzione deve essere un'entità di sicurezza in cui l'istanza di SQL Server e database che contiene i pacchetti e deve essere un membro di un ruolo di gestione pacchetti: **condiviso rpkgs** o **rpkgs privato** 
  + Per sincronizzare i pacchetti contrassegnati come **condivisa**, la persona che esegue la funzione deve disporre dell'appartenenza al **condiviso rpkgs** ruolo e i pacchetti che vengono spostati sia stato installato per un oggetto condiviso libreria di ambito.
  + Per sincronizzare i pacchetti contrassegnati come **privata**, sia il proprietario del pacchetto o l'amministratore deve eseguire la funzione e i pacchetti devono essere privati.
+ **gli utenti di rpkgs** -i membri di questo ruolo possono eseguire codice che utilizza i pacchetti installati nell'istanza di SQL Server, ma non installare o pacchetti di sincronizzazione.
+ Per sincronizzare i pacchetti per conto di altri utenti, il proprietario deve essere un membro del **db_owner** ruolo del database.

## <a name="examples"></a>Esempi

Nell'esempio seguente crea una connessione a un'istanza specifica di SQL Server, specificare un database e quindi specificano un set di pacchetti per sincronizzare. 

Quando la chiamata a `rxSyncPackages` viene effettuata, il pacchetto elenchi vengono sincronizzati tra il file system e il database. 

### <a name="synchronize-all-by-database"></a>Sincronizzare tutti i database

In questo esempio ottiene tutti i pacchetti installati nel database [TestDB]. Poiché nessun proprietario specifico, l'elenco include tutti i pacchetti che sono stati installati per gli ambiti privati e condivisi.

```R
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

### <a name="restrict-synchronized-packages-by-scope"></a>Limitare i pacchetti sincronizzati dall'ambito 

Il seguente Sincronizza esempi solo i pacchetti in ambito condiviso o ambito privato.

**Ambito condiviso**

```R
rxSyncPackages(computeContext=computeContext, scope="shared", verbose=TRUE)
```

**Ambito privato**

```R
rxSyncPackages(computeContext=computeContext, scope="private", verbose=TRUE)
```

### <a name="restrict-synchronized-packages-by-owner"></a>Limitare i pacchetti sincronizzati dal proprietario 

Nell'esempio seguente viene illustrato come ottenere solo i pacchetti che sono stati installati per un utente specifico. In questo esempio, l'utente è identificato dal nome di account di accesso SQL, *user1*.

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

## <a name="see-also"></a>Vedere anche

[Gestione dei pacchetti R per SQL Server](../r/r-package-management-for-sql-server-r-services.md)
