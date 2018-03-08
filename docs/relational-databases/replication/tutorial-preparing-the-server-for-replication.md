---
title: 'Esercitazione: Preparazione del server per la replica | Microsoft Docs'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ff54e23da202e1161c7cc34502f79481cd3a1534
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="tutorial-preparing-the-server-for-replication"></a>Esercitazione: Preparazione del server per la replica
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] È importante pianificare la sicurezza prima di configurare la topologia di replica. In questa esercitazione viene illustrato come proteggere la topologia di replica e come configurare la distribuzione, ovvero il primo passaggio nella replica dei dati. È necessario completare questa esercitazione prima delle altre esercitazioni sulla replica.  
  
> [!NOTE]  
> Per eseguire in modo protetto la replica dei dati tra server, è consigliabile seguire le indicazioni riportate in [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
In questa esercitazione verranno descritte le procedure per preparare i server in modo che la replica possa essere eseguita in modo protetto con privilegi minimi. Nella prima lezione viene illustrato come creare gli account di servizio Windows utilizzati per l'esecuzione degli agenti di replica. Nella seconda lezione viene illustrato come configurare la cartella utilizzata per creare e archiviare gli snapshot di pubblicazione. Nella terza lezione viene illustrato come configurare la distribuzione e impostare le autorizzazioni.  
  
## <a name="requirements"></a>Requisiti  
Questa esercitazione è destinata agli utenti esperti nelle operazioni di database fondamentali ma con una limitata conoscenza della replica.  
  
Per utilizzare l'esercitazione è necessario che nel sistema siano installati i componenti seguenti:  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] con il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
**Tempo previsto per il completamento di questa esercitazione: 30 minuti.**  
  
## <a name="lessons-in-this-tutorial"></a>Lezioni dell'esercitazione  
  
-   [Lezione 1: Creazione di account di Windows per la replica](../../relational-databases/replication/lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [Lezione 2: Preparazione della cartella snapshot](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md)  
  
-   [Lezione 3: Configurazione della distribuzione](../../relational-databases/replication/lesson-3-configuring-distribution.md)  
  
[Avviare l'esercitazione](../../relational-databases/replication/lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a>Vedere anche  
[Configurazione della distribuzione](../../relational-databases/replication/configure-distribution.md)  
[Sicurezza e protezione #40;replica&#41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
  
