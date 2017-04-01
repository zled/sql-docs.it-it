---
title: "Attivazione di backup coordinati per la replica transazionale (programmazione Transact-SQL della replica) | Microsoft Docs"
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
  - "replica transazionale, backup e ripristino"
  - "sp_replicationdboption"
  - "sincronizzazione con backup [replica di SQL Server]"
  - "backup coordinati [replica di SQL Server]"
  - "backup [replica di SQL Server], replica transazionale"
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Attivazione di backup coordinati per la replica transazionale (programmazione Transact-SQL della replica)
  Quando si attiva la replica transazionale per un database, è possibile specificare che è necessario eseguire il backup di tutte le transazioni prima del recapito al database di distribuzione. È inoltre possibile attivare il backup coordinato nel database di distribuzione. In questo modo, il log delle transazioni per il database di pubblicazione viene troncato solo in seguito al backup delle transazioni propagate al server di distribuzione. Per ulteriori informazioni, vedere [strategie di backup e ripristino di Snapshot e transazionali](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
### Per attivare i backup coordinati per un database pubblicato con replica transazionale  
  
1.  Nel server di pubblicazione, utilizzare il [DATABASEPROPERTYEX & #40; Transact-SQL & #41;](../../../t-sql/functions/databasepropertyex-transact-sql.md) funzione per restituire il **IsSyncWithBackup** proprietà del database di pubblicazione. Se la funzione restituisce **1**, coordinata backup è già stato abilitato per il database pubblicato.  
  
2.  Se la funzione nel passaggio 1 restituisce **0**, eseguire [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **sincronizzazione con backup** per **@optname**, e **true** per **@value**.  
  
    > [!NOTE]  
    >  Se si modifica il **sincronizzazione con backup** opzione **false**, il punto di troncamento del database di pubblicazione verrà aggiornato dopo l'esecuzione dell'agente di lettura Log o dopo un intervallo se l'agente di lettura Log è in esecuzione in modo continuo. L'intervallo massimo è controllato dal **– MessageInterval** parametro dell'agente (che presenta un valore predefinito di 30 secondi).  
  
### Per attivare i backup coordinati per un database di distribuzione  
  
1.  Nel server di distribuzione, utilizzare il [DATABASEPROPERTYEX & #40; Transact-SQL & #41;](../../../t-sql/functions/databasepropertyex-transact-sql.md) funzione per restituire il **IsSyncWithBackup** proprietà del database di distribuzione. Se la funzione restituisce **1**, coordinata backup è già stato abilitato per il database di distribuzione.  
  
2.  Se la funzione nel passaggio 1 restituisce **0**, eseguire [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) nel server di distribuzione nel database di distribuzione. Specificare un valore di **sincronizzazione con backup** per **@optname** e **true** per **@value**.  
  
### Per disabilitare i backup coordinati  
  
1.  Il server nel database di pubblicazione o nel server di distribuzione nel database di distribuzione, eseguire [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md). Specificare un valore di **sincronizzazione con backup** per **@optname** e **false** per **@value**.  
  
  