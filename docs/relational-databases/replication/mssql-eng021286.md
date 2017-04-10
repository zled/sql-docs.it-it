---
title: "MSSQL_ENG021286 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG021286 - errore"
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# MSSQL_ENG021286
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21286|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|La tabella dei conflitti '%s' non esiste.|  
  
## Spiegazione  
 Questo errore viene generato se la tabella dei conflitti per un articolo elencato in [sysmergearticles & #40; Transact-SQL & #41;](../../relational-databases/system-tables/sysmergearticles-transact-sql.md) non esiste. Questo errore può verificarsi quando si tenta di aggiungere o di eliminare una colonna da una tabella pubblicata per la replica di tipo merge.  
  
## Azione dell'utente  
 Eseguire [DBCC CHECKDB & #40; Transact-SQL & #41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) il database con la tabella dei conflitti mancante per verificare non siano presenti problemi di coerenza dei dati.  
  
 Se in un Sottoscrittore manca la tabella dei conflitti, eliminare la sottoscrizione e ricrearla. Se in un server di pubblicazione manca la tabella dei conflitti, eliminare tutte le sottoscrizioni, eliminare la pubblicazione e quindi ricreare la pubblicazione e tutte le sottoscrizioni. Per ulteriori informazioni, vedere [pubblicare dati e oggetti di Database](../../relational-databases/replication/publish/publish-data-and-database-objects.md) e [sottoscrivere pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  