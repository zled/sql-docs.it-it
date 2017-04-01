---
title: "Propriet&#224; pubblicazione (pagina sicurezza agente) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.agentsecurity.f1"
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Propriet&#224; pubblicazione (pagina sicurezza agente)
  La pagina **Sicurezza agente** della finestra di dialogo **Proprietà pubblicazione** consente di accedere alle impostazioni relative agli account nell'ambito dei quali gli agenti seguenti vengono eseguiti e si connettono ai computer inclusi in una topologia di replica.  
  
-   Agente snapshot per tutte le pubblicazioni.  
  
-   Agente di lettura log per tutte le pubblicazioni transazionali. Per ogni database pubblicato per la replica transazionale, esiste un solo agente di lettura log. Le modifiche apportate alle impostazioni dell'agente di lettura log sono valide per tutte le pubblicazioni transazionali in un database.  
  
-   Agente di lettura coda per pubblicazioni transazionali che consentono sottoscrizioni ad aggiornamento in coda. A ogni database di distribuzione è associato un agente di lettura coda. Le modifiche apportate all'agente di lettura coda sono valide per tutte le pubblicazioni transazionali con sottoscrizioni ad aggiornamento in coda che utilizzano il medesimo database di distribuzione. Per ulteriori informazioni sulle impostazioni di protezione agente di lettura coda, vedere [visualizzare e modificare le impostazioni di sicurezza](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Per ulteriori informazioni sulle autorizzazioni e le impostazioni di sicurezza necessarie per ogni agente, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Opzioni  
 **Le impostazioni di sicurezza** o **Crea agente**  
 Se è stato creato un processo dell'agente, fare clic su **le impostazioni di sicurezza** per accedere a una finestra di dialogo che consente di modificare le impostazioni di sicurezza per un agente. Se non è stato creato alcun processo agente, fare clic su **Crea agente** per crearne uno e specificare le relative impostazioni di sicurezza.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  