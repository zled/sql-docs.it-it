---
title: Agente snapshot (Creazione guidata nuova pubblicazione) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.configuresnapshotagent.f1
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
caps.latest.revision: 28
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 342cbeb0e746090fd6a74cd897eb83a99f8d871d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305531"
---
# <a name="snapshot-agent-new-publication-wizard"></a>Agente snapshot (Creazione guidata nuova pubblicazione)
  L'agente snapshot crea file contenenti lo schema della pubblicazione e i dati utilizzati per inizializzare nuove sottoscrizioni. Per impostazione predefinita, l'agente snapshot viene eseguito immediatamente dopo la creazione della pubblicazione mediante Creazione guidata nuova pubblicazione. L'agente verrà successivamente eseguito in base alla pianificazione impostata dall'utente. L'eventuale creazione di nuovi file di snapshot a ogni esecuzione dell'agente dipende dal tipo di replica e dalle opzioni scelte. Per altre informazioni, vedere [Creare e applicare lo snapshot](create-and-apply-the-snapshot.md).  
  
 Per le pubblicazioni di tipo merge che utilizzano filtri con parametri, è necessario creare uno snapshot per ogni partizione di dati dopo il completamento dello snapshot di pubblicazione. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).  
  
## <a name="options"></a>Opzioni  
 **Crea snapshot immediatamente** (replica di tipo merge) o **Crea uno snapshot immediatamente e mantieni lo snapshot disponibile per l'inizializzazione delle sottoscrizioni** (replica transazionale)  
 Selezionare questa casella di controllo per creare uno snapshot non appena viene completata la Creazione guidata nuova pubblicazione. Deselezionarla invece se si prevede di modificare le proprietà dello snapshot nella finestra di dialogo **Proprietà pubblicazione** prima di generare uno snapshot oppure se il Sottoscrittore verrà inizializzato senza alcuno snapshot. Per altre informazioni, vedere [Inizializzazione di una sottoscrizione transazionale senza uno snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
> [!NOTE]  
>  Durante la procedura guidata è possibile che venga richiesto di selezionare la connessione al server di distribuzione per consentire l'avvio del processo appropriato per l'agente di distribuzione o l'agente di merge.  
  
 **Usa la pianificazione seguente per l'esecuzione dell'agente snapshot**  
 Accettare la pianificazione predefinita per l'esecuzione dell'agente snapshot oppure fare clic su **Cambia** per specificare una pianificazione diversa.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](publish/create-a-publication.md)   
 [Creare e applicare lo snapshot iniziale](create-and-apply-the-initial-snapshot.md)   
 [Visualizzare e modificare le proprietà della pubblicazione](publish/view-and-modify-publication-properties.md)   
 [Inizializzare una sottoscrizione con uno snapshot](initialize-a-subscription-with-a-snapshot.md)   
 [Pubblicare dati e oggetti di database](publish/publish-data-and-database-objects.md)   
 [Panoramica degli agenti di replica](agents/replication-agents-overview.md)  
  
  
