---
title: "Database di pubblicazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.publicationdatabase.f1"
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Database di pubblicazione
  Il database di pubblicazione è il database del server di pubblicazione che funge da origine dei dati e degli oggetti di database da replicare. Tutti i database utilizzati nella replica devono essere abilitati. Il database viene abilitato quando un membro del ruolo predefinito del server **sysadmin** :  
  
-   Crea una pubblicazione nel database tramite la Creazione guidata nuova pubblicazione.  
  
-   Seleziona il database nella finestra di dialogo **Proprietà server di pubblicazione** .  
  
-   Esegue **sp_replicationdboption** e imposta l'opzione **pubblicare** (per pubblicazioni snapshot o transazionali) o **la pubblicazione di tipo merge** (per le pubblicazioni di tipo merge) per **True**.  
  
## Opzioni  
 **Database**  
 Consente di selezionare il nome del database contenente i dati e gli oggetti di database che si desidera pubblicare.  
  
## Vedere anche  
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  