---
title: 'Lezione 3: Convalida della sottoscrizione e misurazione della latenza | Microsoft Docs'
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
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02e559d21156340da4527e2915e62efc4205eb19
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a>Lezione 3: Convalida della sottoscrizione e misurazione della latenza
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] In questa lezione verranno usati token di traccia per verificare se le modifiche vengono replicate nel Sottoscrittore e per determinare la latenza, ovvero il tempo necessario affinché una modifica apportata nel server di pubblicazione appaia nel Sottoscrittore. Per eseguire questa lezione è necessario aver completato la lezione precedente [Lezione 2: Creazione di una sottoscrizione per una pubblicazione transazionale](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>Per inserire un token di traccia e visualizzarne le informazioni  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server, fare clic con il pulsante destro del mouse sulla cartella **Replica** e scegliere **Launch Replication Monitor**(Avvia Monitoraggio replica).  
  
    Monitoraggio replica verrà avviato.  
  
2.  Espandere un gruppo del server di pubblicazione nel riquadro sinistro, espandere l'istanza del server di pubblicazione e fare clic sulla pubblicazione **AdvWorksProductTrans** .  
  
3.  Fare clic sulla scheda **Token di traccia** .  
  
4.  Fare clic su **Inserisci utilità di traccia**.  
  
5.  Visualizzare il tempo trascorso per il token di traccia nelle colonne **Dal server di pubblicazione al server di distribuzione**, **Dal server di distribuzione al Sottoscrittore**e **Latenza totale**. Il valore **In sospeso** indica che il token non ha raggiunto un determinato punto.  
  
## <a name="next-steps"></a>Next Steps  
In questa lezione sono stati utilizzati token di traccia per verificare che le modifiche apportate ai dati sono state replicate dal server di pubblicazione al Sottoscrittore. È anche possibile inserire, aggiornare o eliminare dati nella tabella **Product** nel server di pubblicazione ed eseguire query nella tabella **Product** nel Sottoscrittore per visualizzare tali modifiche dopo la replica.  
  
Questa lezione completa l'esercitazione Replica di dati tra server con connessione continua. Per un'esercitazione simile che usa la replica di tipo merge, vedere [Esercitazione: Replica di dati con client mobili](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md).  
  
## <a name="see-also"></a>Vedere anche  
[Measure Latency and Validate Connections for Transactional Replication](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
  
