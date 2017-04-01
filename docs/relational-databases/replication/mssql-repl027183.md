---
title: "MSSQL_REPL027183 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL027183 - errore"
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027183
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|27183|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Impossibile enumerare le modifiche negli articoli con filtri di riga con parametri. Se il problema persiste, aumentare il timeout per le query per questo processo, ridurre il periodo di memorizzazione per la pubblicazione e migliorare gli indici delle tabelle pubblicate.|  
  
## Spiegazione  
 Questo errore viene generato se si verifica un timeout dell'agente di merge durante l'elaborazione delle modifiche in una pubblicazione filtrata. Il timeout potrebbe essere provocato da uno dei problemi seguenti:  
  
-   Mancato uso dell'ottimizzazione delle partizioni pre-calcolate.  
  
-   Frammentazione dell'indice nelle colonne utilizzate per il filtraggio.  
  
-   Tabelle di metadati di merge di grandi dimensioni, ad esempio **MSmerge_tombstone**, **MSmerge_contents**, e **MSmerge_genhistory**.  
  
-   Tabelle filtrate non unite in join in una chiave univoca e filtri join che coinvolgono un gran numero di tabelle.  
  
## Azione dell'utente  
 Per risolvere il problema:  
  
-   Aumentare il valore di **- QueryTimeOut** problemi di parametro per l'agente di Merge consentire l'elaborazione di continuare mentre si risolve sottostante che provoca l'errore. I parametri degli agenti possono essere specificati nei profili agente e dalla riga di comando. Per altre informazioni, vedere:  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Visualizzare e modificare i parametri di prompt dei comandi dell'agente di replica & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concetti di file eseguibili dell'agente replica](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Se possibile, utilizzare l'ottimizzazione delle partizioni pre-calcolate. Questa ottimizzazione viene utilizzata per impostazione predefinita se vengono soddisfatti alcuni requisiti di pubblicazione. Per ulteriori informazioni su questi requisiti, vedere [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md). Se la pubblicazione non soddisfa questi requisiti, è necessario prendere in considerazione l'eventualità di riprogettare la pubblicazione.  
  
-   Specificare la minima impostazione possibile per il periodo di memorizzazione della pubblicazione, poiché la replica non è in grado di eliminare i metadati dei database di pubblicazione e sottoscrizione prima della scadenza del periodo di memorizzazione. Per altre informazioni, vedere [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   Come parte della manutenzione della replica di tipo merge, verificare occasionalmente l'aumento delle tabelle di sistema associate alla replica di tipo merge: **MSmerge_contents**, **MSmerge_genhistory**, e **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, e **MSmerge_past_partition_mappings**. Reindicizzare periodicamente queste tabelle. Per ulteriori informazioni, vedere [riorganizzazione e ricompilazione degli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Verificare che le colonne utilizzate per il filtraggio siano indicizzate correttamente e, se necessario, ricompilare tali indici. Per ulteriori informazioni, vedere [riorganizzazione e ricompilazione degli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Impostare il **join_unique_key** proprietà per i filtri di join basati su colonne univoche. Per ulteriori informazioni, vedere [filtri Join](../../relational-databases/replication/merge/join-filters.md).  
  
-   Limitare il numero massimo di tabelle nella gerarchia dei filtri di join. Se si generano filtri di join di cinque o più tabelle, considerare altre soluzioni: non filtrare tabelle piccole, non soggette a modifica o tabelle che fungono principalmente da tabelle di ricerca. Utilizzare i filtri di join solo tra tabelle che devono essere partizionate tra diverse sottoscrizioni.  
  
-   Apportare un numero minore di modifiche sulle tabelle filtrate tra le sincronizzazioni, oppure eseguire l'agente di merge con maggiore frequenza. Per ulteriori informazioni sulle pianificazioni di sincronizzazione di impostazione, vedere [specificare pianificazioni di sincronizzazione](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  