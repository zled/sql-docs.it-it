---
title: "Propriet&#224; server di distribuzione, Server di pubblicazione | Microsoft Docs"
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
  - "sql13.rep.configdistwizard.distproperties.publishers.f1"
helpviewer_keywords: 
  - "Proprietà server di distribuzione - finestra di dialogo"
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Propriet&#224; server di distribuzione, Server di pubblicazione
  La pagina **Server di pubblicazione** della finestra di dialogo **Proprietà server di distribuzione** consente di abilitare l'utilizzo del server di distribuzione corrente da parte dei server di pubblicazione. È inoltre possibile impostare le proprietà associate a tali server di pubblicazione. Tenere presente che, se si abilita un server di pubblicazione per l'utilizzo di questo server come server di distribuzione remoto, il server non diventerà un server di pubblicazione. È infatti necessario connettersi al server di pubblicazione, configurarlo per la pubblicazione e selezionare questo server come server di distribuzione. Utilizzando la Creazione guidata nuova pubblicazione è possibile configurare il server di pubblicazione e selezionare un server di distribuzione.  
  
## Opzioni  
 **Server di pubblicazione**  
 Consente di selezionare i server autorizzati all'utilizzo del server di distribuzione corrente. Fare clic sul pulsante delle proprietà **(...)** accanto a un server di pubblicazione per visualizzare e impostare proprietà aggiuntive.  
  
 **Aggiungi**  
 Se il server desiderato non è elencato, fare clic su **Aggiungi** per aggiungere un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione o server di pubblicazione Oracle all'elenco dei server di pubblicazione disponibili. Se il server aggiunto è il primo server a utilizzare il server di distribuzione corrente come server di distribuzione remoto, viene richiesto di digitare una password per il collegamento amministrativo.  
  
 **Password per collegamento amministrativo**  
 Utilizzato per specificare o aggiornamento rende la password per la replica di connessione tra il server di pubblicazione e il server di distribuzione remoto utilizzando il **distributor_admin** account di accesso:  
  
-   Se il server di distribuzione viene utilizzato solo come server di distribuzione locale, tale password viene generata in modo casuale e viene configurata automaticamente.  
  
-   Se il server di distribuzione viene utilizzato già da un server di pubblicazione remoto, una password è stata specificata inizialmente in questa pagina o nella pagina **Password server di distribuzione** della Configurazione guidata distribuzione.  
  
-   Se si tratta del primo server di pubblicazione abilitato per il server di distribuzione corrente viene richiesto di digitare una password.  
  
 Per ulteriori informazioni sulla sicurezza per i server di distribuzione, vedere [proteggere il server di distribuzione](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## Vedere anche  
 [Configurazione della distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  