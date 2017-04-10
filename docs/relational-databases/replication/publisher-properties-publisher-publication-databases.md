---
title: "Propriet&#224; server di pubblicazione - Server di pubblicazione, Database di pubblicazione | Microsoft Docs"
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
  - "sql13.rep.configdistwizard.pubproperties.pubdb.f1"
helpviewer_keywords: 
  - "Proprietà server di pubblicazione - finestra di dialogo"
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Propriet&#224; server di pubblicazione - Server di pubblicazione, Database di pubblicazione
  La pagina **Database di pubblicazione** della finestra di dialogo **Proprietà server di pubblicazione** consente a un utente membro del ruolo predefinito del server **sysadmin** di abilitare i database per la replica. Attivazione di un database non pubblicare tale database. piuttosto, consente a qualsiasi utente il **db_owner** ruolo predefinito del database per il database creare una o più pubblicazioni nel database.  
  
## Opzioni  
 **Transazionale**  
 Selezionare questa casella di controllo per consentire agli utenti di **db_owner** ruolo predefinito del database per creare le pubblicazioni snapshot o pubblicazioni transazionali nel database.  
  
 **Merge**  
 Selezionare questa casella di controllo per consentire agli utenti di **db_owner** ruolo predefinito del database per creare pubblicazioni di tipo merge nel database.  
  
## Vedere anche  
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Proprietà riferimento & #40; Replica & #41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  