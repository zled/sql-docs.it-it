---
title: Sottoscrizione, Cronologia sincronizzazione (sottoscrizione di tipo merge, SQL Server 2000) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 0a0deab2-1c08-4371-9681-d9403e0236cc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: acf0a3810fd53b695a9ea7f44c6766601d32733a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603509"
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2000"></a>Sottoscrizione, Cronologia sincronizzazione (Sottoscrizione di tipo merge, SQL Server 2000)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Nella scheda **Cronologia sincronizzazione** vengono visualizzate informazioni dettagliate sull'agente di merge, fra cui lo stato, la cronologia, i messaggi informativi e tutti gli eventuali messaggi di errore.  
  
## <a name="options"></a>Opzioni  
 Scegliere le sessioni dell'agente di merge da visualizzare dal menu **Visualizza** e quindi selezionare una sessione specifica nella griglia con l'etichetta **Sessioni dell'agente di merge**. Nella griglia con etichetta **Azioni nella sessione selezionata**verranno visualizzate informazioni dettagliate sulla sessione selezionata. Se la sessione selezionata è terminata con un errore, verrà inoltre visualizzata l'area di testo con etichetta **Messaggio o dettagli errore della sessione selezionata** .  
  
 **Visualizza**  
 Consente di selezionare l'agente di merge da visualizzare. L'agente di merge è in genere in esecuzione continua e potrebbe pertanto essere presente un'unica sessione da visualizzare.  
  
 **Stato**  
 Stato dell'agente di merge. Nell'elenco seguente vengono indicati i valori di stato possibili:  
  
-   Errore  
  
-   Completato  
  
-   Nuovo tentativo in corso  
  
-   In esecuzione  
  
 **Start Time**  
 Ora di inizio della sessione.  
  
 **Ora fine**  
 Ora di fine della sessione. Se l'agente non è arrestato, questo campo è vuoto.  
  
 **Durata**  
 Quantità di tempo di esecuzione dell'agente di merge nella sessione. Il valore di durata rappresenta il tempo trascorso se l'agente è ancora in esecuzione e la durata totale della sessione se la sessione dell'agente è terminata.  
  
 **Messaggio di errore**  
 Se una sessione è terminata con un errore, in questo campo viene visualizzato l'ultimo messaggio di errore registrato dall'agente di merge. Se una sessione non è terminata con un errore, questo campo è vuoto.  
  
 **Messaggio azione**  
 Tutti i messaggi informativi e di errore registrati dall'agente di merge durante la sessione selezionata.  
  
 **Ora azione**  
 Ora di esecuzione dell'azione descritta nella colonna **Messaggio azione** .  
  
 **Messaggio o dettagli errore della sessione selezionata**  
 Area visualizzata solo se per la sessione selezionata è visualizzato il valore **Errore** nella colonna **Stato** . In questa area di testo vengono visualizzate informazioni dettagliate sull'errore e viene indicato il comando di cui è stata tentata l'esecuzione quando si è verificato l'errore. Sono inoltre disponibili collegamenti a contenuto aggiuntivo correlato all'errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
