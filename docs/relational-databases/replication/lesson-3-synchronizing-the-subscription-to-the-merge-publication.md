---
title: 'Lezione 3: Sincronizzazione della sottoscrizione con la pubblicazione di tipo merge | Microsoft Docs'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2f80d0e6e39bea34899501368e7c7dfb693be1c6
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Lezione 3: Sincronizzazione della sottoscrizione con la pubblicazione di tipo merge
In questa lezione verrà avviato l'agente di merge per inizializzare la sottoscrizione con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. È inoltre necessario eseguire questa procedura per la sincronizzazione con il server di pubblicazione. Per eseguire questa lezione è necessario aver completato la lezione precedente [Lezione 2: Creazione di una sottoscrizione per una pubblicazione di tipo merge](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Per avviare la sincronizzazione e inizializzare la sottoscrizione  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi espandere la cartella **Replica** .  
  
2.  Nella cartella **Sottoscrizioni locali** fare clic con il pulsante destro del mouse sulla sottoscrizione nel database **SalesOrdersReplica** e quindi scegliere **Visualizza stato sincronizzazione**.  
  
3.  Fare clic su **Avvia** per inizializzare la sottoscrizione.  
  
## <a name="next-steps"></a>Passaggi successivi  
In questo modo è stato eseguito l'agente di merge per l'avvio della sincronizzazione e l'inizializzazione della sottoscrizione. È anche possibile inserire, aggiornare o eliminare dati nelle tabelle **SalesOrderHeader** o **SalesOrderDetail** nel server di pubblicazione o nel Sottoscrittore, ripetere questa procedura quando è disponibile la connettività di rete per sincronizzare i dati tra il server di pubblicazione e il Sottoscrittore e quindi eseguire query nelle tabelle **SalesOrderHeader** o **SalesOrderDetail** nell'altro server per visualizzare le modifiche replicate.  
  
Questa lezione completa l'esercitazione Replica di dati con client mobili. Per un'esercitazione simile che usa la replica transazionale, vedere [Esercitazione: Replica di dati tra server con connessione continua](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>Vedere anche  
[Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Sincronizzare i dati](../../relational-databases/replication/synchronize-data.md)  
[Sincronizzazione di una sottoscrizione pull](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  

