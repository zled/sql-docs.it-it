---
title: "Proprietà database di distribuzione | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords:
- Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7e086caef0d106066a3f8a9f42d1bbd51d473826
ms.lasthandoff: 04/11/2017

---
# <a name="distribution-database-properties"></a>Proprietà database di distribuzione
  La finestra di dialogo **Proprietà database di distribuzione** consente di visualizzare varie proprietà e di impostare il periodo di memorizzazione della transazione e della cronologia per il database.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Il nome del database di distribuzione, il cui valore predefinito è "distribution" (sola lettura).  
  
 **Percorsi dei file**  
 Il percorso del file di database e del file di log (sola lettura).  
  
 **Periodo di memorizzazione della transazione**  
 Questa proprietà è nota anche come periodo di memorizzazione della distribuzione. Si tratta della quantità di tempo di memorizzazione delle transazioni ai fini della replica transazionale. Per altre informazioni, vedere [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Periodo di memorizzazione cronologia**  
 Quantità di tempo di memorizzazione dei metadati della cronologia ai fini di tutti i tipi di replica.  
  
 **Sicurezza agente di lettura coda**  
 L'agente di lettura coda viene utilizzato dalla replica transazionale con sottoscrizioni ad aggiornamento in coda. L'agente di lettura coda viene creato automaticamente se si seleziona **Creazione di una pubblicazione transazionale con aggiornamento delle sottoscrizioni** nella pagina **Tipo di pubblicazione** della Creazione guidata nuova pubblicazione. Fare clic su **Impostazioni di sicurezza** per modificare l'account nell'ambito del quale l'agente viene eseguito e si connette al server di distribuzione.  
  
 In questa pagina è inoltre possibile creare un agente di lettura coda selezionando **Crea agente di lettura coda** . L'opzione è disabilitata se l'agente è già stato creato.  
  
 Ulteriori informazioni sulla connessione relative all'agente di lettura coda vengono specificate in due posizioni:  
  
-   L'agente si connette al server di pubblicazione mediante le credenziali specificate nella finestra di dialogo **Proprietà server di pubblicazione** che è disponibile nella pagina **Server di pubblicazione** della finestra di dialogo **Proprietà server di distribuzione** .  
  
-   L'agente si connette al Sottoscrittore mediante le credenziali specificate per l'agente di distribuzione in Creazione guidata nuova sottoscrizione.  
  
 Per altre informazioni, vedere  [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Creare una sottoscrizione pull](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
