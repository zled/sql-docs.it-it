---
title: "MSSQL_REPL027056 | Microsoft Docs"
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
  - "MSSQL_REPL027056 - errore"
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027056
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|27056|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Impossibile modificare la cronologia di generazione in '%1'. Per risolvere il problema, riavviare la sincronizzazione con la registrazione dettagliata della cronologia e specificare un file di output in cui registrare i dati.|  
  
## Spiegazione  
 Questo errore viene solitamente generato come risultato della contesa in tabelle di sistema della replica di tipo merge che hanno raggiunto una dimensione eccessiva. L'eccessivo aumento delle dimensioni delle tabelle di sistema è in genere dovuto a un lungo periodo di memorizzazione della pubblicazione, in quanto i metadati devono essere archiviati in queste tabelle fino al raggiungimento del periodo di memorizzazione.  
  
## Azione dell'utente  
 **Per risolvere il problema:**  
  
1.  Ridurre il valore di-**DownloadGenerationsPerBatch** e **- UploadGenerationsPerBatch** emettere i parametri per l'agente di Merge consentire l'elaborazione di continuare mentre si risolve sottostante che provoca l'errore. I parametri degli agenti possono essere specificati nei profili agente e dalla riga di comando. Per altre informazioni, vedere:  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Visualizzare e modificare i parametri di prompt dei comandi dell'agente di replica & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concetti di file eseguibili dell'agente replica](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
2.  Specificare l'impostazione più bassa possibile per il periodo di memorizzazione della pubblicazione. Per altre informazioni, vedere [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
3.  Come parte della manutenzione della replica di tipo merge, verificare occasionalmente l'aumento delle tabelle di sistema associate alla replica di tipo merge: **MSmerge_contents**, **MSmerge_genhistory**, e **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, e **MSmerge_past_partition_mappings**. Reindicizzare periodicamente queste tabelle. Per ulteriori informazioni, vedere [riorganizzazione e ricompilazione degli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  