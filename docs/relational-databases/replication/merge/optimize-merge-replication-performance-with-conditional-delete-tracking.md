---
title: "Ottimizzazione delle prestazioni della replica di tipo merge con il rilevamento condizionale delle eliminazioni | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rilevamento condizionale di eliminazioni [replica di SQL Server]"
  - "replica di tipo merge [replica di SQL Server], rilevamento condizionale di eliminazioni"
  - "articoli [replica di SQL Server], rilevamento condizionale di eliminazioni"
ms.assetid: 58f120a3-ea3a-4e97-93f0-0eb4e580ecf2
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Ottimizzazione delle prestazioni della replica di tipo merge con il rilevamento condizionale delle eliminazioni
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Con la replica di tipo merge è possibile specificare che le eliminazioni per uno o più articoli non devono essere rilevate dai trigger di replica e dalle tabelle di sistema. Se si specifica questa opzione per un articolo, le eliminazioni non vengono rilevate o replicate dal server di pubblicazione o da qualsiasi Sottoscrittore. Questa opzione è disponibile per il supporto di numerosi scenari applicativi e per offrire l'ottimizzazione delle prestazioni, nei casi in cui la replica delle eliminazioni non è necessaria o desiderata. Il miglioramento delle prestazioni avviene per tre motivi: non vengono archiviati i metadati delle eliminazioni, le eliminazioni non vengono enumerate durante la sincronizzazione e, infine, non vengono replicate nel Sottoscrittore e applicate allo stesso.  
  
> [!NOTE]  
>  Per utilizzare questo tipo di articoli è necessario che il livello di compatibilità della pubblicazione sia impostato almeno su 90RTM.  
  
 Questa opzione può essere specificata alla creazione della pubblicazione oppure attivata e disattivata se un'applicazione richiede la replica di alcune eliminazioni e non di altre, ad esempio eliminazioni batch. Gli esempi seguenti illustrano le modalità di utilizzo di questa opzione in un'applicazione.  
  
-   Un'applicazione per una forza vendita mobile in genere contiene tabelle, ad esempio **SalesOrderHeader**, **SalesOrderDetail** e **prodotto**. Gli ordini vengono immessi nel Sottoscrittore e poi replicati nel server di pubblicazione, che spesso assicura i dati a un sistema di evasione degli ordini. Molti lavoratori mobili utilizzano dispositivi palmari che hanno una capacità di archiviazione limitata: quando l'ordine viene ricevuto nel server di pubblicazione, può essere eliminato nel Sottoscrittore. L'eliminazione non viene propagata al server di pubblicazione, perché l'ordine è ancora attivo nel sistema.  
  
     In questo scenario, le eliminazioni non verrebbero rilevate per il **SalesOrderHeader** e **SalesOrderDetail** tabelle. Verrebbero invece rilevate per il **prodotto** tabella, perché se un prodotto viene eliminato nel server di pubblicazione, l'eliminazione deve essere inviato al server di sottoscrizione per mantenere aggiornato l'elenco dei prodotti.  
  
-   Un'applicazione potrebbe archiviare i dati cronologici in una tabella, ad esempio **TransactionHistory**, che vengono periodicamente eliminati i record meno recenti rispetto a un anno. La tabella potrebbe essere filtrata in modo che i Sottoscrittori ricevano solo i dati delle transazioni del mese corrente. Le eliminazioni batch mensili del server di pubblicazione, con cui vengono eliminati i dati più vecchi, non interessano i Sottoscrittori, ma verrebbero comunque rilevate ed enumerate per impostazione predefinita.  
  
     In questo scenario, prima che abbia luogo l'elaborazione batch, sarebbe possibile arrestare l'attività del sistema e disabilitare il rilevamento delle eliminazioni dall'applicazione. Al termine dell'elaborazione, sarebbe possibile riabilitare la rilevazione.  
  
> [!IMPORTANT]  
>  Se nel server di pubblicazione prosegue l'attività, è necessario verificare che le eliminazioni che dovrebbero essere propagate ai Sottoscrittori non abbiano luogo mentre il rilevamento delle eliminazioni è disabilitato.  
  
 **Per specificare di non rilevare le eliminazioni**  
  
-   Replica [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming: [specificare che elimina dovrebbe non essere rilevati per articoli di Merge & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/publish/specify that deletes should not be tracked for merge articles.md)  
  
## Vedere anche  
 [Opzioni degli articoli per la replica di tipo merge](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Ottimizzazione delle prestazioni della replica di tipo merge con gli articoli di solo download](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)  
  
  