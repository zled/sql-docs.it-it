---
title: "Inizializzazione nuovi peer (replica peer-to-peer) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.p2pwizard.init.f1"
ms.assetid: 050c00e1-78bd-4d9c-affe-40e22feb4d94
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Inizializzazione nuovi peer (replica peer-to-peer)
  La pagina **Inizializzazione nuovi peer** consente di specificare la modalità di inizializzazione dei database peer. I peer devono essere inizializzati prima di completare la procedura guidata. I peer possono essere inizializzati manualmente oppure utilizzando la funzionalità **initialize with backup** fornita dalla replica transazionale. La replica transazionale peer-to-peer non supporta l'inizializzazione dei peer tramite uno snapshot. Se peer diversi devono essere inizializzati utilizzando metodi diversi, è necessario aggiungere i peer separatamente eseguendo più volte la procedura guidata.  
  
## Opzioni  
 **Specificare il tipo di inizializzazione dei nuovi database peer**  
 È necessario che lo schema e i dati relativi a tutti gli oggetti pubblicati siano presenti in ogni peer. Selezionare una delle opzioni seguenti:  
  
-   Selezionare la prima opzione nel caso in cui lo schema relativo agli oggetti pubblicati sia stato creato manualmente oppure sia stato ripristinato un backup e non siano state apportate modifiche ai dati nel primo database di pubblicazione dal momento dell'esecuzione del backup. Se lo schema è stato creato manualmente, è necessario verificare che tutti i dati necessari siano presenti in ogni peer. Questa opzione corrisponde a un valore di **solo supporto replica** per la proprietà della sottoscrizione **sync_type**.  
  
-   Selezionare la seconda opzione nel caso in cui sia stato ripristinato un backup e siano state apportate modifiche ai dati nel primo database di pubblicazione dal momento dell'esecuzione del backup. È necessario quindi che la replica recapiti le modifiche non incluse nel backup del primo database di pubblicazione. Questa opzione corrisponde a un valore di **inizializzazione con backup** per la proprietà della sottoscrizione **sync_type**.  
  
     Quando una pubblicazione è abilitata per la replica peer-to-peer, la **allow_initialize_from_backup** è impostata la proprietà di pubblicazione. La replica inizierà immediatamente a rilevare le modifiche nel primo database di pubblicazione. Queste modifiche possono pertanto essere recapitate a un database ripristinato in uno o più peer se l'opzione **initialize with backup** è selezionata. Fare clic sui **Sfoglia** per individuare il backup utilizzato e la replica verrà letto il numero di sequenza log (LSN) dal backup. Tutte le modifiche apportate al primo database di pubblicazione a cui è associato un numero di sequenza del file di log superiore verranno recapitate a tutti i peer.  
  
     Questa opzione potrebbe non essere disponibile se si sta eseguendo la creazione o l'aggiunta in una topologia che include [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Nella tabella seguente viene indicato se l'opzione è disponibile quando si aggiunge un nodo a una topologia esistente.  
  
    |Nuovo nodo|Primo nodo|Nodi aggiuntivi|Opzione|  
    |--------------|----------------|----------------------|------------|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Disabilitata|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Nessuno|Disabilitata|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Disabilitata|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Nessuno|Abilitata|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Nessuno|Abilitata|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Abilitata|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Nessuno|Abilitata|  
  
## Vedere anche  
 [Amministrare una topologia Peer-to-Peer & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Replica transazionale peer-to-peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  