---
title: "Attivit&#224; di creazione cluster di Azure HDInsight | Microsoft Docs"
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
  - "sql13.dts.designer.afpcreatecltask.f1"
  - "sql14.dts.designer.afpcreatecltask.f1"
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Attivit&#224; di creazione cluster di Azure HDInsight
  L'**attività di creazione cluster di Azure HDInsight** consente a un pacchetto di SSIS di creare un cluster Azure HDInsight nella sottoscrizione di Azure specificata.  
  
 L'**attività di creazione cluster di Azure HDInsight** è un componente del Feature Pack di SQL Server Integration Services (SSIS) per Azure per SQL Server 2016. Scaricare il Feature Pack [qui](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
> [!NOTE]  
>  -   La creazione di un nuovo cluster HDInsight richiede in genere 10 minuti.  
> -   Alla creazione ed esecuzione di un cluster HDInsight di Azure è associato un costo. Per altre informazioni, vedere l'argomento [Prezzi di HDInsight](http://azure.microsoft.com/en-us/pricing/details/hdinsight/).  
  
 Per aggiungere un'**attività di creazione cluster di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all'**editor dell'attività di creazione cluster di Azure HDInsight**.  
  
 La tabella seguente fornisce una descrizione dei campi di questa finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Description**|  
|AzureSubscriptionConnection|Consente di selezionare un'istanza di Gestione connessioni esistente per una sottoscrizione di Azure oppure di creare una nuova istanza che fa riferimento a una sottoscrizione di Azure che ospita il cluster HDInsight.|  
|AzureStorageConnection|Selezionare una gestione connessione di archiviazione di Azure esistente o crearne una nuova che si riferisca a un Account di archiviazione Azure che sarà associato al cluster HDInsight.|  
|Percorso|Specificare il percorso del cluster HDInsight. Il cluster deve essere creato nella stessa posizione di archiviazione di Azure.|  
|ClusterName|Specificare un nome per il cluster HDInsight da creare.|  
|ClusterSize|Specificare il numero di nodi da includere nel cluster.|  
|BlobContainer|Specificare il nome del contenitore di archiviazione predefinito associato al cluster HDInsight.|  
|UserName|Specificare il nome dell'utente che ha accesso al cluster.|  
|Password|Specificare la password per l'utente.|  
|FailIfExists|Specificare se l'attività non dovrà riuscire se il cluster esiste già.|  
  
> [!NOTE]  
>  Il percorso del cluster HDInsight e dell'archiviazione di Azure deve essere lo stesso.  
  
  