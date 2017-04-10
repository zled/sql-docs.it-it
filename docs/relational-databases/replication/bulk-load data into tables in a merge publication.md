---
title: "Caricamento bulk dei dati nelle tabelle in una pubblicazione di tipo merge (programmazione Transact-SQL della replica) | Microsoft Docs"
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
  - "caricamento bulk [replica di SQL Server]"
  - "caricamento bulk replica di tipo merge [replica di SQL Server]"
  - "sp_addtabletocontents"
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Caricamento bulk dei dati nelle tabelle in una pubblicazione di tipo merge (programmazione Transact-SQL della replica)
  Quando i dati vengono caricati in tabelle utilizzando il [utilità bcp](../../tools/bcp-utility.md) o [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) comando, per impostazione predefinita, i trigger di replica di tipo merge che gestiscono dati di rilevamento nel [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) tabella di sistema non vengono attivati. È possibile forzare l'attivazione dei trigger della replica di tipo merge al momento del caricamento dei dati o inserire i metadati di replica generati a livello di programmazione dopo l'operazione di copia bulk utilizzando le stored procedure di replica.  
  
### Per eseguire il caricamento bulk dei dati nelle tabelle pubblicate mediante la replica di tipo merge utilizzando l'utilità bcp  
  
1.  Nel server di pubblicazione o nel Sottoscrittore eseguire l' [bcp Utility](../../tools/bcp-utility.md) o [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) per inserire i dati in una tabella pubblicata mediante la replica di tipo merge.  
  
2.  Utilizzare uno dei metodi seguenti per assicurarsi che i metadati di replica vengano generati per i dati inseriti.  
  
    -   Eseguire la copia bulk utilizzando l'opzione FIRE_TRIGGERS.  
  
    -   Nel database in cui è stati inseriti i dati, eseguire [sp_addtabletocontents & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql.md). Specificare il nome della tabella in cui è stati inseriti i dati per **@table_name**.  
  
  