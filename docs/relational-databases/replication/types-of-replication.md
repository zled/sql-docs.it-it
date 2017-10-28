---
title: Tipi di replica | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e73bdd657a12e4eda65ce7cc16f2e9d139ce9913
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="types-of-replication"></a>Tipi di replica
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following types of replication for use in distributed applications:  
  
-   Replica transazionale. Per altre informazioni, vedere [Replica transazionale](../../relational-databases/replication/transactional/transactional-replication.md).  
  
-   Replica di tipo merge. Per altre informazioni, vedere [Replica di tipo merge](../../relational-databases/replication/merge/merge-replication.md).  
  
-   Replica snapshot. Per altre informazioni, vedere [Replica snapshot](../../relational-databases/replication/snapshot-replication.md).  
  
 Il tipo di replica selezionato per un'applicazione dipende da numerosi fattori, tra cui l'ambiente fisico di replica, il tipo e la quantità di dati da replicare e l'eventuale presenza di dati aggiornati nel Sottoscrittore. L'ambiente fisico include il numero e la posizione dei computer coinvolti nella replica, nonché se si tratti di computer client (workstation, computer portatili o dispositivi palmari) o server.  
  
 Ogni tipo di replica ha in genere inizio con una sincronizzazione degli oggetti pubblicati tra server di pubblicazione e Sottoscrittori. Questa sincronizzazione iniziale può essere eseguita dalla replica con uno *snapshot*, ovvero una copia di tutti gli oggetti e i dati specificati da una pubblicazione. Dopo la creazione, lo snapshot viene recapitato ai Sottoscrittori. Per alcune applicazioni, è sufficiente la replica snapshot. Per altri tipi di applicazioni, è importante che esista un flusso incrementale nel tempo delle successive modifiche di dati al Sottoscrittore. Alcune applicazioni richiedono inoltre il flusso delle modifiche dal Sottoscrittore al server di pubblicazione. La replica transazionale e la replica di tipo merge offrono opzioni per questi tipi di applicazioni.  
  
 Le modifiche di dati non vengono rilevate per la replica snapshot. Ogni volta che viene applicato uno snapshot, vengono completamente sovrascritti i dati esistenti. La replica transazionale rileva le modifiche tramite il log delle transazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mentre la replica di tipo merge utilizza a tale scopo trigger e tabelle di metadati.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  

