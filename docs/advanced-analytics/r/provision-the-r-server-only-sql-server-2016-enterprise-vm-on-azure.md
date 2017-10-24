---
title: Eseguire il provisioning di una macchina virtuale per machine learning in Azure | Documenti Microsoft
ms.custom: 
ms.date: 10/16/2017
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
ms.sourcegitcommit: 8cc1fcfdeae8742a93916dfb08c9db1215f88721
ms.openlocfilehash: 7cb9e069fc3b537f8aab9d048a152435ad0cc6ac
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="provision-a-virtual-machine-for-machine-learning-on-azure"></a>Eseguire il provisioning di una macchina virtuale per machine learning in Azure

Macchine virtuali in Azure sono una soluzione comoda per configurare rapidamente un ambiente completo del server per soluzioni di apprendimento automatico. In questo articolo sono elencate alcune immagini di macchine virtuali che contengono Server R, Machine Learning Server o SQL Server con machine learning.

Questo elenco non intende essere completa, ma fornire solo i nomi delle immagini che sono correlati a Machine Learning Server o SQL Server Machine Learning Services, per facilitare l'individuazione.

> [!TIP]
> È consigliabile utilizzare la nuova versione del portale di Azure e Azure Marketplace. Alcune immagini non sono disponibili quando si esplorano la raccolta di Azure nel portale classico.

## <a name="how-to-provision-a-virtual-machine"></a>Come eseguire il provisioning di una macchina virtuale

Se si ha familiarità con l'utilizzo di macchine virtuali di Azure, è consigliabile che vedere gli articoli per ulteriori informazioni sull'utilizzo del portale e la configurazione di una macchina virtuale.

+ [Macchine virtuali - Introduzione](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Introduzione a macchine virtuali di Windows](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/)

## <a name="find-a-machine-learning-image"></a>Trovare un'immagine di machine learning

1. Dal portale di Azure (portal.azure.com), fare clic su **macchine virtuali**, oppure fare clic su **New**.

2. Individuare la casella di ricerca nella parte superiore della pagina, è possibile utilizzare per filtrare le risorse in base al nome. 

3. Digitare "R Server" (o "ML Server") il **filtro** controllo per visualizzare un elenco di risorse correlate. Fare clic su **ricerca in Marketplace** per visualizzare le macchine virtuali.

    > [!TIP]
    > 
    > Altre stringhe per il controllo filtro possibili sono "analisi scientifica dei dati" e "machine learning".
    > 
    > Utilizzare il `%` jolly nella ricerca per trovare i nomi delle macchine virtuali. Ad esempio, è possibile digitare `"`% % Julia` or `%R %'.

4. Per ottenere R Server per Windows, selezionare **R Server solo SQL Server 2016 Enterprise Edition**.
  
    [R Server](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) è concesso in licenza come una funzionalità di SQL Server Enterprise Edition, ma la versione 9.1 viene installato come server autonomo e viene gestita in base ai criteri di supporto del ciclo di vita moderna.

    > [!NOTE] 
    > 
    > Questo rientra, cercare per la versione di una nuova macchina virtuale che include 2017 di SQL Server e il 9.2.1 versione del Server di Machine Learning.
    > Fino ad allora, è possibile aggiornare la versione di SQL Server installata nella macchina virtuale utilizzando il Centro installazione SQL Server e scegliendo l'opzione di aggiornamento. Per ulteriori informazioni, vedere [l'aggiornamento di SQL Server mediante l'installazione guidata](https://docs.microsoft.com/sql/database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup).

5. Dopo la macchina virtuale è stata creata e sia in esecuzione, fare clic su di **Connetti** pulsante per aprire una connessione e accedere al nuovo computer.

5. Dopo la connessione, è possibile installare il pacchetto R aggiuntivo o lo strumento di sviluppo preferito.

### <a name="install-additional-r-tools"></a>Installare gli strumenti di R aggiuntivi

Per impostazione predefinita, Microsoft R Server include tutti gli strumenti R installati con un'installazione di base di R, tra cui RTerm ed RGui. Un collegamento a RGui è stata aggiunta anche al desktop.

Tuttavia, può essere necessario installare altri strumenti di R, ad esempio RStudio, strumenti R per Visual Studio (RTVS) o Microsoft R Client. Per istruzioni e percorsi di download e istruzioni, vedere i collegamenti seguenti:

+ [Strumenti R per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio per Windows](https://www.rstudio.com/products/rstudio/download/)

Al termine dell'installazione, assicurarsi di modificare il percorso di runtime predefinito di R in modo che tutti gli strumenti di sviluppo di R usino le librerie di Microsoft R Server.

### <a name="configure-r-server-to-support-web-services"></a>Configurare R Server per supportare i servizi web

Configurazione aggiuntiva è necessaria per utilizzare una distribuzione del servizio web, l'esecuzione remota, o di usare R Server come server di distribuzione nell'organizzazione. Per istruzioni, vedere [configurazione R Server per rendere operative le analitica](https://docs.microsoft.com/machine-learning-server/install/operationalize-r-server-one-box-config).

> [!NOTE]
> Configurazione aggiuntiva non è necessario se si desidera utilizzare i pacchetti, ad esempio RevoScaleR o MicrosoftML.

## <a name="other-virtual-machines"></a>Altre macchine virtuali

Le immagini seguenti sono disponibili da Azure Marketplace e includere completamente configurate computer gli strumenti di apprendimento, ma non includono necessariamente SQL Server.

### <a name="data-science-virtual-machine"></a>Macchina virtuale di analisi scientifica dei dati

Questa immagine è preconfigurata con Microsoft R Server, nonché Python (distribuzione Anaconda), un server Jupyter notebook, Visual Studio Community Edition, Power BI Desktop, di Azure SDK e SQL Server Express edition.

La versione di Windows viene eseguito in Windows Server 2012 e contiene molti strumenti speciali per la modellazione e analitica, tra cui [CNTK](https://www.microsoft.com/cognitive-toolkit/), [mxNet](https://mxnet.incubator.apache.org/), e dei pacchetti R più diffusi, ad esempio **xgboost**.

Le versioni di Linux vengono fornite per Ubuntu, in Centos e Centos CSP e contengono molti strumenti comuni per le attività di sviluppo e di analisi scientifica dei dati.

Per ulteriori informazioni, vedere [Introduzione a Data Science macchina virtuale di Azure per Linux e Windows](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-vm).

Questa immagine è stata aggiornata di recente in modo da includere: 

+ Supporto per Julia, la lingua di analisi scientifica dei dati potenti e scalabili del futuro 
+ JupyterHub, che è un'opzione utile quando si desidera eseguire una classe di training e tutti gli studenti condividono lo stesso server, ma utilizzare directory e i blocchi appunti separati.

Per ulteriori informazioni sugli strumenti supportati e Framework di machine learning, vedere [conoscere la macchina virtuale di analisi scientifica dei dati](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/dsvm-tools-overview)

### <a name="r-server-virtual-machines"></a>Macchine virtuali R Server

Oltre al **R Server solo SQL Server 2016 Enterprise Edition** immagine, è possibile ottenere macchine virtuali autonome che contengono R Server. Le immagini sono disponibili per Linux CentOS versione 7.2, Linux RedHat 7.2 e Ubuntu versione 16.04.

Per ulteriori informazioni, vedere [Machine Learning Server nel Cloud](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-in-the-cloud)

 > [!NOTE]
 > Queste macchine virtuali sostituiscono la **versione RRE della macchina virtuale di Windows** precedentemente disponibile in Azure Marketplace.

### <a name="sql-server-virtual-machines"></a>Macchine virtuali di SQL Server

Sono disponibili due opzioni per l'utilizzo di apprendimento di SQL Server in Azure:

+ Ottiene una delle immagini di macchina virtuale che include SQL Server R Services preinstallato.
+ Creare una macchina virtuale di Azure e installare SQL Server Enterprise Edition o Developer edition utilizzando il proprio codice di licenza. 
  
    Quindi, eseguire nuovamente l'installazione per aggiungere e abilitare il servizio machine learning, come descritto qui: [l'installazione di SQL Server R Services in una macchina virtuale Azure](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).
+ Creare un Database di SQL Azure mediante un livello di servizio in grado di supportare l'apprendimento e utilizzare la nuova funzionalità di R Services attualmente in anteprima. Per ulteriori informazioni, vedere [database SQL di Azure](../r/using-r-in-azure-sql-database.md).

> [!NOTE]
> Attualmente, servizi di SQL Server Machine Learning non è supportato nelle macchine virtuali Linux per SQL Server 2017. Tuttavia, è possibile eseguire l'assegnazione dei punteggi in un modello con training utilizzando la funzione di stima di T-SQL. Per ulteriori informazioni, vedere [in SQl Server Native di assegnazione dei punteggi](../sql-native-scoring.md). 

### <a name="virtual-machines-for-deep-learning"></a>Macchine virtuali per la formazione 

Microsoft fornito in precedenza, il Toolkit di apprendimento completa per i dati dell'analisi scientifica dei macchina virtuale, che è possibile aggiungere a una macchina virtuale scienza esistente dati. Questo toolkit ora viene sostituito dalla macchina virtuale di apprendimento completa, che contiene gli strumenti di apprendimento completa comuni:

+ Le edizioni di GPU di formazione Framework come Microsoft cognitivi Toolkit, TensorFlow, Keras e Caffe
+ Driver GPU predefiniti
+ Una raccolta di strumenti per l'elaborazione di testo e immagine
+ Strumenti di sviluppo di Enterprise, ad esempio Microsoft R Server Developer Edition, Python Anaconda, Jupyter notebook per Python e R
+ Strumenti di sviluppo per Python, R, SQL Server e molto altro ancora
+ Esempi end-to-end per una conoscenza di testo e immagine

La macchina virtuale di apprendimento completa è disponibile nel server di Windows 2016 o piattaforme Ubuntu Linux. Per ulteriori informazioni, vedere [di formazione e AI Framework](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/dsvm-deep-learning-ai-frameworks).

> [!IMPORTANT]
> 
> La distribuzione di questa macchina virtuale richiede le immagini di macchina virtuale di Azure GPU NC-series, sono disponibili in aree di Azure limitate. Per informazioni sulla disponibilità, vedere [i prodotti disponibili per area](https://azure.microsoft.com/en-us/regions/services/). Quando si esegue il provisioning della macchina virtuale, assicurarsi di utilizzare **HDD** come tipo di disco, non **SSD**.

## <a name="frequently-asked-questions"></a>Domande frequenti

In questa sezione contiene alcune domande frequenti sulle macchine virtuali di Microsoft di apprendimento automatico.

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>È possibile installare una macchina virtuale con SQL Server 2017?

Una macchina virtuale basato su Windows per SQL Server 2017 Enterprise Edition che include i servizi di Machine Learning sarà presto disponibile. Cercare gli annunci in questi siti di blog:

+ [Cortana Intelligence e machine Learning](https://blogs.technet.microsoft.com/machinelearning/)
+ [Data Platform Insider](https://blogs.technet.microsoft.com/dataplatforminsider/)

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Come si accede ai dati in un account di archiviazione di Azure?

Quando è necessario usare i dati dell'account di archiviazione di Azure, è possibile usare diverse opzioni per l'accesso o lo spostamento dei dati:

+ Copiare i dati dall'account di archiviazione nel file system locale mediante un'utilità, ad esempio [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Aggiungere i file a una condivisione file nell'account di archiviazione e quindi montare la condivisione file come un'unità di rete nella macchina virtuale.  Per altre informazioni, vedere [Montare la condivisione file](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Come si usano i dati di Azure Data Lake Storage (ADLS)?

È possibile leggere i dati dall'archivio ADLS con RevoScaleR, se si fa riferimento allo stesso modo che un HDFS file system utilizzando webHDFS l'account di archiviazione.  Per ulteriori informazioni, vedere l'articolo: [usando R per eseguire operazioni di file System in un archivio Azure Data Lake](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).



