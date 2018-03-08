---
title: "Proprietà sottoscrizione - Server di pubblicazione | Microsoft Docs"
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
ms.topic: article
f1_keywords: sql13.rep.newsubwizard.subproperties.publisher.f1
helpviewer_keywords: Subscription Properties dialog box
ms.assetid: d4b2bc8b-0431-4331-8305-8992c96d0d34
caps.latest.revision: "22"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: baba517b574179be16ef1376d0b1eff113c6338d
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="subscription-properties---publisher"></a>Proprietà sottoscrizione - Server di pubblicazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] La finestra di dialogo **Proprietà sottoscrizione** nel server di pubblicazione consente di visualizzare e impostare proprietà per le sottoscrizioni push. Sebbene sia possibile visualizzare alcune proprietà per le sottoscrizioni pull, nella finestra di dialogo **Proprietà sottoscrizione** nel Sottoscrizione sono incluse proprietà aggiuntive ed è possibile modificarle.  
  
 Ogni proprietà nella finestra di dialogo **Proprietà sottoscrizione** include una descrizione. Fare clic su una proprietà per visualizzarne la descrizione nella parte inferiore della finestra di dialogo. In questo argomento vengono fornite informazioni aggiuntive su alcune proprietà che, nella maggior parte dei casi, sono visualizzate nel server di pubblicazione solo per le sottoscrizioni push. Le proprietà sono raggruppate nelle categorie seguenti:  
  
-   Proprietà che si applicano a tutte le sottoscrizioni.  
  
-   Proprietà che si applicano alle sottoscrizioni transazionali.  
  
-   Proprietà che si applicano alle sottoscrizioni di tipo merge.  
  
 Se un'opzione è visualizzata in modalità di sola lettura, può essere impostata solo al momento della creazione della sottoscrizione. Se si desidera impostare opzioni non disponibili nella Creazione guidata nuova sottoscrizione, creare la sottoscrizione tramite stored procedure. Per ulteriori informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) e [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
## <a name="options-for-all-subscriptions"></a>Opzioni per tutte le sottoscrizioni  
 **Security**  
 Fare clic sulla riga **Account processo agente** e quindi sul pulsante delle proprietà (**...**) per modificare l'account utilizzato per l'esecuzione dell'agente di distribuzione o dell'agente di merge nel server di distribuzione. Per modificare l'account utilizzato dall'agente di distribuzione o dall'agente di merge per creare connessioni al Sottoscrittore, fare clic su **Connessione al Sottoscrittore**e quindi sul pulsante delle proprietà (**...**).  
  
 Per ulteriori informazioni sulle autorizzazioni necessarie per ogni agente, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="options-for-transactional-subscriptions"></a>Opzioni per le sottoscrizioni transazionali  
 **Impedisci il loop delle transazioni**  
 Consente di stabilire se l'agente di distribuzione reinvia le transazioni originate nel Sottoscrittore al Sottoscrittore. Questa opzione viene utilizzata per la replica transazionale bidirezionale. Per altre informazioni, vedere [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).  
  
 **Sottoscrizione aggiornabile**  
 Consente di stabilire se le modifiche del Sottoscrittore vengono replicate sul server di pubblicazione. È possibile replicare le modifiche utilizzando l'aggiornamento in coda o immediato. L'opzione **Metodo di aggiornamento del Sottoscrittore** determina quale metodo utilizzare. Per altre informazioni, vedere [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
## <a name="options-for-merge-subscriptions"></a>Opzioni per sottoscrizioni di tipo merge  
 **Definizione partizione (HOST_NAME)**  
 Nel caso di una pubblicazione che utilizza filtri con parametri, la replica di tipo merge valuta una delle due funzioni di sistema, o entrambe se il filtro fa riferimento sia all'una che all'altra, durante la sincronizzazione per determinare i dati che devono essere ricevuti dal Sottoscrittore, ovvero **SUSER_SNAME()** o **HOST_NAME()**. Per impostazione predefinita, **HOST_NAME()** restituisce il nome del computer in cui è in esecuzione l'agente di merge. È tuttavia possibile sostituire questo valore nella Creazione guidata nuova sottoscrizione. Per ulteriori sui filtri con parametri e la sostituzione di **HOST_NAME()**, vedere [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
 **Tipo di sottoscrizione** e **Priorità**  
 Indica se la sottoscrizione è una sottoscrizione client o server. Questa impostazione non può essere modificata dopo la creazione della sottoscrizione. Le sottoscrizioni server possono ripubblicare i dati in altri Sottoscrittori. A tali sottoscrizioni è inoltre possibile assegnare una priorità per la risoluzione dei conflitti.  
  
 Se si seleziona un tipo di sottoscrizione server nella Creazione guidata nuova sottoscrizione, al Sottoscrittore viene assegnata una priorità che verrà utilizzata nella risoluzione dei conflitti.  
  
 **Risoluzione interattiva**  
 Consente di indicare di utilizzare l'interfaccia utente del sistema di risoluzione dei conflitti interattivo durante la sincronizzazione di tipo merge. A tale scopo, è necessario impostare **Usa Gestione sincronizzazione Microsoft Windows** su **Abilita**. Per altre informazioni, vedere [Interactive Conflict Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà delle sottoscrizioni pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni push](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
