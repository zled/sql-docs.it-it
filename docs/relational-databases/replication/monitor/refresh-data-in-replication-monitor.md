---
title: "Aggiornamento dei dati in Monitoraggio replica | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aggiornamento di dati"
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Aggiornamento dei dati in Monitoraggio replica
  In Monitoraggio replica è possibile aggiornare automaticamente o manualmente la finestra principale e le finestre dei dettagli, ovvero le finestre avviate dalla finestra principale. Per aggiornare manualmente una finestra, premere F5. Per impostazione predefinita, la finestra principale viene aggiornata automaticamente ogni cinque secondi. È possibile personalizzare la frequenza di ogni server di pubblicazione.  
  
 I dati visualizzati in Monitoraggio replica viene eseguita una query da una cache. Per informazioni sulla relazione tra la cache e aggiornamento Monitoraggio replica, vedere [la memorizzazione nella cache, aggiornamento e prestazioni di monitoraggio replica](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md). Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Per impostare le opzioni di aggiornamento di Monitoraggio replica  
  
1.  Fare doppio clic su un server di pubblicazione nel riquadro sinistro di monitoraggio replica e quindi fare clic su **Impostazioni server di pubblicazione**.  
  
2.  Nella finestra di dialogo **Impostazioni server di pubblicazione** , impostare le opzioni **Aggiornamento automatico** e **Frequenza di aggiornamento** . L'impostazione **Aggiornamento automatico** è valida per la finestra principale di Monitoraggio replica. Il **frequenza** impostazione interessa anche le finestre dei dettagli che prevedono l'aggiornamento automatico (modifica l'impostazione viene applicata solo le finestre dei dettagli aperti dopo la modifica).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Per impostare l'aggiornamento automatico di una finestra dei dettagli  
  
1.  Aprire una finestra dei dettagli in Monitoraggio replica. Esempio:  
  
    1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
    2.  Fare clic sulla scheda **Tutte le sottoscrizioni** .  
  
    3.  Fare doppio clic su una sottoscrizione e quindi fare clic su **Visualizza dettagli**.  
  
2.  Nel **sottoscrizione \< SubscriptionName>** finestra dei dettagli fare clic su **azione**, quindi fare clic su **aggiornamento automatico**. La frequenza di aggiornamento viene determinata dall'impostazione **Frequenza di aggiornamento** nella finestra di dialogo **Impostazioni server di pubblicazione** .  
  
## Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  