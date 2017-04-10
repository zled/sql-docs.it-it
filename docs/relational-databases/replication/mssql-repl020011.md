---
title: "MSSQL_REPL020011 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL020011 - errore"
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_REPL020011
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20011|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Impossibile eseguire '%1' in '%2'.|  
  
## Spiegazione  
 Questo errore può essere generato in diverse circostanze durante l'elaborazione, ad esempio quando l'agente di lettura Log esegue la replica transazionale **sp_replcmds** (il processo non è in grado di eseguire 'sp_replcmds' in \< ServerName>) o **sp_repldone** (il processo non è in grado di eseguire 'sp_repldone' in \< ServerName>).  
  
## Azione dell'utente  
 Se questo errore viene generato in un database che è appena stato ripristinato da un backup, verificare di aver eseguito i passaggi descritti nella documentazione di backup e ripristino, inclusa l'esecuzione di **sp_replrestart** se appropriato. Per ulteriori informazioni, vedere [strategie di backup e ripristino di Snapshot e transazionali](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 Si tratta di un errore di elaborazione interna. Se viene generato in circostanze diverse dal ripristino, in genere indica che è necessario rimuovere o riconfigurare la replica. Se non è possibile rimuovere la replica, rivolgersi al supporto tecnico.  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [sp_replcmds & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)  
  
  