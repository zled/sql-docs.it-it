---
title: Impostazioni monitoraggio log shipping | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e93dde0e413ab7f7303d0f8404cdc4311edf8aa7
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="log-shipping-monitor-settings"></a>Impostazioni monitoraggio log shipping
  Utilizzare questa pagina per configurare e modificare le proprietà del server di monitoraggio del log shipping.  
  
 Per approfondimenti sui concetti correlati al log shipping, vedere [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
## <a name="options"></a>Opzioni  
 **Istanza server di monitoraggio**  
 Visualizza il nome dell'istanza del server attualmente configurato come server di monitoraggio per la configurazione per il log shipping.  
  
 **Connect**  
 Consente di scegliere un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da utilizzare come server di monitoraggio e di connettersi a tale istanza. È necessario che l'account utilizzato per la connessione sia membro del ruolo predefinito del server sysadmin nell'istanza del server secondario.  
  
 **Tramite rappresentazione dell'account proxy del processo**  
 Consente al log shipping di rappresentare l'account proxy di SQL Server Agent durante la connessione all'istanza del server di monitoraggio. Per aggiornare lo stato delle operazioni di log shipping i processi di backup, di copia e di ripristino devono potersi connettere al server di monitoraggio.  
  
 **Tramite l'account di accesso di SQL Server seguente**  
 Consente al log shipping di utilizzare un account di accesso specifico di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante la connessione all'istanza del server di monitoraggio. Per aggiornare lo stato delle operazioni di log shipping i processi di backup, di copia e di ripristino devono potersi connettere al server di monitoraggio. Se si desidera che il log shipping utilizzi un account di accesso specifico di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , selezionare questa opzione e quindi specificare l'account di accesso e la password.  
  
 **Elimina cronologia dopo**  
 Consente di specificare per quanto tempo le informazioni sulla cronologia di log shipping vengono mantenute sul server di monitoraggio prima di essere eliminate.  
  
 **Nome processo**  
 Indica il nome del processo di gestione degli avvisi di SQL Server Agent utilizzato dal log shipping per generare avvisi in caso di superamento dei valori soglia per il backup o il ripristino. Al momento della prima creazione di tale processo è possibile modificarne il nome nell'apposita casella.  
  
 **Pianificazione**  
 Indica la pianificazione corrente del processo di gestione degli avvisi di SQL Server Agent.  
  
 **Modifica**  
 Consente di modificare i parametri del processo di gestione degli avvisi di SQL Server Agent.  
  
 **Disabilita questo processo**  
 Consente di sospendere il processo di gestione degli avvisi di SQL Server Agent.  
  
  
