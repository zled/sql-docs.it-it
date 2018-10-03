---
title: Sincronizzare le sottoscrizioni (replica) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], subscriptions
- subscriptions [SQL Server replication], synchronizing
- replication [SQL Server], synchronization
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ed208c81fe7b3459f22e013117ed1f7cf51ec314
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796559"
---
# <a name="synchronize-subscriptions-replication"></a>Sincronizzazione delle sottoscrizioni (replica)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Le sottoscrizioni vengono sincronizzate dagli agenti di replica. L'agente di distribuzione sincronizza le sottoscrizioni di pubblicazioni transazionali e snapshot, mentre l'agente di merge sincronizza le sottoscrizioni di pubblicazioni di tipo merge. Per sincronizzare le sottoscrizioni e controllare il comportamento della sincronizzazione, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], le stored procedure di replica e gli oggetti RMO (Replication Management Objects). Negli argomenti seguenti viene descritto come sincronizzare le sottoscrizioni e specificare le opzioni di sincronizzazione.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Creazione e applicazione dello snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Creare uno snapshot per una pubblicazione di tipo merge con filtri con parametri](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Abilitare l'inizializzazione con un backup per le pubblicazioni transazionali &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/enable-initialization-with-backup-for-transactional-publications.md)  
  
-   [Inizializzare una sottoscrizione transazionale da un backup &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Inizializzare manualmente una sottoscrizione](../../relational-databases/replication/initialize-a-subscription-manually.md)  
  
-   [Sincronizzazione di una sottoscrizione pull](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Sincronizzazione di una sottoscrizione push](../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
-   [Reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md)  
  
-   [Eseguire script prima e dopo l'applicazione di uno snapshot &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [Eseguire script durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Visualizzare e risolvere i conflitti di dati per le pubblicazioni di tipo merge &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [Visualizzare i conflitti di dati per le pubblicazioni transazionali &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Sincronizzare una sottoscrizione mediante Gestione sincronizzazione Microsoft Windows &#40;Gestione sincronizzazione Microsoft&#41;](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md)  
  
-   [Implementare un gestore della logica di business per un articolo di merge](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Eseguire il debug di un gestore della logica di business &#40;programmazione della replica&#41;](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [Controllare il comportamento di trigger e vincoli durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md)  
  
-   [Implementare un sistema di risoluzione dei conflitti personalizzato per un articolo di tipo merge](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Sincronizzare i dati](../../relational-databases/replication/synchronize-data.md)  
  
  
