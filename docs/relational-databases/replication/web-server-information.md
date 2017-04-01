---
title: "Informazioni server Web | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.webserverinformation.f1"
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Informazioni server Web
  Le informazioni sul server Web sono necessarie per l'utilizzo dell'opzione relativa alla sincronizzazione Web per la replica di tipo merge. Per informazioni sulla configurazione della sincronizzazione Web, vedere [Configura sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
## Opzioni  
 **Indirizzo server Web**  
 Se è stato specificato un indirizzo del server Web nel **andInternet FTP Snapshot** pagina della **Proprietà pubblicazione** nella finestra di dialogo viene visualizzato nella casella di testo come valore predefinito. È possibile accettare l'impostazione predefinita oppure immettere l'indirizzo di un server Web completo per il server [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) che esegue la sincronizzazione della sottoscrizione.  
  
 **Indicare la modalità di connessione di ogni Sottoscrittore al server Web**  
 Consente di specificare il tipo di autenticazione utilizzato per la connessione al server Web. È consigliabile utilizzare l'autenticazione di base per le connessioni al server IIS realizzate in combinazione con SSL (Secure Sockets Layer). Se si seleziona l'autenticazione di base, immettere l'account e la password che verranno utilizzati per la connessione dal Sottoscrittore al server IIS.  
  
## Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Sottoscrittori non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Sincronizzazione Web per la replica di tipo merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  