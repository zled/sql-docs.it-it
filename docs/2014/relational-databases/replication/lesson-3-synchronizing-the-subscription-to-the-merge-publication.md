---
title: 'Lezione 3: Sincronizzazione della sottoscrizione con la pubblicazione di tipo merge | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: af7e1e4c59cfc624e9e83a24fcbb6095a20d2dda
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077550"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Lezione 3: Sincronizzazione della sottoscrizione con la pubblicazione di tipo merge
  In questa lezione verrà avviato l'agente di merge per inizializzare la sottoscrizione con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. È inoltre necessario eseguire questa procedura per la sincronizzazione con il server di pubblicazione. Per eseguire questa lezione è necessario aver completato la lezione precedente [Lezione 2: Creazione di una sottoscrizione per una pubblicazione di tipo merge](lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Per avviare la sincronizzazione e inizializzare la sottoscrizione  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi espandere la cartella **Replica** .  
  
2.  Nella cartella **Sottoscrizioni locali** fare clic con il pulsante destro del mouse sulla sottoscrizione nel database **SalesOrdersReplica** e quindi scegliere **Visualizza stato sincronizzazione**.  
  
3.  Fare clic su **Avvia** per inizializzare la sottoscrizione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 In questo modo è stato eseguito l'agente di merge per l'avvio della sincronizzazione e l'inizializzazione della sottoscrizione. È anche possibile inserire, aggiornare o eliminare dati nelle tabelle **SalesOrderHeader** o **SalesOrderDetail** nel server di pubblicazione o nel Sottoscrittore, ripetere questa procedura quando è disponibile la connettività di rete per sincronizzare i dati tra il server di pubblicazione e il Sottoscrittore e quindi eseguire query nelle tabelle **SalesOrderHeader** o **SalesOrderDetail** nell'altro server per visualizzare le modifiche replicate.  
  
 Questa lezione completa l'esercitazione Replica di dati con client mobili. Per un'esercitazione simile che usa la replica transazionale, vedere [Esercitazione: Replica di dati tra server con connessione continua](tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Inizializzare una sottoscrizione con uno snapshot](initialize-a-subscription-with-a-snapshot.md)   
 [Sincronizzare i dati](synchronize-data.md)   
 [Sincronizzazione di una sottoscrizione pull](synchronize-a-pull-subscription.md)  
  
  