---
title: Informazioni sulla pubblicazione, avvisi (pubblicazione di tipo Merge, SQL Server 2005 e versioni successive) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.merge.f1
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 099a4e4685a2eb5a77448f6230ea928adf49c2d1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073441"
---
# <a name="publication-information-warnings-merge-publication-sql-server-2005-and-later"></a>Informazioni sulla pubblicazione, Avvisi (pubblicazione di tipo merge, SQL Server 2005 e versioni successive)
  La scheda **Avvisi** è disponibile per i server di distribuzione che eseguono [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. La scheda **Avvisi** consente di eseguire le attività seguenti per la pubblicazione selezionata:  
  
-   Abilitazione di avvisi.  
  
-   Specificare valori soglia associati agli avvisi.  
  
-   Definire messaggi di avviso associati ad avvisi.  
  
## <a name="warnings-thresholds-and-alerts"></a>Avvisi, soglie e messaggi di avviso  
 Per impostazione predefinita, Monitoraggio replica visualizza avvisi per le sottoscrizioni non inizializzate, includendo lo stato **Sottoscrizione non inizializzata** come avviso nella colonna **Stato** delle pagine contenenti informazioni sulla sottoscrizione. Per le pubblicazioni di tipo merge è possibile specificare se le condizioni aggiuntive seguenti generano avvisi:  
  
-   Scadenza imminente della sottoscrizione.  
  
     Corrisponde all'opzione **Avvisa se una sottoscrizione scade entro il valore soglia**. Se il valore soglia specificato viene raggiunto o superato, lo stato della sottoscrizione viene visualizzato come **Scadenza imminente/Scaduta** , a meno che non sia necessario visualizzare un problema con una priorità più alta.  
  
-   Superamento del tempo di sincronizzazione specificato.  
  
     Corrisponde alle opzioni **Avvisa se la durata del processo di merge per le connessioni remote supera il valore soglia** e **Avvisa se la durata del processo di merge per le connessioni LAN supera il valore soglia**. È possibile impostare entrambe le soglie, ma solo una delle due viene utilizzata durante una determinata sincronizzazione. L'agente di merge applica la soglia appropriata in base al tipo di connessione.  
  
     Se il valore soglia specificato viene raggiunto o superato, lo stato della sottoscrizione viene visualizzato come **Merge con esecuzione prolungata** , a meno che non debba essere visualizzato un problema con priorità più alta.  
  
-   Impossibilità di elaborare il numero di righe specificato in un determinato intervallo di tempo.  
  
     Corrisponde alle opzioni **Avvisa se il numero di righe al secondo di cui è stato eseguito il merge per le connessioni remote è minore del valore soglia** e **Avvisa se la durata del processo di merge per le connessioni LAN supera il valore soglia**. È possibile impostare entrambe le soglie, ma solo una delle due viene utilizzata durante una determinata sincronizzazione. L'agente di merge applica la soglia appropriata in base al tipo di connessione.  
  
     Se il valore soglia specificato viene raggiunto o superato, lo stato della sottoscrizione viene visualizzato come **Prestazioni critiche** , a meno che non sia necessario visualizzare un problema con una priorità più alta.  
  
 Quando si abilita un avviso, è inoltre necessario impostare un valore soglia. Ad esempio, se si abilita l'avviso **Avvisa se la durata del processo di merge per le connessioni LAN supera il valore soglia**, impostare la lunghezza di tempo massima consentita per una sincronizzazione di tipo merge.  
  
 Oltre a visualizzare un avviso in Monitoraggio replica, il raggiungimento di un valore soglia può inoltre attivare un messaggio di avviso. Gli avvisi vengono definiti facendo clic su **Configura avvisi** e specificando le informazioni appropriate nella finestra di dialogo **Configura avvisi di replica** .  
  
## <a name="options"></a>Opzioni  
 **Abilitata**  
 Selezionare questa opzione per abilitare un avviso e specificare un valore soglia.  
  
 **Avviso**  
 Selezionare questa opzione per abilitare l'impostazione di avvisi per un determinato avviso di replica.  
  
 **Avviso**  
 Descrizione dell'avviso associato al valore soglia.  
  
 **Soglia**  
 Consente di specificare un valore per la soglia.  
  
 **Configura avvisi**  
 Selezionare una riga nella griglia **Avvisi** e fare clic su **Configura avvisi** per aprire la finestra di dialogo **Configura avvisi di replica** . Tramite questa finestra di dialogo è possibile definire un avviso associato al valore soglia e all'avviso selezionati.  
  
 **Ignora modifiche**  
 Fare clic su questo pulsante per ignorare le eventuali modifiche apportate agli avvisi e alle soglie.  
  
> [!NOTE]  
>  La scelta del pulsante **Ignora modifiche** non influisce sugli avvisi definiti nella finestra di dialogo **Configura avvisi di replica** .  
  
 **Salva modifiche**  
 Fare clic su questo pulsante per salvare le eventuali modifiche apportate agli avvisi e alle soglie.  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare Monitoraggio replica](monitor/start-the-replication-monitor.md)   
 [Visualizzare le informazioni ed eseguire attività per una pubblicazione &#40;Monitoraggio replica&#41;](monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Monitorare le prestazioni con Monitoraggio replica](monitor/monitor-performance-with-replication-monitor.md)   
 [Monitoraggio della replica](monitoring-replication.md)   
 [Impostare valori di soglia e avvisi in Monitoraggio replica](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
