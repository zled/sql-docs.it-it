---
title: Rilevare e risolvere i conflitti tra repliche di tipo merge | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- conflict resolution [SQL Server replication]
- viewing merge replication conflicts
- resolving merge replication conflicts
- articles [SQL Server replication], conflict resolution
- merge replication conflict resolution [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9a65456772b4d19facec168d977e67443d90063
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="advanced-merge-replication---resolve-merge-replication-conflicts"></a>Replica di tipo merge avanzata - Risolvere i conflitti tra repliche di tipo merge
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Se un server di pubblicazione e un Sottoscrittore sono connessi e viene eseguita la sincronizzazione, l'agente di merge rileva l'eventuale presenza di conflitti. Se si verificano conflitti, l'agente di merge utilizza un sistema di risoluzione dei conflitti per determinare quali dati verranno accettati e propagati agli altri siti.  
  
> [!NOTE]  
>  Sebbene un Sottoscrittore esegua la sincronizzazione con il server di pubblicazione, i conflitti in genere si verificano tra gli aggiornamenti effettuati in diversi Sottoscrittori, anziché tra gli aggiornamenti effettuati in un Sottoscrittore e nel server di pubblicazione.  
  
 La replica di tipo merge prevede diversi metodi per rilevare e risolvere i conflitti. Il metodo predefinito è appropriato alla maggior parte delle applicazioni:  
  
-   Se si verifica un conflitto tra un server di pubblicazione e un Sottoscrittore, la modifica nel server di pubblicazione viene confermata e quella nel Sottoscrittore viene ignorata.  
  
-   Se si verifica un conflitto tra due Sottoscrittori che utilizzano sottoscrizioni client (tipo predefinito per le sottoscrizioni pull), verrà confermata la modifica del primo Sottoscrittore che eseguirà la sincronizzazione con il server di pubblicazione e la modifica del secondo Sottoscrittore verrà ignorata. Per informazioni sulla scelta delle sottoscrizioni client e server, vedere [Specificare una sottoscrizione di tipo merge e la priorità per la risoluzione dei conflitti &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify-a-merge-subscription-type-and-conflict-resolution-priority.md).  
  
-   Se si verifica un conflitto tra due Sottoscrittori che utilizzano sottoscrizioni server (tipo predefinito per le sottoscrizioni push), verrà confermata la modifica del Sottoscrittore con valore di priorità più alto e la modifica del secondo Sottoscrittore verrà ignorata. Se i valori di priorità sono uguali, verrà confermata la modifica del primo Sottoscrittore che eseguirà la sincronizzazione con il server di pubblicazione.  
  
 Per ulteriori informazioni sul rilevamento e la risoluzione dei conflitti per la replica di tipo merge, vedere [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni degli articoli per la replica di tipo merge](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Sottoscrivere le pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  
