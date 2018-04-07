---
title: Alimentazione del dispositivo di punti di accesso o disattivare (Analitica piattaforma System)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2258f8e3-e7a1-4455-8a5e-10d4d15775d6
caps.latest.revision: 45
ms.openlocfilehash: 04473682d04a5b3ff26a5dec0081300d83052f09
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="power-the-aps-appliance-on-or-off"></a>Alimentazione del dispositivo di punti di accesso o disattivare
In questo argomento viene descritto come accendere o spegnere il Systemappliance piattaforma Analitica che è in esecuzione Parallel Data Warehouse e, facoltativamente, in esecuzione un'area HDInsight. Dopo un'interruzione dell'alimentazione irreversibile, utilizzare questo argomento quando si sposta un dispositivo di sistema della piattaforma Analitica o alla potenza su un dispositivo.  
  
Accensione del dispositivo e lo spegnimento non è lo stesso come l'avvio e arresto dei servizi di dispositivo. Per informazioni su tale argomento, vedere [PDW stato del servizio &#40;Analitica Platform System&#41;](pdw-services-status.md). Per informazioni su come si attiva o disattiva un SQL Server 2008 Parallel Data Warehouse, vedere il file della Guida di SQL Server 2008 Parallel Data Warehouse. Per informazioni su come si attiva o disattiva un SQL Server 2012 AU1 o AU2 Parallel Data Warehouse, vedere il file della Guida per le versioni.  
  
Quando queste istruzioni specificano la connessione a un nodo di SQL Server PDW, la connessione può essere locale usando dispositivi collegati (KVM) o remota tramite Desktop remoto. Alcune azioni devono essere fisica (accensione di un interruttore di alimentazione), mentre altri (ad esempio arresta) può essere fisico o utilizzando i comandi.  
  
Le connessioni ai nodi di SQL Server PDW è possibile stabilire utilizzando gli indirizzi IP assegnati ai nodi, o dal **HST01** computer utilizzando il **gestione Cluster di Failover** (**cluadmin.msc**) o **gestione di Hyper-V** (**virtmgmt.msc**) le applicazioni e il pulsante destro del nome del nodo.  
  
## <a name="PowerOff"></a>Spegnere il dispositivo  
  
### <a name="before-you-begin"></a>Operazioni preliminari  
Prima di spegnere il dispositivo, chiudere tutte le attività nel dispositivo. Per terminare tutte le attività:  
  
-   Utilizzare il **sessioni** della Console di amministrazione per identificare gli utenti correnti. Contattarlo e chiedergli di provvedere alla disconnessione.  
  
-   Se necessario è possibile utilizzare il **KILL** istruzione per forzare la chiusura di una connessione client. Prestare attenzione durante la terminazione di connessioni. Quando interrotta, alcuni processi transazionale, ad esempio un aggiornamento a esecuzione prolungata, attività di rollback prima di SQL Server può completare il ripristino del database. Rollback di un aggiornamento parzialmente completato o delete, può richiedere tempi lunghi.  
  
### <a name="to-power-off-the-appliance"></a>Per spegnere il dispositivo  
  
> [!WARNING]  
> Tutti i passaggi devono essere eseguiti nell'ordine esatto e ogni passaggio è necessario completare prima di eseguita il passaggio successivo, se non diversamente specificato. Eseguire i passaggi nell'ordine errato o senza attendere che ogni passaggio per completare può causare errori quando il dispositivo è acceso in un secondo momento.  
  
1.  Connettersi al nodo di controllo PDW (***PDW_region *-CTL01** ) e account di accesso con l'account di amministratore di sistema della piattaforma Analitica accessorio dominio.  
  
2.  Eseguire `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` per aprire la **Configuration Manager**.  
  
3.  In Configuration Manager nel **Parallel Data Warehouse topologia** menu, fare clic sul **stato del servizio** scheda e fare clic su **area arrestare** per arrestare i servizi PDW.  
  
4.  Se è presente un'area di HDInsight, nel **HDInsight topologia** menu, fare clic sul **stato del servizio** scheda e fare clic su **arrestare area** per arrestare i servizi di HDInsight.  
  
5.  Connettersi a ***appliance_domain *-HST01** e accedere con l'account di amministratore di dominio dello strumento.  
  
6.  Utilizzando il **gestione Cluster di Failover** connettersi il ***appliance_domain *-WFOHST01** cluster, se non automaticamente connessi e quindi nel riquadro di spostamento, fare clic su **ruoli**. Nel **ruoli** riquadro:  
  
    1.  Selezionare più tutte le macchine virtuali. Fare doppio clic su essi e selezionare **Arresta**.  
  
    2.  Attendere che tutte le macchine virtuali selezionate completamento in corso l'arresto.  
  
7.  Se è disponibile un'area HDInsight:  
  
    1.  Connettersi al cluster HDInsight. A tale scopo, fare clic su **gestione Cluster di Failover**, selezionare **Connetti al Cluster**e specificare ***appliance_domain *-WFOHST02** per il nome del cluster.  
  
    2.  Selezionare il cluster HDInsight, **ruoli**. Nel **ruoli** riquadro:  
  
        1.  Selezionare più tutte le macchine virtuali, fare doppio clic su essi e selezionare **Arresta**.  
  
        2.  Attendere che le macchine virtuali arrestare.  
  
8.  Chiudi il **gestione Cluster di Failover** dell'applicazione.  
  
9. Arrestare tutti i server tranne ***appliance_domain *-HST01**.  
  
10. Arrestare il ***appliance_domain *-HST01** server.  
  
11. Arrestare l'unità di distribuzione dell'alimentazione (PDU).  
  
## <a name="PowerOn"></a>Accensione del dispositivo  
  
### <a name="to-power-on-the-appliance"></a>Per accendere il dispositivo  
  
> [!WARNING]  
> Tutti i passaggi devono essere eseguiti nell'ordine esatto e ogni passaggio è necessario completare prima di eseguita il passaggio successivo, se non diversamente specificato. Eseguire i passaggi nell'ordine errato o senza attendere che ogni passaggio per completare può causare errori di avvio.  
  
1.  Accendere l'unità di distribuzione dell'alimentazione (PDU) e attendere che le opzioni per l'avvio automatico.  
  
2.  Accendere il ***appliance_domain *-HST01** server.  
  
3.  Accedere a ***appliance_domain *-HST01** come amministratore di dominio dello strumento.  
  
4.  Avviare il **gestione di Hyper-V** programma (**virtmgmt.msc**) e connettersi a ***appliance_domain *-HST01** se non è connesso per impostazione predefinita.  
  
    1.  Se non è possibile connettersi in base al nome perché il ***PDW_region *-AD01** è non in esecuzione, provare a connettersi usando l'indirizzo IP.  
  
    2.  Nel **macchine virtuali** riquadro individuare ***PDW_region *-AD01** e verificare che sia in esecuzione. In caso contrario, avviare la macchina virtuale e attendere che deve essere completamente avviato.  
  
5.  Accendere il resto dei server nel dispositivo.  
  
6.  Mentre in **HST01** connessi come amministratore di dominio di applicazione, scegliere **gestione di Hyper-V**:  
  
    1.  Connettersi a ***appliance_domain *-HST02**.  
  
    2.  Nel **macchine virtuali** riquadro individuare ***PDW_region *-AD02** e verificare che sia in esecuzione.  In caso contrario, avviare la macchina virtuale e attendere che deve essere completamente avviato.  
  
7.  Utilizzando il **gestione Cluster di Failover** connettersi il ***appliance_domain *-WFOHST01** cluster, se connessi non automaticamente e quindi nel **navigazione** riquadro, fare clic su **Ruoli**. Nel **ruoli** riquadro:  
  
    1.  Selezionare più tutte le macchine virtuali, fare doppio clic su essi e quindi fare clic su **avviare**.  
  
    2.  Attendere che tutte le macchine virtuali selezionate completare l'avvio prima di procedere al passaggio successivo.  
  
    3.  Se necessario per le macchine virtuali che è stato eseguito il failover, arrestarli, spostarli e riavviarle nell'host primario appropriato.  
  
8.  Se il dispositivo dispone di un'area HDInsight, connettersi al cluster HDInsight. (A tale scopo, fare clic su **gestione Cluster di Failover**, selezionare **Connetti al Cluster**e specificare ***appliance_domain *-WFOHST01** per il nome del cluster.)  
  
    1.  Selezionare il cluster HDInsight, **ruoli**. Nel **ruoli** riquadro.  
  
        1.  Selezionare più tutte le macchine virtuali, fare doppio clic su essi e selezionare **avviare**,  
  
        2.  Attendere che tutte le macchine virtuali selezionate completare l'avvio prima di procedere al passaggio successivo.  
  
        3.  Se necessario per le macchine virtuali che è stato eseguito il failover, arrestarli, spostarli e riavviarle nell'host primario appropriato.  
  
9. Disconnettersi da **HST01** se si desidera.  
  
10. Connettersi a ***PDW_region *-CTL01** utilizzando l'account di amministratore di dominio dello strumento.  
  
11. Eseguire `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` per avviare il **Configuration Manager**.  
  
12. Nel **Configuration Manager**, nel **Parallel Data Warehouse topologia** menu, fare clic sul **stato del servizio** scheda e fare clic su **avviare area**per avviare i servizi PDW.  
  
13. Se il dispositivo dispone di un'area di HDInsight, nel menu della topologia di HDInsight, fare clic su di **stato del servizio** scheda e fare clic su **area avviare** per avviare i servizi di HDInsight.  
  
### <a name="to-verify-the-appliance-health"></a>Per verificare l'integrità del dispositivo  
Dopo aver avviato il dispositivo, aprire il **Console di amministrazione** e selezionare la pagina di integrità per gli avvisi che potrebbero indicare le condizioni di errore. Per altre informazioni, vedere [monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
## <a name="see-also"></a>Vedere anche  
[Attività di gestione dello strumento &#40;Analitica Platform System&#41;](appliance-management-tasks.md)  
  
