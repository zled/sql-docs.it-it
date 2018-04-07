---
title: Disponibilità elevata di sistema della piattaforma Analitica
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: Viene descritto come Analitica piattaforma di strumenti analitici è progettato per la disponibilità elevata.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 5ab245e9-0316-4d25-a626-4745ce856925
caps.latest.revision: 9
ms.openlocfilehash: 9fd057a4cd673f06034e0093ca93be7ceaf345ea
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="analytics-platform-system-high-availability"></a>Disponibilità elevata di sistema della piattaforma Analitica
Viene descritto come Analitica piattaforma di strumenti analitici è progettato per la disponibilità elevata.  
  
## <a name="high-availability-architecture"></a>Architettura a disponibilità elevata  
![Architettura dello strumento](media/appliance-architecture.png "architettura dello strumento")  
  
## <a name="network"></a>Rete  
La disponibilità di rete, il dispositivo di punti di accesso dispone di due reti InfiniBand. Se una delle reti InfiniBand diventa inattiva, l'altro è ancora disponibile. Inoltre, Active Directory ha replicato i controller di dominio per risolvere le richieste in entrata alla rete InfiniBand corretta.  
  
Per ulteriori informazioni, vedere [schede di rete InfiniBand configurare](configure-infiniband-network-adapters.md).  
  
## <a name="storage"></a>Archiviazione  
Per la protezione dei dati, i punti di accesso utilizza RAID 1 mirroring per mantenere due copie di tutti i dati utente. Quando un disco ha esito negativo, il sistema hardware consente di ricompilare i dati in un disco di riserva e imposta un avviso che si verifica un errore di disco.  
  
Per mantenere i dati disponibili in linea, APS Usa spazi di archiviazione di Windows e i volumi condivisi cluster per gestire l'archiviazione collegata direttamente i dischi dati utente. È un pool di archiviazione per ogni unità di scala di dati organizzati in volumi condivisi del Cluster che sono disponibili per gli host del nodo di calcolo tramite punti di montaggio.  
  
Per garantire il pool di archiviazione in linea, ogni host nell'unità di scala di dati dispone di una macchina virtuale ISCSI che esegue il failover. Questa architettura è importante perché se un host non riesce, i dati sono ancora accessibili tramite degli altri host nell'unità di scala di dati.  
  
## <a name="hosts"></a>Host  
Per la disponibilità dell'host, tutti gli host vengono configurati in un Cluster di Failover di Windows. Ogni rack dispone di un host passivo. Facoltativamente il primo rack, che controlla l'infrastruttura di dispositivo e di SQL Server Parallel Data Warehouse (PDW), può avere un secondo host passivo. Se un host non riesce, le macchine virtuali che sono configurate per il failover, eseguirà il failover a un host passivo disponibile.  
  
## <a name="pdw-nodes-and-appliance-fabric"></a>I nodi PDW e dell'infrastruttura di dispositivo  
Per la disponibilità elevata dei nodi PDW e dell'infrastruttura di dispositivo, i punti di accesso utilizza la virtualizzazione. Ciascuno dei componenti dell'infrastruttura PDW e il dispositivo viene eseguito in una macchina virtuale.  
  
Ogni macchina virtuale è definita come un ruolo del cluster di failover di Windows. Quando una macchina virtuale non riesce, il cluster viene riavviato in un host passivo disponibile. Le macchine virtuali vengono distribuite con System Center Virtual Machine Manager. Quando si verifica un failover, la macchina virtuale in esecuzione nell'host passivo è ancora in grado di accedere ai dati utente attraverso la rete InfiniBand.  
  
Il nodo controllo del codice e le macchine virtuali di nodo di calcolo sono configurate come cluster a nodo singolo. Il cluster a nodo singolo gestisce le reti InfiniBand come risorsa cluster per verificare che il cluster utilizza sempre l'IP InfiniBand attivo. Il cluster a nodo singolo gestisce i processi PDW eseguiti all'interno della macchina virtuale. Ad esempio, il cluster a nodo singolo con SQL Server e servizio lo spostamento dei dati (DMS) come risorse in modo che sia possibile avviarli nell'ordine corretto. Il nodo controllo VM controlla anche l'ordine di avvio per le altre macchine virtuali in esecuzione in host di orchestrazione.  
  
