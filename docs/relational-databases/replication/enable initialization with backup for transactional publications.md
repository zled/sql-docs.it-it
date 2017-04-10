---
title: "Abilitazione dell&#39;inizializzazione con un backup per le pubblicazioni transazionali (SQL Server Management Studio) | Microsoft Docs"
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
  - "manual subscription initialization [SQL Server replication]"
  - "subscriptions [SQL Server replication], initializing"
  - "inizializzazione delle sottoscrizioni [replica di SQL Server], senza snapshot"
  - "replica transazionale, backup e ripristino"
  - "backup [replica di SQL Server], replica transazionale"
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Abilitazione dell&#39;inizializzazione con un backup per le pubblicazioni transazionali (SQL Server Management Studio)
  Per inizializzare una sottoscrizione di una pubblicazione transazionale da un backup, attivare la pubblicazione in modo da consentire l'inizializzazione da un backup e quindi specificare le informazioni di backup durante la creazione della sottoscrizione:  
  
-   Attivare la pubblicazione di **Opzioni di sottoscrizione** pagina del **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Specificare le informazioni di backup con la stored procedure [sp_addsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Per ulteriori informazioni sui parametri necessari per **sp_addsubscription**, vedere [inizializzare una sottoscrizione transazionale da un Backup & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/initialize a transactional subscription from a backup.md).  
  
### Per attivare l'inizializzazione con un backup  
  
1.  Nel **Opzioni di sottoscrizione** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un valore di **True** per il **Consenti inizializzazione dai file di backup** opzione.  
  
## Vedere anche  
 [Inizializzazione di una sottoscrizione transazionale senza uno snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  