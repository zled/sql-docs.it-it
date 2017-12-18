---
title: "Attività di creazione cluster di Azure HDInsight | Microsoft Docs"
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpcreatecltask.f1
- sql14.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c92d57984e0cb929a28ab441e40341d0eb8635df
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="azure-hdinsight-create-cluster-task"></a>Attività di creazione cluster di Azure HDInsight
L' **attività di creazione cluster di Azure HDInsight** consente a un pacchetto di SSIS di creare un cluster Azure HDInsight nella sottoscrizione e nel gruppo di risorse di Azure specificati.
  
L'**attività di creazione cluster di Azure HDInsight** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]  
> - La creazione di un nuovo cluster HDInsight può richiedere da 10 a 20 minuti circa.  
> - Alla creazione ed esecuzione di un cluster HDInsight di Azure è associato un costo. Per altre informazioni, vedere [Prezzi di HDInsight](http://azure.microsoft.com/pricing/details/hdinsight/).  
  
Per aggiungere un' **attività di creazione cluster di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività di creazione cluster di Azure HDInsight** .  
  
La tabella seguente offre una descrizione dei campi della finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Description**|  
|AzureResourceManagerConnection|Selezionare un'istanza di Gestione connessioni esistente per Azure Resource Manager oppure creare una nuova istanza che verrà usata per creare il cluster HDInsight.|  
|AzureStorageConnection|Selezionare una gestione connessione di archiviazione di Azure esistente o crearne una nuova che si riferisca a un Account di archiviazione Azure che sarà associato al cluster HDInsight.|
|SubscriptionId|Specificare l'ID della sottoscrizione in cui verrà creato il cluster HDInsight.|
|ResourceGroup|Specificare il gruppo di risorse di Azure in cui verrà creato il cluster HDInsight.|
|Percorso|Specificare il percorso del cluster HDInsight. Il cluster deve essere creato nella stessa posizione specificata nell'account di Archiviazione di Microsoft Azure.|  
|ClusterName|Specificare un nome per il cluster HDInsight da creare.|  
|ClusterSize|Specificare il numero di nodi da creare nel cluster.|  
|BlobContainer|Specificare il nome del contenitore di archiviazione predefinito da associare al cluster HDInsight.|  
|UserName|Specificare il nome utente da usare per la connessione al cluster HDInsight.|  
|Password|Specificare la password da usare per la connessione al cluster HDInsight.|
|SshUserName|Specificare il nome utente usato per accedere in remoto al cluster HDInsight con SSH.|
|SshPassword|Specificare la password usata per accedere in remoto al cluster HDInsight con SSH.|
|FailIfExists|Specificare se l'attività non dovrà riuscire se il cluster esiste già.|  
  
> [!NOTE]  
> Il percorso del cluster HDInsight e dell'account di archiviazione di Azure deve essere lo stesso.
