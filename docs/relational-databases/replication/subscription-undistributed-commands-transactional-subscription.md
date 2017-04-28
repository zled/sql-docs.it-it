---
title: Sottoscrizione, Comandi non distribuiti (sottoscrizione transazionale) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3986838ebcbb9f5ed787c974b82e9a87f2a43a29
ms.lasthandoff: 04/11/2017

---
# <a name="subscription-undistributed-commands-transactional-subscription"></a>Sottoscrizione, Comandi non distribuiti (sottoscrizione transazionale)
  La scheda **Comandi non distribuiti** visualizza informazioni sul numero di comandi nel database di distribuzione che non sono stati recapitati al Sottoscrittore selezionato e il tempo previsto per il recapito di tali comandi. Per informazioni sulla visualizzazione dei comandi nel database di distribuzione, vedere [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md).  
  
## <a name="options"></a>Opzioni  
 **Numero di comandi nel database di distribuzione in attesa di essere applicati al Sottoscrittore**  
 Numero di comandi nel database di distribuzione che non sono stati recapitati al Sottoscrittore selezionato. Un comando è composto da un'istruzione DDL (Data Definition Language) o da un'istruzione DML (Data Manipulation Language) Transact-SQL.  
  
 **Tempo previsto per l'applicazione di questi comandi, sulla base delle prestazioni passate**  
 Tempo stimato per il recapito dei comandi al Sottoscrittore. Se questo valore è maggiore del tempo necessario per generare uno snapshot e applicarlo al Sottoscrittore, potrebbe risultare conveniente reinizializzare il Sottoscrittore. Per altre informazioni, vedere [Reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Monitorare le prestazioni con Monitoraggio replica](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
