---
title: "Tipi di pubblicazioni per la replica transazionale | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replica transazionale, pubblicazioni"
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Tipi di pubblicazioni per la replica transazionale
  La replica transazionale offre tre tipi di pubblicazioni:  
  
|Tipo di pubblicazione|Descrizione|  
|----------------------|-----------------|  
|Pubblicazione transazionale standard|Appropriata per topologie in cui tutti i dati nel Sottoscrittore sono di sola lettura. (La replica transazionale non impone l'impostazione dei dati in sola lettura nel Sottoscrittore).<br /><br /> Le pubblicazioni transazionali standard vengono create per impostazione predefinita quando si utilizzano Transact-SQL o gli oggetti RMO (Replication Management Objects). Quando si utilizza la creazione guidata nuova pubblicazione, vengono creati selezionando **pubblicazione transazionale** sul **tipo di pubblicazione** pagina.<br /><br /> Per ulteriori informazioni sulla creazione di pubblicazioni, vedere [pubblicare dati e oggetti di Database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).|  
|Pubblicazione transazionale in una topologia peer-to-peer|Le caratteristiche di questo tipo di pubblicazione sono:<br /><br /> - Ogni posizione presenta dati identici e opera sia come server di pubblicazione che come Sottoscrittore.<br /><br /> - La stessa riga può essere modificata solo in una posizione per volta.<br /><br /> - Questa topologia è più adatta agli ambienti server che necessitano di disponibilità elevata e di scalabilità per la lettura.<br /><br /> <br /><br /> Per ulteriori informazioni, vedere [la replica transazionale Peer-to-Peer](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
  
## Vedere anche  
 [Replica transazionale](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  