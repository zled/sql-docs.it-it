---
title: Sottoscrizioni aggiornabili | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8d9a0e7625d424dea66291cc8b9707d1bd660820
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="updatable-subscriptions"></a>Sottoscrizioni aggiornabili
  Con la replica transazionale, è consigliabile utilizzare i dati replicati in sola lettura. È tuttavia possibile modificare i dati replicati nel Sottoscrittore [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando le sottoscrizioni aggiornabili. Se è necessario modificare i dati nel Sottoscrittore, scegliere una delle opzioni seguenti in base ai requisiti specifici.  
  
|Tipo di sottoscrizione aggiornabile|Requisiti|  
|---------------------------------|------------------|  
|Aggiornamento immediato|Per aggiornare i dati nel Sottoscrittore è necessario che il server di pubblicazione e il Sottoscrittore siano connessi.|  
|Aggiornamento in coda|Per aggiornare i dati nel Sottoscrittore non è necessario che il server di pubblicazione e il Sottoscrittore siano connessi. È possibile eseguire gli aggiornamenti in modalità offline ed eseguire in seguito la sincronizzazione tra il server di pubblicazione e il Sottoscrittore.|  
  
## <a name="options"></a>Opzioni  
 **Replica modifiche del Sottoscrittore**  
 Selezionare questa casella di controllo nella colonna **Replica** per ogni Sottoscrittore che deve essere in grado di eseguire aggiornamenti. Per i Sottoscrittori che possono eseguire aggiornamenti, selezionare l'opzione appropriata nell'elenco a discesa della colonna **Commit nel server di pubblicazione** :  
  
-   Selezionare **Commit delle modifiche simultaneo** per una sottoscrizione ad aggiornamento immediato.  
  
-   Selezionare **Accoda le modifiche ed esegui il commit appena possibile** per una sottoscrizione ad aggiornamento in coda.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una sottoscrizione pull](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
