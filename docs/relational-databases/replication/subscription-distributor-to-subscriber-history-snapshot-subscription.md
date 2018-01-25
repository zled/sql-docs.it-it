---
title: Sottoscrizione, Cronologia database di distribuzione - Sottoscrittore (sottoscrizione snapshot) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.monitor.subscription.pubtodist.snapshot.f1
ms.assetid: d3575964-f287-4bcf-8d2e-f81a33141b25
caps.latest.revision: "20"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9c11b141c7448c215f2bf0a1fe292569db1e11a
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="subscription-distributor-to-subscriber-history-snapshot-subscription"></a>Sottoscrizione, Cronologia server di distribuzione - Sottoscrittore (sottoscrizione snapshot)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] La scheda **Cronologia server di distribuzione - Sottoscrittore** mostra informazioni dettagliate sull'agente di distribuzione, tra cui lo stato, la cronologia, i messaggi informativi ed eventuali messaggi di errore.  
  
## <a name="options"></a>Opzioni  
 Scegliere le sessioni dell'agente di distribuzione da visualizzare dal menu **Visualizza** e quindi selezionare una sessione specifica nella griglia con etichetta **Sessioni dell'agente di distribuzione**. Nella griglia con etichetta **Azioni nella sessione selezionata**verranno visualizzate informazioni dettagliate sulla sessione selezionata. Se la sessione selezionata è terminata con un errore, verrà inoltre visualizzata l'area di testo con etichetta **Messaggio o dettagli errore della sessione selezionata** .  
  
 **Visualizza**  
 Consente di selezionare le sessioni dell'agente di distribuzione da visualizzare.  
  
 **Stato**  
 Stato dell'agente di distribuzione. Nell'elenco seguente vengono indicati i valori di stato possibili:  
  
-   Errore  
  
-   Completato  
  
-   Nuovo tentativo in corso  
  
-   In esecuzione  
  
 **Start Time**  
 Ora di inizio della sessione.  
  
 **Ora fine**  
 Ora di fine della sessione. Se l'agente non è arrestato, questo campo è vuoto.  
  
 **Durata**  
 Periodo di tempo durante il quale l'agente di distribuzione è stato eseguito in questa sessione. Il valore di durata rappresenta il tempo trascorso se l'agente è ancora in esecuzione e la durata totale della sessione se la sessione dell'agente è terminata.  
  
 **Messaggio di errore**  
 Se una sessione è terminata con un errore, in questo campo viene visualizzato l'ultimo messaggio di errore registrato dall'agente di distribuzione. Se una sessione non è terminata con un errore, questo campo è vuoto.  
  
 **Messaggio azione**  
 Tutti i messaggi informativi e i messaggi di errore registrati dall'agente di distribuzione durante la sessione selezionata.  
  
 **Ora azione**  
 Ora di esecuzione dell'azione descritta nella colonna **Messaggio azione** .  
  
 **Messaggio o dettagli errore della sessione selezionata**  
 Area visualizzata solo se per la sessione selezionata è visualizzato il valore **Errore** nella colonna **Stato** . In questa area di testo vengono visualizzate informazioni dettagliate sull'errore e viene indicato il comando di cui è stata tentata l'esecuzione quando si è verificato l'errore. Sono inoltre disponibili collegamenti a contenuto aggiuntivo correlato all'errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
