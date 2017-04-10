---
title: "Rilevamento e risoluzione di conflitti tra repliche di tipo merge | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "risoluzione dei conflitti di replica di tipo merge [replica di SQL Server], informazioni sulla risoluzione dei conflitti"
  - "sistema di risoluzione di conflitti predefinito"
  - "risoluzione di conflitti [replica di SQL Server]"
  - "visualizzazione di conflitti di replica di tipo merge"
  - "risoluzione di conflitti di replica di tipo merge"
  - "articoli [replica di SQL Server], risoluzione dei conflitti"
  - "risoluzione di conflitti di replica di tipo merge [replica di SQL Server]"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Rilevamento e risoluzione di conflitti tra repliche di tipo merge
  Se un server di pubblicazione e un Sottoscrittore sono connessi e viene eseguita la sincronizzazione, l'agente di merge rileva l'eventuale presenza di conflitti. Se si verificano conflitti, l'agente di merge utilizza un sistema di risoluzione dei conflitti per determinare quali dati verranno accettati e propagati agli altri siti.  
  
> [!NOTE]  
>  Sebbene un Sottoscrittore esegua la sincronizzazione con il server di pubblicazione, i conflitti in genere si verificano tra gli aggiornamenti effettuati in diversi Sottoscrittori, anziché tra gli aggiornamenti effettuati in un Sottoscrittore e nel server di pubblicazione.  
  
 La replica di tipo merge prevede diversi metodi per rilevare e risolvere i conflitti. Il metodo predefinito è appropriato alla maggior parte delle applicazioni:  
  
-   Se si verifica un conflitto tra un server di pubblicazione e un Sottoscrittore, la modifica nel server di pubblicazione viene confermata e quella nel Sottoscrittore viene ignorata.  
  
-   Se si verifica un conflitto tra due Sottoscrittori che utilizzano sottoscrizioni client (tipo predefinito per le sottoscrizioni pull), verrà confermata la modifica del primo Sottoscrittore che eseguirà la sincronizzazione con il server di pubblicazione e la modifica del secondo Sottoscrittore verrà ignorata. Per informazioni su come specificare le sottoscrizioni client e server, vedere [specificare un tipo di sottoscrizione di tipo Merge e priorità per la risoluzione dei conflitti & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md).  
  
-   Se si verifica un conflitto tra due Sottoscrittori che utilizzano sottoscrizioni server (tipo predefinito per le sottoscrizioni push), verrà confermata la modifica del Sottoscrittore con valore di priorità più alto e la modifica del secondo Sottoscrittore verrà ignorata. Se i valori di priorità sono uguali, verrà confermata la modifica del primo Sottoscrittore che eseguirà la sincronizzazione con il server di pubblicazione.  
  
 Per ulteriori informazioni sul rilevamento dei conflitti e risoluzione per la replica di tipo merge, vedere [Avanzate rilevamento dei conflitti di replica di Merge e la risoluzione](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
## Vedere anche  
 [Opzioni degli articoli per la replica di tipo merge](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Sottoscrizione delle pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  