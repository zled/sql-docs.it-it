---
title: "Connetti al server (Oracle) - Propriet&#224; connessione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.oracleconnection.connectionprops.f1"
helpviewer_keywords: 
  - "Connetti al server (finestra di dialogo), replica"
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# Connetti al server (Oracle) - Propriet&#224; connessione
  Utilizzare il **le proprietà di connessione** scheda della finestra di **Connetti al Server** la finestra di dialogo per specificare un'opzione di pubblicazione **Gateway** o **Complete**. Dopo aver identificato un server di pubblicazione, questa opzione può essere modificata solo eliminando e riconfigurando il server di pubblicazione. Per ulteriori informazioni, vedere [configurare un server di pubblicazione Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## Opzioni  
 **Tipo server di pubblicazione**  
 Selezionare **Gateway** o **completo**. L'opzione **Completa** è progettata per offrire pubblicazioni snapshot e transazionali con il set completo di caratteristiche supportate per la pubblicazione Oracle. L'opzione **Gateway** consente l'ottimizzazione della progettazione specifica per migliorare le prestazioni per i casi in cui la replica funge da gateway tra i sistemi. Non è possibile usare l'opzione **Gateway** se si intende pubblicare la stessa tabella in più pubblicazioni transazionali. Se si seleziona **Gateway**, una tabella può essere presente al massimo in una pubblicazione transazionale e in un numero qualsiasi di pubblicazioni snapshot.  
  
 **Timeout**  
 Specificare quanto tempo il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di distribuzione deve tentare di connettersi al server di pubblicazione Oracle prima che si verifichi un errore di timeout.  
  
## Vedere anche  
 [Glossario dei termini per la pubblicazione Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Ottimizzazione delle prestazioni per i server di pubblicazione Oracle](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  