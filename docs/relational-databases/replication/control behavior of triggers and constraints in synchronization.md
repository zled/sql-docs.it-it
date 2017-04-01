---
title: "Controllo del comportamento di trigger e vincoli durante la sincronizzazione (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
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
  - "identità [replica di SQL Server]"
  - "vincoli [SQL Server], replica"
  - "trigger [SQL Server], replica"
  - "trigger [replica di SQL Server]"
  - "vincoli [replica di SQL Server]"
  - "NOT FOR REPLICATION, opzione"
  - "NFR, opzione"
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Controllo del comportamento di trigger e vincoli durante la sincronizzazione (programmazione Transact-SQL della replica)
  Durante la sincronizzazione, eseguire gli agenti di replica [Inserisci & #40; Transact-SQL & #41;](../../t-sql/statements/insert-transact-sql.md), [Aggiorna & #40; Transact-SQL & #41;](../../t-sql/queries/update-transact-sql.md), e [Elimina & #40; Transact-SQL & #41;](../../t-sql/statements/delete-transact-sql.md) istruzioni nelle tabelle replicate, che possono causare la modifica dei dati trigger language (DML) in queste tabelle deve essere eseguito. In alcuni casi è necessario impedire l'attivazione di questi trigger o l'applicazione di vincoli durante la sincronizzazione. Questo comportamento dipende dalla modalità di creazione del trigger o del vincolo.  
  
### Per impedire l'esecuzione di trigger durante la sincronizzazione  
  
1.  Quando si crea un nuovo trigger, specificare l'opzione NOT FOR REPLICATION di [CREATE TRIGGER & #40; Transact-SQL & #41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
2.  Per un trigger esistente, specificare l'opzione NOT FOR REPLICATION di [ALTER TRIGGER & #40; Transact-SQL & #41;](../../t-sql/statements/alter-trigger-transact-sql.md).  
  
### Per impedire l'applicazione di vincoli durante la sincronizzazione  
  
1.  Quando si crea un nuovo vincolo CHECK o FOREIGN KEY, specificare l'opzione CHECK NOT FOR REPLICATION nella definizione del vincolo di [CREATE TABLE & #40; Transact-SQL & #41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## Vedere anche  
 [Creare tabelle & #40; motore di Database & #41;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  