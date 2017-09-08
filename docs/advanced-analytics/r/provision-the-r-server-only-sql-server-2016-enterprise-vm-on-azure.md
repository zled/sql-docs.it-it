---
title: Eseguire il provisioning della macchina virtuale di R Server Only SQL Server 2016 Enterprise in Azure | Microsoft Docs
ms.custom: 
ms.date: 06/05/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a3bfca0753984f09220d8ca4e4f6933c949daf2b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="advanced-analytics-virtual-machines-on-azure"></a>Analitica avanzate di macchine virtuali in Azure

Macchine virtuali in Azure sono una soluzione comoda per configurare rapidamente un ambiente completo del server per soluzioni di apprendimento automatico. Questo argomento vengono elencate alcune immagini di macchine virtuali che contengono R Server, SQL Server con machine learning o altri strumenti di analisi scientifica dei dati da Microsoft.

> [!TIP]
> È consigliabile utilizzare la nuova versione del portale di Azure e Azure Marketplace. Alcune immagini non sono disponibili quando si esplorano la raccolta di Azure nel portale classico.

Azure Marketplace contiene più macchine virtuali che supportano l'analisi scientifica dei dati. Questo elenco non intende essere completa, ma fornire solo i nomi delle immagini che includono servizi, per facilitare l'individuazione di apprendimento automatico di Microsoft R Server o SQL Server.

## <a name="how-to-provision-a-vm"></a>Come eseguire il provisioning di una macchina virtuale

Se si ha familiarità con l'utilizzo di macchine virtuali di Azure, è consigliabile che vedere gli articoli per ulteriori informazioni sull'utilizzo del portale e la configurazione di una macchina virtuale.

+ [Macchine virtuali - Introduzione](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Introduzione a macchine virtuali di Windows](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-hero-tutorial/)

### <a name="find-an-image"></a>Trovare un'immagine

1. Il dashboard di Azure fare clic su **Marketplace**.

    - Fare clic su **Intelligence e analitica** o **database**, e quindi digitare "R" il **filtro** controllo per visualizzare un elenco di macchine virtuali R Server.
    - Altri possibili le stringhe per il **filtro** controllo sono *analisi scientifica dei dati* e *machine learning*
    - Utilizzare il carattere jolly % nella ricerca per trovare i nomi di macchina virtuale che contengono una stringa di destinazione, ad esempio *R* o *Julia*.

2. Per ottenere R Server per Windows, selezionare **R Server solo SQL Server 2016 Enterprise Edition**.
  
    [R Server](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) è concesso in licenza come una funzionalità di SQL Server Enterprise Edition, ma la versione 9.1. viene installato come server autonomo e gestite in base ai criteri di supporto del ciclo di vita moderna.

3. Dopo la creazione e l'esecuzione della macchina virtuale fare clic sul pulsante **Connetti** per aprire una connessione e accedere alla nuova macchina virtuale.

4. Dopo la connessione, si potrebbe essere necessario installare gli strumenti di sviluppo o di altri strumenti di R.

### <a name="install-additional-r-tools"></a>Installare gli strumenti di R aggiuntivi

Per impostazione predefinita, Microsoft R Server include tutti gli strumenti R installati con un'installazione di base di R, tra cui RTerm ed RGui. Un collegamento a RGui è stato aggiunto al desktop, se si vuole iniziare a usare R sin da subito.

Tuttavia, può essere necessario installare altri strumenti di R, ad esempio RStudio, gli strumenti R per Visual Studio (RTVS) o Microsoft R Client. Per istruzioni e percorsi di download e istruzioni, vedere i collegamenti seguenti:
+ [Strumenti R per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio per Windows](https://www.rstudio.com/products/rstudio/download/)

Al termine dell'installazione, assicurarsi di modificare il percorso di runtime predefinito di R in modo che tutti gli strumenti di sviluppo di R usino le librerie di Microsoft R Server.

### <a name="configure-server-for-web-services"></a>Configurare i server per servizi web

Se la macchina virtuale include R Server, è richiesta una configurazione aggiuntiva per usare la distribuzione dei servizi Web, l'esecuzione remota o per usare R Server come server di distribuzione all'interno dell'organizzazione. Per istruzioni, vedere [Configure R Server for Operationalization](https://msdn.microsoft.com/microsoft-r/operationalize/configuration-initial) (Configurare R Server per l'operazionalizzazione).

> [!NOTE]
> Configurazione aggiuntiva non è necessario se si desidera utilizzare i pacchetti, ad esempio RevoScaleR o MicrosoftML.

## <a name="r-server-images"></a>R Server immagini

### <a name="microsoft-data-science-virtual-machine"></a>Impostazioni della macchina virtuale Microsoft per l'analisi scientifica dei dati

Sono configurate per Microsoft R Server, nonché Python (distribuzione Anaconda), un server Jupyter notebook, Visual Studio Community Edition, Power BI Desktop, di Azure SDK e SQL Server Express edition.

La versione di Windows viene eseguito in Windows Server 2012 e contiene molti strumenti speciali per la modellazione e analitica, tra cui CNTK e mxnet, pacchetti R più diffusi, ad esempio xgboost e Vowpal Wabbit.

### <a name="linux-data-science-virtual-machine"></a>Macchina virtuale di analisi scientifica dei dati di Linux

Sono disponibili inoltre strumenti comuni per attività di sviluppo e di analisi scientifica dei dati, incluso Microsoft R Open, Microsoft R Server Developer Edition, Anaconda Python e Jupyter notebook per Python, R e Julia.

Questa immagine di macchina virtuale è stato recentemente aggiornata per includere JupyterHub, software open source che consente l'utilizzo da più utenti, tramite i metodi di autenticazione diversi, tra cui l'autenticazione di account locali del sistema operativo e l'autenticazione account Github. JupyterHub è un'opzione particolarmente utile se si desidera eseguire una classe di training e tutti gli studenti condividono lo stesso server, ma utilizzare directory e i blocchi appunti separati.

Le immagini vengono fornite per Ubuntu, in Centos e Centos CSP.

### <a name="r-server-only-sql-server-2016-enterprise"></a>R Server solo SQL Server 2016 Enterprise Edition

Questa macchina virtuale include un programma di installazione autonomo per [R Server 9.1.](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) che supporta il nuovo modello di licenza del ciclo di vita di Software più recenti.

 R Server è disponibile anche nelle immagini per Linux CentOS versione 7.2, Linux RedHat 7.2 e Ubuntu versione 16.04.

 > [!NOTE]
 > Queste macchine virtuali sostituiscono la **versione RRE della macchina virtuale di Windows** precedentemente disponibile in Azure Marketplace.

## <a name="sql-server-images"></a>Immagini di SQL Server

Per usare R Services (In-Database) o Machine Learning Services, è necessario installare una delle macchine virtuali SQL Server Enterprise Edition o Developer edition e aggiungere il servizio machine learning, come descritto qui: [l'installazione di SQL Server R Services in un Macchina virtuale di Azure](../../advanced-analytics/r-services/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

> [!NOTE]
> Attualmente, machine learning servizi non sono supportati nelle macchine virtuali Linux per SQL Server 2017, o in Database SQL di Azure. Per Windows, è necessario utilizzare SQL Server 2016 SP1 o SQL Server 2017.

La macchina virtuale di analisi scientifica dei dati include anche SQL Server 2016 con la funzionalità di servizi R già abilitata.


## <a name="other-vms"></a>Altre macchine virtuali

### <a name="deep-learning-toolkit-for-the-data-science-virtual-machine"></a>Deep Learning Toolkit per la macchina virtuale di analisi scientifica dei dati

La macchina virtuale contiene lo stesso computer disponibili nella macchina virtuale di analisi scientifica dei dati, strumenti di apprendimento, ma con le versioni GPU di mxnet, CNTK, TensorFlow e Keras. Questa immagine può essere utilizzata solo su istanze di Azure GPU N-series. 

Il toolkit di formazione fornisce inoltre un set di esempio deep learning soluzioni che usano la GPU, inclusi il riconoscimento di immagini per il database CIFAR 10 e un esempio di riconoscimento di caratteri nel database MNIST. Le istanze GPU sono attualmente disponibili nel centro-meridionali, Stati Uniti orientali, Europa occidentale e Asia sudorientale.

> [!IMPORTANT]
> Le istanze della GPU sono attualmente disponibili solo nell'area centro-meridionale degli Stati Uniti.


## <a name="frequently-asked-questions"></a>Domande frequenti

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>È possibile installare una macchina virtuale con SQL Server 2017?

Le immagini sono disponibili che contengono 2017 CTP 2.0 di SQL Server per gli ambienti Linux, ma questi ambienti non supportano servizi di Machine Learning. 

Una macchina virtuale basato su Windows per SQL Server 2017 Enterprise Edition che include i servizi di Machine Learning saranno disponibile dopo il rilascio pubblico. 

In alternativa, è possibile utilizzare l'immagine di SQL Server 2016 e aggiornare l'istanza di R, come descritto qui: [aggiornare un'istanza utilizzando SqlBindR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). 

In alternativa, creare una macchina virtuale e scaricare l'anteprima della versione CTP 2.0 di [SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-2017).

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Come si accede ai dati in un account di archiviazione di Azure?

Quando è necessario usare i dati dell'account di archiviazione di Azure, è possibile usare diverse opzioni per l'accesso o lo spostamento dei dati:

+ Copiare i dati dall'account di archiviazione nel file system locale mediante un'utilità, ad esempio [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Aggiungere i file a una condivisione file nell'account di archiviazione e quindi montare la condivisione file come un'unità di rete nella macchina virtuale.  Per altre informazioni, vedere [Montare la condivisione file](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Come si usano i dati di Azure Data Lake Storage (ADLS)?

È possibile leggere i dati dall'archivio ADLS con RevoScaleR, se si fa riferimento allo stesso modo che un HDFS file system utilizzando webHDFS l'account di archiviazione.  Per ulteriori informazioni, vedere l'articolo: [usando R per eseguire operazioni di file System in un archivio Azure Data Lake](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).

## <a name="see-also"></a>Vedere anche

[SQL Server R Services](https://msdn.microsoft.com/library/mt604845.aspx)


