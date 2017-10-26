---
title: Aggiornare i dati in Monitoraggio replica | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7b58ebcc0ce0f46fd2818ae87f8093da1c3bb086
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="refresh-data-in-replication-monitor"></a>Aggiornamento dei dati in Monitoraggio replica
  In Monitoraggio replica è possibile aggiornare automaticamente o manualmente la finestra principale e le finestre dei dettagli, ovvero le finestre avviate dalla finestra principale. Per aggiornare manualmente una finestra, premere F5. Per impostazione predefinita, la finestra principale viene aggiornata automaticamente ogni cinque secondi. È possibile personalizzare la frequenza di ogni server di pubblicazione.  
  
 I dati visualizzati in Monitoraggio replica provengono da query eseguite nella cache. Per informazioni sul rapporto tra la cache e l'aggiornamento di Monitoraggio replica, vedere [Memorizzazione nella cache, aggiornamento e prestazioni di Monitoraggio replica](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md). Per informazioni sull'avvio di Monitoraggio replica, vedere [Avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a>Per impostare le opzioni di aggiornamento di Monitoraggio replica  
  
1.  Fare clic con il pulsante destro del mouse su un server di pubblicazione nel riquadro sinistro di Monitoraggio replica e quindi scegliere **Impostazioni server di pubblicazione**.  
  
2.  Nella finestra di dialogo **Impostazioni server di pubblicazione** , impostare le opzioni **Aggiornamento automatico** e **Frequenza di aggiornamento** . L'impostazione **Aggiornamento automatico** è valida per la finestra principale di Monitoraggio replica. L'impostazione **Frequenza di aggiornamento** è valida anche per le finestre dei dettagli sulle quali è stato impostato l'aggiornamento automatico. Le modifiche apportate all'impostazione avranno effetto sulle finestre dei dettagli solo alla loro successiva apertura.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a>Per impostare l'aggiornamento automatico di una finestra dei dettagli  
  
1.  Aprire una finestra dei dettagli in Monitoraggio replica. Esempio:  
  
    1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
    2.  Fare clic sulla scheda **Tutte le sottoscrizioni** .  
  
    3.  Fare clic con il pulsante destro del mouse su una sottoscrizione e quindi scegliere **Visualizza dettagli**.  
  
2.  Nella finestra dei dettagli **Sottoscrizione \<NomeSottoscrizione>** fare clic su **Azione** e quindi scegliere **Aggiornamento automatico**. La frequenza di aggiornamento viene determinata dall'impostazione **Frequenza di aggiornamento** nella finestra di dialogo **Impostazioni server di pubblicazione** .  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  

