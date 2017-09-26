---
title: "Attività di Cluster Azure HDInsight Delete | Documenti Microsoft"
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
- sql13.dts.designer.afpdelcltask.f1
- sql14.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f98b69e8bd3b2e78f6dd20a19ca17a83a834c3b3
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-delete-cluster-task"></a>Attività di eliminazione cluster di Azure HDInsight
Il **attività di Azure HDInsight eliminazione Cluster** consente a un pacchetto SSIS di eliminare un cluster HDInsight di Azure nel gruppo di risorse e di sottoscrizione Azure specificato.
  
Il **attività di Azure HDInsight eliminazione Cluster** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]
> L'eliminazione di un cluster HDInsight può richiedere 10 ~ 20 minuti.  
  
Per aggiungere un' **attività di eliminazione cluster di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività di eliminazione cluster di Azure HDInsight** .  
  
Nella tabella seguente fornisce una descrizione per i campi nella finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Description**|  
|AzureResourceManagerConnection|Selezionare una gestione connessione Gestione risorse Azure esistente o crearne uno nuovo che verrà utilizzato per eliminare il cluster HDInsight.|
|ID sottoscrizione|Specificare l'ID della sottoscrizione, che il cluster HDInsight.|
|Gruppo di risorse|Specificare il gruppo di risorse di Azure che il cluster HDInsight.|
|ClusterName|Consente di specificare il nome del cluster da eliminare.|  
|FailIfNotExists|Consente di indicare se l'attività deve avere esito negativo se il cluster non esiste.|

