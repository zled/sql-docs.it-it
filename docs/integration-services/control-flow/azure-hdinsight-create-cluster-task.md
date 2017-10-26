---
title: "Azure HDInsight attività di creazione Cluster | Documenti Microsoft"
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
- sql13.dts.designer.afpcreatecltask.f1
- sql14.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 71a24dc15253916c32b07e6024e2ab32514c9d39
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-create-cluster-task"></a>Attività di creazione cluster di Azure HDInsight
Il **attività di Azure HDInsight creazione Cluster** consente a un pacchetto SSIS creare un cluster HDInsight di Azure nel gruppo di risorse e di sottoscrizione Azure specificato.
  
Il **attività di Azure HDInsight creazione Cluster** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]  
> - Creazione di un nuovo cluster HDInsight può richiedere 10 ~ 20 minuti.  
> - È un costo associato alla creazione ed esecuzione di un cluster Azure HDInsight. Vedere [prezzi di HDInsight](http://azure.microsoft.com/en-us/pricing/details/hdinsight/) per informazioni dettagliate.  
  
Per aggiungere un' **attività di creazione cluster di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività di creazione cluster di Azure HDInsight** .  
  
Nella tabella seguente fornisce una descrizione dei campi in questa finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Description**|  
|AzureResourceManagerConnection|Selezionare una gestione connessione Gestione risorse Azure esistente o crearne uno nuovo che verrà utilizzato per creare il cluster HDInsight.|  
|AzureStorageConnection|Selezionare una gestione connessione di archiviazione di Azure esistente o crearne una nuova che si riferisca a un Account di archiviazione Azure che sarà associato al cluster HDInsight.|
|ID sottoscrizione|Specificare l'ID della sottoscrizione in che verrà creato il cluster HDInsight.|
|Gruppo di risorse|Specificare la risorsa di Azure gruppo il HDInsight verrà creato nel cluster.|
|Percorso|Specificare il percorso del cluster HDInsight. Il cluster deve essere creato nello stesso percorso dell'Account di archiviazione di Azure specificato.|  
|ClusterName|Specificare un nome per il cluster HDInsight da creare.|  
|ClusterSize|Specificare il numero di nodi da creare nel cluster.|  
|BlobContainer|Specificare il nome del contenitore di archiviazione predefinito da associare al cluster HDInsight.|  
|UserName|Specificare il nome utente da utilizzare per la connessione al cluster HDInsight.|  
|Password|Specificare la password da utilizzare per la connessione al cluster HDInsight.|
|SshUserName|Specificare il nome utente utilizzato per accedere in remoto al cluster HDInsight tramite SSH.|
|SshPassword|Specificare la password utilizzata per accedere in remoto al cluster HDInsight tramite SSH.|
|FailIfExists|Specificare se l'attività non dovrà riuscire se il cluster esiste già.|  
  
> [!NOTE]  
> I percorsi del cluster HDInsight e l'Account di archiviazione di Azure devono essere lo stesso.

