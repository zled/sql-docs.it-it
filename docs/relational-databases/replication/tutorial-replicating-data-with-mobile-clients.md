---
title: "Esercitazione: Replica di dati con client mobili | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "replica [SQL Server], esercitazioni"
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# Esercitazione: Replica di dati con client mobili
La replica è una buona soluzione al problema legato al trasferimento dei dati tra un server centrale e client mobili connessi solo occasionalmente. Le procedure guidate relative alla replica consentono di eseguire in modo semplificato i passaggi necessari per configurare e amministrare una topologia di replica. In questa esercitazione viene illustrato come configurare una topologia di replica per client mobili.  
  
## Lezioni dell'esercitazione  
In questa esercitazione verrà utilizzata la replica di tipo merge per pubblicare i dati da un database centrale in uno o più client mobili in modo che ogni utente disponga di un subset di dati filtrato in modo univoco. Nella prima lezione verranno descritte le procedure per la creazione di una pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Nelle lezioni successive verranno descritte le procedure per creare e sincronizzare una sottoscrizione.  
  
## Requisiti  
Questa esercitazione è destinata agli utenti esperti nelle operazioni di database fondamentali ma con una limitata conoscenza della replica. Prima di iniziare questa esercitazione, è necessario completare l'[Esercitazione: Preparazione del server per la replica](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Per utilizzare l'esercitazione è necessario che nel sistema siano installati i componenti seguenti:  
  
-   Nel server di pubblicazione (origine):  
  
    -   Qualsiasi edizione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ad eccezione di Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) o [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Queste edizioni non possono fungere da server di pubblicazione per la replica.  
  
    -   Database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Per maggiore sicurezza, i database di esempio non vengono installati per impostazione predefinita.  
  
-   Sottoscrittore (destinazione):  
  
    -   Qualsiasi edizione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ad eccezione di [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] non è supportato dalla pubblicazione creata in questa esercitazione.  
  
    > [!NOTE]  
    > La replica non è installata per impostazione predefinita in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
> [!NOTE]  
> In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è necessario connettersi al server di pubblicazione e al Sottoscrittore mediante un account di accesso che sia membro del ruolo predefinito del server sysadmin.  
  
**Tempo previsto per il completamento di questa esercitazione: 30 minuti.**  
  
## Lezioni dell'esercitazione  
  
-   [Lezione 1: Pubblicazione dei dati tramite la replica di tipo merge](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)  
  
-   [Lezione 2: Creazione di una sottoscrizione per una pubblicazione di tipo merge](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
[Avviare l'esercitazione](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)  
  
## Vedere anche  
[Concetti di base relativi alla programmazione della replica](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  
  
  
