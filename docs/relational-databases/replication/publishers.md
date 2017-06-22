---
title: Server di pubblicazione | Microsoft Docs
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
- sql13.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cbddd946268cf097c1b088b9c25c3adade11d39d
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="publishers"></a>Server di pubblicazione
  È possibile concedere ad altri server di pubblicazione l'autorizzazione per l'utilizzo del server di distribuzione. Tenere presente che, se si abilita un server di pubblicazione per l'utilizzo di questo server come server di distribuzione remoto, il server non diventerà un server di pubblicazione. È infatti necessario connettersi al server di pubblicazione, configurarlo per la pubblicazione e selezionare questo server come server di distribuzione. Utilizzando la Creazione guidata nuova pubblicazione è possibile configurare il server di pubblicazione e selezionare un server di distribuzione.  
  
 I server selezionati come server di pubblicazione utilizzeranno il database di distribuzione specificato nella pagina **Database di distribuzione** della creazione guidata. Se si desidera utilizzare un database di distribuzione diverso, non abilitare il server di pubblicazione in questa fase. Utilizzare invece la finestra di dialogo **Proprietà server di distribuzione** per aggiungere i server di pubblicazione dopo aver completato la Configurazione guidata distribuzione.  
  
## <a name="options"></a>Opzioni  
 **Server di pubblicazione**  
 Consente di selezionare i server autorizzati all'utilizzo del server di distribuzione corrente. Fare clic sul pulsante delle proprietà (**...**) accanto al server di pubblicazione per visualizzare e impostare proprietà aggiuntive.  
  
 **Aggiungi**  
 Se il server desiderato non è incluso nell'elenco, fare clic su **Aggiungi** per aggiungere un server di pubblicazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o Oracle all'elenco dei server di pubblicazione disponibili.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Creare una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)  
  
  
