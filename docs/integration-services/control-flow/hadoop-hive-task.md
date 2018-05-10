---
title: Attività Hive Hadoop | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: control-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hadoophivetask.f1
ms.assetid: 10ff37c0-9f3f-442a-889b-c351afbdc74c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2df3cf58c2b8140870ca39b03c75abf2e077928e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="hadoop-hive-task"></a>Attività Hive Hadoop
  Usare l'attività Hive Hadoop per eseguire script Hive in un cluster Hadoop.  
  
 Per aggiungere un'attività Hive Hadoop, trascinarla e rilasciarla nella finestra di progettazione. Fare doppio clic sull'attività o fare clic con il pulsante destro del mouse e scegliere **Modifica**per aprire la finestra di dialogo **Editor attività Hive Hadoop** .  
  
 ![Editor attività Hive Hadoop](../../integration-services/control-flow/media/hadoop-hive-task.png "Editor attività Hive Hadoop")  
  
## <a name="options"></a>Opzioni  
 Configurare le opzioni seguenti nella finestra di dialogo **Editor attività Hive Hadoop** .  
  
|Campo|Description|  
|-----------|-----------------|  
|**Connessione Hadoop**|Specificare un'istanza esistente di Gestione connessione Hadoop o crearne una nuova. Questa istanza di Gestione connessione indica dove è ospitato il servizio WebHCat.|  
|**SourceType**|Specificare il tipo di origine della query. I valori disponibili sono **ScriptFile** e **DirectInput**.|  
|**InlineScript**|Quando il valore di **SourceType** è **DirectInput**, specificare lo script Hive.|  
|**HadoopScriptFilePath**|Quando il valore di **SourceType** è **ScriptFile**, specificare il percorso del file di script in Hadoop.|  
|**TimeoutInMinutes**|Specificare un valore di timeout in minuti. Il processo Hadoop viene interrotto se non è stato completato prima del timeout. Specificare 0 per pianificare il processo Hadoop in modo che sia eseguito in modo asincrono.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione connessione Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  
