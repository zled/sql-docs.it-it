---
title: "Attivit&#224; di eliminazione cluster di Azure HDInsight | Microsoft Docs"
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
  - "sql13.dts.designer.afpdelcltask.f1"
  - "sql14.dts.designer.afpdelcltask.f1"
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Attivit&#224; di eliminazione cluster di Azure HDInsight
  L'**attività di eliminazione cluster di Azure HDInsight** consente a un pacchetto di SSIS di eliminare un cluster Azure HDInsight nella sottoscrizione di Azure specificata.  
  
 L'**attività di eliminazione cluster di Azure HDInsight** è un componente del Feature Pack di SQL Server Integration Services (SSIS) per Azure per SQL Server 2016. Scaricare il Feature Pack [qui](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
> [!NOTE]  
>  L'eliminazione di un cluster HDInsight richiede in genere 10 minuti.  
  
 Per aggiungere un'**attività di eliminazione cluster di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all'**editor dell'attività di eliminazione cluster di Azure HDInsight**.  
  
 La tabella seguente fornisce una descrizione dei campi della finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Description**|  
|AzureSubscriptionConnection|Consente di selezionare un'istanza di Gestione connessioni esistente per una sottoscrizione di Azure oppure di creare una nuova istanza che fa riferimento a una sottoscrizione di Azure che ospita il cluster HDInsight.|  
|ClusterName|Consente di specificare il nome del cluster da eliminare.|  
|FailIfNotExists|Consente di indicare se l'attività deve avere esito negativo se il cluster non esiste.|  
  
  