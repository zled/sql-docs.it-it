---
title: "Visualizzare comandi replicati e altre informazioni nel database di distribuzione (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_browsereplcmds"
  - "replica transazionale, monitoraggio"
  - "database di distribuzione [replica di SQL Server], visualizzazione di comandi replicati"
  - "visualizzazione di comandi replicati"
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Visualizzare comandi replicati e altre informazioni nel database di distribuzione (programmazione Transact-SQL della replica)
  Durante l'utilizzo della replica transazionale, i comandi della transazione vengono archiviati nel database di distribuzione finché non vengono propagati a tutti i Sottoscrittori dall'agente di distribuzione o un agente di distribuzione nel Sottoscrittore non esegue il pull delle modifiche. È possibile visualizzare tali comandi in sospeso nel database di distribuzione a livello di programmazione, utilizzando le stored procedure di replica. Per ulteriori informazioni, vedere [Stored procedure di replica & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).  
  
### Per visualizzare comandi replicati da tutte le pubblicazioni transazionali nel database di distribuzione  
  
1.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md).  
  
### Per visualizzare comandi replicati nel database di distribuzione da un articolo specifico o da un database specifico pubblicato tramite la replica transazionale  
  
1.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md). Specificare **@publication** e **@article**. Prendere nota del valore di **id articolo** nel set di risultati.  
  
2.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md). (Facoltativo) Specificare l'ID articolo ottenuto al passaggio 2 per **@article_id**. (Facoltativo) Specificare l'ID del database di pubblicazione per **@publisher_database_id**, che può essere ottenuto dal **database_id** colonna il [Sys. Databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo.  
  
## Vedere anche  
 [Programmatically Monitor Replication](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  