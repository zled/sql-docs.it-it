---
title: "Attività Pig di Azure HDInsight | Documenti Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afppigtask.f1
- sql14.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9874b119b634966b146f8fa9d22c016bcd91617b
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-pig-task"></a>Attività Pig di Azure HDInsight
Usare l' **attività Pig di Azure HDInsight** per eseguire uno script Pig in un cluster di Azure HDInsight.
     
Per aggiungere un' **attività Pig di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività Pig di Azure HDInsight** .  
  
Il **attività Pig di Azure HDInsight** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 L'elenco seguente contiene i campi di questa finestra di dialogo.  
  
1.  Per il **HDInsightConnection** campo, selezionare una gestione connessione HDInsight di Azure esistente o creare un nuovo oggetto che fa riferimento al cluster HDInsight di Azure usato per eseguire lo script.
  
2.  Per il **AzureStorageConnection** campo, selezionare una gestione connessione di archiviazione Azure esistente o creare un nuovo oggetto che fa riferimento all'Account di archiviazione di Azure associato al cluster. Questo è necessario solo se si desidera scaricare i log di output e l'errore di esecuzione dello script.
 
3.  Per il **BlobContainer** , specificare il nome del contenitore di archiviazione associato al cluster. Questo è necessario solo se si desidera scaricare i log di output e l'errore di esecuzione dello script.
  
4.  Per il **LocalLogFolder** campo, specificare la cartella in cui verranno scaricati i log di output e l'errore di esecuzione dello script. Questo è necessario solo se si desidera scaricare i log di output e l'errore di esecuzione dello script.   
  
5.  Esistono due modi per specificare lo script Pig da eseguire:
  
    1.  **Script inline**: specificare il **Script** campo digitando nella riga di script da eseguire nel **Immetti Script** la finestra di dialogo.
  
    2.  **File di script**: caricare il file di script in archiviazione Blob di Azure e specificare il **BlobName** campo. Se il blob non è incluso nell'account di archiviazione predefinito o nel contenitore associato al cluster HDInsight, il **ExternalStorageAccountName** e **ExternalBlobContainer** campi devono essere specificati. Per un blob esterno, assicurarsi che sia configurato come pubblicamente accessibile.  
  
     Se vengono specificati entrambi, verrà utilizzato il file di script e lo script inline verrà ignorato.

