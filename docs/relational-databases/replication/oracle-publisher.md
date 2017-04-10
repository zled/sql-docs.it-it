---
title: "Server di pubblicazione Oracle | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.selectoraclepublisher.f1"
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Server di pubblicazione Oracle
  A partire da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di pubblicare dati da un database Oracle tramite replica snapshot e transazionale. Per ulteriori informazioni, vedere [Cenni preliminari sulla pubblicazione Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
 Il server di pubblicazione Oracle deve utilizzare un server di distribuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] remoto nel quale deve essere eseguita la procedura guidata dopo che il software di rete Oracle necessario è stato installato e testato. Per ulteriori informazioni, vedere [configurare un server di pubblicazione Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
> [!IMPORTANT]  
>  Se un altro amministratore configurato il database Oracle come server di pubblicazione, dopo aver fatto clic **Avanti** viene chiesto di immettere la password per l'accesso alla replica utilizzata per la connessione al database Oracle. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Crea un mapping tra l'account di accesso e la connessione al server collegato al database Oracle. Non sarà più necessario digitare la password per le connessioni successive al database Oracle.  
  
## Opzioni  
 **Server di pubblicazione Oracle**  
 Consente di selezionare un server di pubblicazione Oracle nell'elenco. Nell'elenco sono inclusi i server di pubblicazione Oracle precedentemente configurati per l'utilizzo del server su cui viene eseguita la procedura guidata come server di distribuzione. Se l'elenco è vuoto o il server di pubblicazione Oracle si desidera utilizzare non è presente nell'elenco, fare clic su **Aggiungi server di pubblicazione Oracle**.  
  
 **Aggiungi server di pubblicazione Oracle**  
 Fare clic per avviare il **proprietà server di distribuzione** la finestra di dialogo. Nella finestra di dialogo, fare clic su **Aggiungi**, quindi fare clic su **Aggiungi server di pubblicazione Oracle**. Nel **Connetti al Server** finestra di dialogo specificare il nome del server Oracle e l'account di accesso e password per lo schema utente di amministrazione della replica. Per ulteriori informazioni, vedere [Connetti al Server & #40; Oracle & #41; account di accesso](../../relational-databases/replication/connect-to-server-oracle-login.md).  
  
> [!NOTE]  
>  Se il server su cui viene eseguita la procedura guidata non è stato ancora configurato come server di distribuzione, viene richiesto di eseguire la configurazione adesso.  
  
## Vedere anche  
 [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)   
 [Proprietà riferimento & #40; Replica & #41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  