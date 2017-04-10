---
title: "Attivit&#224; Pig di Azure HDInsight | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afppigtask.f1"
  - "sql14.dts.designer.afppigtask.f1"
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Attivit&#224; Pig di Azure HDInsight
  Usare l' **attività Pig di Azure HDInsight** per eseguire uno script Pig in un cluster di Azure HDInsight. 
    
Per aggiungere un'**attività Pig di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all'**editor dell'attività Pig di Azure HDInsight**.  
  
 L'**attività Pig di Azure HDInsight** è un componente del Feature Pack di SQL Server Integration Services (SSIS) per Azure per SQL Server 2016. Scaricare il Feature Pack [qui](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
1.  Per il campo **AzureSubscriptionConnection** selezionare un'istanza di Gestione connessione esistente per una sottoscrizione di Azure oppure creare una nuova istanza che faccia riferimento a una sottoscrizione di Azure che ospita il cluster HDInsight.  
  
2.  Per il campo **HDInsightClusterName** immettere il nome del cluster HDInsight in cui si vuole eseguire lo script Pig.  
  
3.  Per il campo **LocalLogFolder** fare clic su **… (puntini di sospensione)**, selezionare la cartella in cui si vuole caricare i log di elaborazione Pig dal cluster HDInsight.  
  
4.  È possibile specificare lo script Pig in due modi:  
  
    1.  **Script inline**: fare clic su **… (puntini di sospensione)** accanto al campo **Script** e digitare lo script inline nella finestra di dialogo **Immetti script**.  
  
    2.  **File script**: caricare il file script in un percorso BLOB e specificare il relativo **BlobName**. Se il BLOB non è presente nell'archivio o nel contenitore predefinito del cluster HDInsight, è necessario specificato **ExternalStorageAccountName** e **ExternalBlobContainer** . Per il BLOB esterno, assicurarsi che sia configurato come accessibile al pubblico.  
  
     Se vengono specificati entrambi, verrà usato il file script e lo script inline verrà ignorato.  
  
  