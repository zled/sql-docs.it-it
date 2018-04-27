---
title: Attività File system Hadoop | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: control-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ssis.designer.hadoopfiletask.f1
ms.assetid: 594aaf5d-7703-4788-897d-fb95aca798c5
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b963428b347e86b10f8110b21c95b32f1c10eea0
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="hadoop-file-system-task"></a>Attività File system Hadoop
  L'attività File system Hadoop consente a un pacchetto SSIS di copiare file da, a o all'interno di un cluster Hadoop.  
  
 Per aggiungere un'attività File system Hadoop, trascinarla e rilasciarla nella finestra di progettazione. Fare doppio clic sull'attività o fare clic con il pulsante destro del mouse e scegliere **Modifica**per aprire la finestra di dialogo **Editor attività File system Hadoop** .  
  
 ![Editor attività File system Hadoop](../../integration-services/control-flow/media/hadoop-filesystem-task.png "Editor attività File system Hadoop")  
  
## <a name="options"></a>Opzioni  
 Configurare le opzioni seguenti nella finestra di dialogo **Editor attività File system Hadoop** .  
  
|Campo|Description|  
|-----------|-----------------|  
|**Connessione Hadoop**|Specificare un'istanza esistente di Gestione connessione Hadoop o crearne una nuova. Questa istanza di Gestione connessione indica dove sono ospitati i file di destinazione.|  
|**Percorso del file Hadoop**|Specificare il percorso file o directory in HDFS.|  
|**Tipo di file Hadoop**|Specificare se l'oggetto del File system HDFS è un file o una directory.|  
|**Sovrascrivere la destinazione**|Specificare se sovrascrivere il file di destinazione, se già presente.|  
|**Operazione**|Specificare l'operazione. Le operazioni disponibili sono **CopyToHDFS**, **CopyFromHDFS**e **CopyWithinHDFS**.|  
|**Connessione al file locale**|Specificare un'istanza esistente di Gestione connessione file o crearne una nuova. Questa istanza di Gestione connessione indica dove sono ospitati i file di origine.|  
|**Ricorsivo**|Specificare se copiare in modo ricorsivo tutte le sottocartelle.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione connessione Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Gestione connessione file](../../integration-services/connection-manager/file-connection-manager.md)  
  
  
