---
title: 'Lezione 3: Sincronizzazione della sottoscrizione con la pubblicazione di tipo merge | Microsoft Docs'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: "14"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5e0712662eb839270a8932e6059551b45af3f7a2
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Lezione 3: Sincronizzazione della sottoscrizione con la pubblicazione di tipo merge
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] In questa lezione verrà avviato l'agente di merge per inizializzare la sottoscrizione con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. È inoltre necessario eseguire questa procedura per la sincronizzazione con il server di pubblicazione. Per eseguire questa lezione è necessario aver completato la lezione precedente [Lezione 2: Creazione di una sottoscrizione per una pubblicazione di tipo merge](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Per avviare la sincronizzazione e inizializzare la sottoscrizione  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi espandere la cartella **Replica** .  
  
2.  Nella cartella **Sottoscrizioni locali** fare clic con il pulsante destro del mouse sulla sottoscrizione nel database **SalesOrdersReplica** e quindi scegliere **Visualizza stato sincronizzazione**.  
  
3.  Fare clic su **Avvia** per inizializzare la sottoscrizione.  
  
## <a name="next-steps"></a>Next Steps  
In questo modo è stato eseguito l'agente di merge per l'avvio della sincronizzazione e l'inizializzazione della sottoscrizione. È anche possibile inserire, aggiornare o eliminare dati nelle tabelle **SalesOrderHeader** o **SalesOrderDetail** nel server di pubblicazione o nel Sottoscrittore, ripetere questa procedura quando è disponibile la connettività di rete per sincronizzare i dati tra il server di pubblicazione e il Sottoscrittore e quindi eseguire query nelle tabelle **SalesOrderHeader** o **SalesOrderDetail** nell'altro server per visualizzare le modifiche replicate.  
  
Questa lezione completa l'esercitazione Replica di dati con client mobili. Per un'esercitazione simile che usa la replica transazionale, vedere [Esercitazione: Replica di dati tra server con connessione continua](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>Vedere anche  
[Inizializzare una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Sincronizzare i dati](../../relational-databases/replication/synchronize-data.md)  
[Sincronizzazione di una sottoscrizione pull](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  
