---
title: "Eseguire il provisioning della macchina virtuale di R Server Only SQL Server 2016 Enterprise in Azure | Microsoft Docs"
ms.custom: ""
ms.date: "12/22/2016"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 5
---
# Eseguire il provisioning della macchina virtuale di R Server Only SQL Server 2016 Enterprise in Azure

La macchina virtuale di R Server Only SQL Server 2016 Enterprise in Azure è una nuova opzione per la configurazione semplice e rapida di un ambiente server per il supporto di soluzioni R. Questa macchina virtuale di Azure è stata preconfigurata con Microsoft R Server (autonomo). 

Questa nuova macchina virtuale sostituisce la versione RRE della macchina virtuale di Windows, precedentemente disponibile in Azure Marketplace. 

Questa macchina virtuale include anche DeployR Enterprise, per la distribuzione di analisi R all'interno di applicazioni e sistemi back-end. Per altre informazioni, vedere [About Deploy R](https://msdn.microsoft.com/microsoft-r/deployr-about) (Informazioni su DeployR).


## Eseguire il provisioning della macchina virtuale di R Server

Se non si ha familiarità con l'uso delle macchine virtuali di Azure, si consiglia di vedere questo articolo per altre informazioni sull'uso del portale e sulla configurazione di una macchina virtuale.
[Macchine virtuali - Introduzione](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)

Per creare la macchina virtuale in R Server da Microsoft Azure Marketplace 
1. Fare clic su **Macchine virtuali** e, nella casella di ricerca, digitare *R Server*.
2. Selezionare **R Server Only SQL Server 2016 Enterprise**
3. Continuare a eseguire il provisioning della macchina virtuale come descritto in questo articolo: [https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-hero-tutorial/) 
7. Dopo la creazione e l'esecuzione della macchina virtuale fare clic sul pulsante **Connetti** per aprire una connessione e accedere alla nuova macchina virtuale.
8. Quando ci si connette, **Server Manager** viene aperto per impostazione predefinita, ma non viene richiesta alcuna configurazione aggiuntiva del server. Chiudere **Server Manager** per accedere al desktop e procedere con i passaggi successivi:
    + Installazione di strumenti R aggiuntivi o di strumenti di sviluppo
    + Configurazione di DeployR  

Per individuare la macchina virtuale di R Server nel portale classico di Azure
1. Fare clic su **Macchine virtuali** e quindi su **NUOVO**.
2. Nel riquadro **NUOVO** le opzioni **Calcolo** e **Macchina virtuale** devono essere già selezionate. 
3. Fare clic su **Da raccolta** per individuare l'immagine della macchina virtuale. È possibile digitare *R Server* nella casella di ricerca oppure fare clic su **Microsoft** e quindi scorrere verso il basso fino a visualizzare **R Server Only SQL Server 2016 Enterprise**.


## Installare gli strumenti R
Per impostazione predefinita, Microsoft R Server include tutti gli strumenti R installati con un'installazione di base di R, tra cui RTerm ed RGui. Un collegamento a RGui è stato aggiunto al desktop, se si vuole iniziare a usare R sin da subito.

Tuttavia, può essere necessario installare altri strumenti R, ad esempio RStudio, R Tools per Visual Studio o Microsoft R Client. Per istruzioni e percorsi di download e istruzioni, vedere i collegamenti seguenti:
+ [Strumenti R per Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio per Windows](https://www.rstudio.com/products/rstudio/download/)

Dopo aver installato questi strumenti, assicurarsi di puntare gli strumenti alle librerie di R Server.

## Uso di DeployR nella macchina virtuale

Per usare l'istanza di DeployR installata nella macchina virtuale, sono necessari altri passaggi. 

Per configurare l'istanza di DeployR:

1. Nella macchina virtuale aprire **DeployR Administrator Utility** (Utilità di amministrazione di DeployR).
2. Impostare la password dell'amministratore DeployR come descritto in [Post Installation Steps](https://msdn.microsoft.com/microsoft-r/deployr-install-on-windows) (Passaggi successivi all'installazione).
3. Impostare il contesto di DeployR Web. Per altre informazioni, vedere [DeployR Admin Installation in the Cloud](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud) (Installazione di Deploy R nel cloud). 
4. Aprire le porte appropriate nella macchina virtuale come descritto in [Configuring Azure Endpoints](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud#configuring-azure-endpoints) (Configurazione degli endpoint di Azure). 
4. Aggiornare Windows Firewall come descritto in [Updating the firewall](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud#updating-the-firewall) (Aggiornamento del firewall). 

## Accesso ai dati in un account di archiviazione di Azure 

Quando è necessario usare i dati dell'account di archiviazione di Azure, è possibile usare diverse opzioni per l'accesso o lo spostamento dei dati:


+ Copiare i dati dall'account di archiviazione nel file system locale mediante un'utilità, ad esempio [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Aggiungere i file a una condivisione file nell'account di archiviazione e quindi montare la condivisione file come un'unità di rete nella macchina virtuale.  Per altre informazioni, vedere [Montare la condivisione file](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/). 

## Uso dei dati in un account di Azure Data Lake Storage (ADLS)

È possibile leggere dati dall'archivio ADLS tramite ScaleR, se si fa riferimento all'account di archiviazione in modo analogo a un file system HDFS, tramite webHDFS.  Per altre informazioni, vedere questa [guida all'installazione](http://go.microsoft.com/fwlink/?LinkId=723452).

## Risorse

Ulteriore documentazione su Microsoft R è disponibile in MSDN Library: [R Server e Scale R](https://msdn.microsoft.com/microsoft-r)  


Per informazioni generali su R, vedere le risorse aggiuntive seguenti: 
+ [DataCamp](http://www.datacamp.com): fornisce un corso gratuito introduttivo e di livello intermedio su R e un corso sull'uso dei Big Data con Revolution R.
+ [Stack Overflow](http://www.stackoverflow.com): un'ottima risorsa per la programmazione R che contiene anche domande sugli strumenti di Machine Learning. 
+ [Cross Validated](https://stats.stackexchange.com/): sito per domande sui problemi statistici in Machine Learning.
+ [Archivi della lista di distribuzione R Help](https://www.r-project.org/mail.html): valida risorsa con informazioni in ordine cronologico. 
+ [Sito Web MRAN](https://mran.microsoft.com/documents/getting-started/): contiene molte altre risorse R.  

## Vedere anche
[SQL Server R Services](https://msdn.microsoft.com/library/mt604845.aspx)
