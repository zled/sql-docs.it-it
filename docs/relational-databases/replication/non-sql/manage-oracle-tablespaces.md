---
title: "Gestione di spazi di tabella Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione Oracle [SQL Server replication], gestione di spazi di tabella"
  - "spazi tabella [replica di SQL Server]"
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Gestione di spazi di tabella Oracle
  Uno spazio di tabella è un'unità di archiviazione di database è quasi equivalente a un gruppo di file in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Gli spazi di tabella consentono l'archiviazione e la gestione di oggetti di database all'interno di singoli gruppi. Per ulteriori informazioni, vedere la documentazione di Oracle.  
  
 Quando si configura una tabella nell'ambito di una pubblicazione Oracle, è possibile specificare facoltativamente uno spazio di tabella Oracle esistente da utilizzare nell'archiviazione di informazioni di registrazione delle repliche. Se non specificato, lo spazio di tabella per gli oggetti di replica corrisponde allo spazio di tabella predefinito associato allo schema utente di amministrazione della replica che è stato configurato al momento della configurazione del server di pubblicazione.  
  
 **Per specificare uno spazio di tabella per una tabella di registrazione articolo**:  
  
-   Specificare uno spazio di tabella nel **Proprietà articolo** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Utilizzare [sp_changearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Utilizzare **sp_changearticle**, specificare quanto segue:  
  
    -   Il nome del server di pubblicazione Oracle per il parametro **@publisher**.  
  
    -   Il nome della pubblicazione Oracle per il parametro **@publication**.  
  
    -   Il nome dell'articolo per il parametro **@article**.  
  
    -   Un valore "tablespace" per il parametro **@property**.  
  
    -   Il nome dello spazio di tabella per il parametro **@value**.  
  
## Vedere anche  
 [Configurazione di un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oggetti creati nel server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)  
  
  