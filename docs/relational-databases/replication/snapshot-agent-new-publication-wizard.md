---
title: Agente snapshot (Creazione guidata nuova pubblicazione) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.configuresnapshotagent.f1
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
caps.latest.revision: 29
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb07b14c4d43ed664da7ac0b2b77324594c88f98
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="snapshot-agent-new-publication-wizard"></a>Agente snapshot (Creazione guidata nuova pubblicazione)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'agente snapshot crea file contenenti lo schema della pubblicazione e i dati utilizzati per inizializzare nuove sottoscrizioni. Per impostazione predefinita, l'agente snapshot viene eseguito immediatamente dopo la creazione della pubblicazione mediante Creazione guidata nuova pubblicazione. L'agente verrà successivamente eseguito in base alla pianificazione impostata dall'utente. L'eventuale creazione di nuovi file di snapshot a ogni esecuzione dell'agente dipende dal tipo di replica e dalle opzioni scelte. Per altre informazioni, vedere [Creare e applicare lo snapshot](../../relational-databases/replication/create-and-apply-the-snapshot.md).  
  
 Per le pubblicazioni di tipo merge che utilizzano filtri con parametri, è necessario creare uno snapshot per ogni partizione di dati dopo il completamento dello snapshot di pubblicazione. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
## <a name="options"></a>Opzioni  
 **Crea snapshot immediatamente** (replica di tipo merge) o **Crea uno snapshot immediatamente e mantieni lo snapshot disponibile per l'inizializzazione delle sottoscrizioni** (replica transazionale)  
 Selezionare questa casella di controllo per creare uno snapshot non appena viene completata la Creazione guidata nuova pubblicazione. Deselezionarla invece se si prevede di modificare le proprietà dello snapshot nella finestra di dialogo **Proprietà pubblicazione** prima di generare uno snapshot oppure se il Sottoscrittore verrà inizializzato senza alcuno snapshot. Per altre informazioni, vedere [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
> [!NOTE]  
>  Durante la procedura guidata è possibile che venga richiesto di selezionare la connessione al server di distribuzione per consentire l'avvio del processo appropriato per l'agente di distribuzione o l'agente di merge.  
  
 **Usa la pianificazione seguente per l'esecuzione dell'agente snapshot**  
 Accettare la pianificazione predefinita per l'esecuzione dell'agente snapshot oppure fare clic su **Cambia** per specificare una pianificazione diversa.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Creare e applicare lo snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Visualizzare e modificare le proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Inizializzare una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
