---
title: Eseguire il provisioning di una macchina virtuale per machine learning in Azure | Documenti Microsoft
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 6777a47d9f2078b662990c2597f84cc41222de63
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="provision-a-virtual-machine-for-machine-learning-on-azure"></a>Eseguire il provisioning di una macchina virtuale per machine learning in Azure

Macchine virtuali in Azure sono una soluzione comoda per configurare rapidamente un ambiente completo del server per soluzioni di apprendimento automatico.

Questo articolo elenca le immagini di macchina virtuale che contengono SQL Server con di machine learning, nonché alcuni le macchine virtuali correlate.

Questo articolo fornisce anche le risposte alle domande più comuni sulla modifica o l'aggiornamento di un'istanza esistente di SQL Server in una macchina virtuale.

+ [Elenco di macchine virtuali corrente](#bkmk_list)

## <a name="provision-a-virtual-machine-with-sql-server-and-machine-learning"></a>Eseguire il provisioning di una macchina virtuale con SQL Server e machine learning

Se si ha familiarità con l'utilizzo di macchine virtuali di Azure, è consigliabile che vedere gli articoli per ulteriori informazioni sull'utilizzo del portale e la configurazione di una macchina virtuale.

+ [Macchine virtuali - Introduzione](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Guida introduttiva con macchine virtuali di Windows](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/)

Assicurarsi di usare la nuova versione del portale di Azure o Azure Marketplace. Alcune immagini non sono disponibili quando si esplorano la raccolta di Azure nel portale classico.

**Creare la macchina virtuale**

1. Aprire il portale di Azure: [portal.azure.com](https:portal.azure.com).

2. Fare clic su **macchine virtuali**, oppure fare clic su **New**.

3. Scegliere **Aggiungi**.

4. Nella casella di ricerca nella parte superiore della pagina, digitare "Machine Learning Server" o "SQL Server" per visualizzare un elenco di macchine virtuali correlate.

5. Esaminare i requisiti e fare clic su **crea** per iniziare.

6. Dopo la macchina virtuale è stata creata e sia in esecuzione, fare clic su di **Connetti** pulsante per aprire una connessione e accedere al nuovo computer.

5. Dopo la connessione, è possibile installare i pacchetti R o Python aggiuntivi o configurare lo strumento di sviluppo preferito.

### <a name="connect-to-the-virtual-machine"></a>Connettersi alla macchina virtuale

Il modo in cui che un client si connette a SQL Server in esecuzione in una macchina virtuale è diverso a seconda della posizione del client e la configurazione di rete.

Per ulteriori informazioni, vedere [Connetti a una macchina virtuale di SQL Server in Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-connect).

## <a name="frequently-asked-questions"></a>Domande frequenti

In questa sezione contiene alcune domande frequenti sulle macchine virtuali di Microsoft di apprendimento automatico.

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>È possibile installare una macchina virtuale con SQL Server 2017?

Una macchina virtuale basato su Windows per SQL Server 2017 Enterprise Edition che include i servizi di Machine Learning è disponibile a partire da novembre 2017. 

Per gli annunci relativi nuove macchine virtuali di analisi scientifica dei dati, controllare i siti di blog:

+ [Cortana Intelligence e Machine Learning](https://blogs.technet.microsoft.com/machinelearning/)
+ [Data Platform Insider](https://blogs.technet.microsoft.com/dataplatforminsider/)

### <a name="adding-sql-server-to-an-existing-virtual-machine"></a>Aggiunta di SQL Server a una macchina virtuale esistente

Oltre a creare una macchina virtuale usando un'immagine che include già l'apprendimento, è possibile installare SQL Server in una macchina virtuale esistente e abilitare di machine learning funzionalità macchina di SQL Server. È consigliabile Enterprise o Developer edition, per evitare limitazioni delle risorse. Installazione richiede inoltre che si utilizza la propria chiave di licenza.

Quando si esegue il programma di installazione, assicurarsi di selezionare di machine learning funzionalità e almeno una lingua (R o Python). Alcuni passaggi aggiuntivi sono è necessari abilitare i servizi di machine learning per comunicare con SQL Server e per abilitare la rete nella macchina virtuale.

Per ulteriori informazioni, vedere [l'installazione di SQL Server R Services in una macchina virtuale Azure](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

### <a name="using-machine-learning-in-azure-sql-database"></a>Utilizzo di apprendimento in database SQL di Azure

A partire da rientrano 2017, Database SQL di Azure supporta l'uso di R per eseguire il training di modelli e utilizzarli per la stima. 

R Services nel database è disponibile come funzionalità di anteprima e presenta alcune limitazioni rispetto alla versione locale di SQL Server. Per ulteriori informazioni, vedere [database SQL di Azure](../r/using-r-in-azure-sql-database.md).

### <a name="can-i-upgrade-the-sql-server-version-on-a-virtual-machine"></a>È possibile aggiornare la versione di SQL Server in una macchina virtuale?

Anche se le immagini di SQL Server 2016 supportano R, se si desidera utilizzare Python, è possibile aggiornare a SQL Server 2017, che aggiorna anche altri componenti di apprendimento automatico.

Per aggiornare la versione di SQL Server in cui è installato, aprire il Centro installazione SQL Server nella macchina virtuale e selezionare il **aggiornamento** opzione. A seconda della macchina virtuale creata, una licenza potrebbe essere necessario.

Per ulteriori informazioni, vedere [l'aggiornamento di SQL Server mediante l'installazione guidata](https://docs.microsoft.com/sql/database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup).

### <a name="can-i-upgrade-just-the-machine-learning-components"></a>È possibile eseguire l'aggiornamento solo di machine learning componenti?

Quando nuovi aggiornamenti vengono pubblicati per RevoScaleR, MicrosoftML o revoscalepy, è possibile eseguire l'aggiornamento di machine learning componenti utilizzati da SQL Server, tramite un processo noto come _associazione_. Ciò non modifica la versione di SQL Server, ma modifica i criteri di supporto per l'istanza.

Per ulteriori informazioni, vedere [SqlBindR utilizzare per l'aggiornamento dei componenti di machine learning in SQL Server](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Come si accede ai dati in un account di archiviazione di Azure?

Quando è necessario usare i dati dell'account di archiviazione di Azure, è possibile usare diverse opzioni per l'accesso o lo spostamento dei dati:

+ Copiare i dati dall'account di archiviazione nel file system locale mediante un'utilità, ad esempio [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Aggiungere i file a una condivisione file nell'account di archiviazione e quindi montare la condivisione file come un'unità di rete nella macchina virtuale. Per altre informazioni, vedere [Montare la condivisione file](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Come si usano i dati di Azure Data Lake Storage (ADLS)?

È possibile leggere i dati dall'archivio ADLS utilizzando RevoScaleR, webHDFS per fare riferimento allo stesso modo che un HDFS file sistema l'account di archiviazione. Per ulteriori informazioni, vedere l'articolo: [usando R per eseguire operazioni di file System in un archivio Azure Data Lake](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).

### <a name="i-cant-find-the-rre-virtual-machine"></a>Impossibile trovare la macchina virtuale RRE

Il "RRE per macchina virtuale Windows" che in precedenza era disponibile in Azure Marketplace è stata sostituita dall'immagine "Machine Learning Server per Windows".

Sono disponibili per Linux CentOS versione 7.2, Linux RedHat 7.2 e Ubuntu versione 16.04 anche le immagini della macchina Server di apprendimento.

Per ulteriori informazioni, vedere [Machine Learning Server nel Cloud](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-in-the-cloud)

### <a name="configuring-machine-learning-server-or-r-server-to-support-web-services"></a>Configurazione di Server di Machine Learning o R Server per supportare i servizi web

Se si usa una macchina virtuale che include i Server di Machine Learning, potrebbe essere necessaria per utilizzare una distribuzione del servizio web, l'esecuzione remota, o utilizzare la macchina virtuale come server di distribuzione nell'organizzazione configurazione aggiuntiva.

Per istruzioni, vedere [configurazione del Server di Machine Learning per rendere operative le analitica](https://docs.microsoft.com/machine-learning-server/operationalize/configure-machine-learning-server-one-box).

Configurazione aggiuntiva non è necessario se si desidera utilizzare i pacchetti, ad esempio RevoScaleR o MicrosoftML.

## <a name="bkmk_list"></a>Elenco di macchine virtuali

Le macchine virtuali seguenti sono attualmente disponibili per machine learning con SQL Server:

|nome| Commenti|
|----|----|----|
| **SQL Server 2016**| ***  |
|SQL Server 2016 Enterprise Edition SP1 in Windows|R Services per integrata analitica avanzate.|
|BYOL SQL Server 2016 SP1 Enterprise in Windows Server |R Services per integrata analitica avanzate. |
|Licenza gratuita: SQL Server 2016 Developer SP1 in Windows Server 2016 |R Services per integrata analitica avanzate. |
| Macchina virtuale di analisi scientifica dei dati - Windows 2012|Contiene i comuni strumenti di analisi scientifica dei dati, incluso Microsoft R Server Developer Edition, SQL Server 2016 Developer edition, distribuzione Anaconda Python, Julia Pro developer edition e notebook Jupyter per R.| 
| Macchina virtuale di analisi scientifica dei dati - 2016 Windows|Include SQL Server 2016 Developer Edition, con supporto per analitica R nel database.|
|**SQL Server 2017**| ***   |
|SQL Server 2017 Enterprise Windows Server 2016| Servizi di Machine Learning con supporto del linguaggio Python e R.|
|BYOL SQL Server 2017 Enterprise Windows Server 2016|Servizi di Machine Learning con supporto del linguaggio Python e R.|
| Licenza di gratuita di SQL Server: SQL Server 2017 Developer Edition in Windows Server|Servizi di Machine Learning con supporto del linguaggio Python e R.|
| **Altro**| *** |
| Machine Learning Server solo SQL Server 2017 Enterprise|Simile all'immagine di SQL Server 2016 Enterprise Edition, ma contiene la versione autonoma di Server di Machine Learning e ha core ScaleR e funzionalità di rendere operativo ottimizzato per Windows ambienti.|
| Server di Machine Learning per Windows|Contiene la versione autonoma di Machine Learning Server, con funzionalità di rendere operativo ottimizzata per ambienti Windows.|
|Macchina virtuale di analisi scientifica dei dati |Versioni di Linux includono R Server. Macchine virtuali Linux che includono 2017 di SQL Server non può eseguire codice R o Python in SQL Server. Tuttavia, è possibile eseguire l'assegnazione dei punteggi in un modello con training utilizzando la funzione di stima di T-SQL. Per ulteriori informazioni, vedere [in SQl Server Native di assegnazione dei punteggi](../sql-native-scoring.md).|
