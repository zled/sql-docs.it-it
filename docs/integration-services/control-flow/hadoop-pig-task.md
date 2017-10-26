---
title: "Attività Pig Hadoop | Documenti Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.hadooppigtask.f1
ms.assetid: 90646316-9822-48aa-9900-295a33750780
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 816ca947c45128a996686d1269815ac909e364fe
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="hadoop-pig-task"></a>Attività Pig Hadoop
  Usare l'attività Pig Hadoop per eseguire script Pig in un cluster Hadoop.  
  
 Per aggiungere un'attività Pig Hadoop, trascinarla e rilasciarla nella finestra di progettazione. Fare doppio clic sull'attività o fare clic con il pulsante destro del mouse e scegliere **Modifica**per visualizzare la finestra di dialogo **Editor attività Pig Hadoop** .  
  
 ![Editor attività Pig Hadoop](../../integration-services/control-flow/media/hadoop-pig-task.png "Editor attività Pig Hadoop")  
  
## <a name="options"></a>Opzioni  
 Configurare le opzioni seguenti nella finestra di dialogo **Editor attività Pig Hadoop** .  
  
|Campo|Description|  
|-----------|-----------------|  
|**Connessione Hadoop**|Specificare un'istanza esistente di Gestione connessione Hadoop o crearne una nuova. Questa istanza di Gestione connessione indica dove è ospitato il servizio WebHCat.|  
|**SourceType**|Specificare il tipo di origine della query. I valori disponibili sono **ScriptFile** e **DirectInput**.|  
|**InlineScript**|Quando il valore di **SourceType** è **DirectInput**, specificare lo script Pig.|  
|**HadoopScriptFilePath**|Quando il valore di **SourceType** è **ScriptFile**, specificare il percorso del file di script in Hadoop.|  
|**TimeoutInMinutes**|Specificare un valore di timeout in minuti. Il processo Hadoop viene interrotto se non è stato completato prima del timeout. Specificare 0 per pianificare il processo Hadoop in modo che sia eseguito in modo asincrono.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione connessione Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  

