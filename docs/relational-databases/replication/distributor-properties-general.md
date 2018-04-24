---
title: Proprietà database di distribuzione, Generale | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.distproperties.general.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: ab4120ec-e524-4c0c-8b48-f2f40adb1a3b
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72a19533f68de783317fbea0b8305d9f474b50bb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="distributor-properties-general"></a>Proprietà server di distribuzione, Generale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La pagina **Generale** della finestra di dialogo **Proprietà server di distribuzione** consente di aggiungere ed eliminare i database di distribuzione e di impostarne le relative proprietà.  
  
 Nel database di distribuzione vengono archiviati i metadati e i dati di cronologia relativi a tutti i tipi di replica, nonché le transazioni per la replica transazionale. In molti casi, è sufficiente un singolo database di distribuzione. Se tuttavia un singolo server di distribuzione viene utilizzato da più server di pubblicazione, è opportuno creare un database di distribuzione per ogni server di pubblicazione, in modo da garantire che il flusso di dati di ogni database di distribuzione risulti distinto.  
  
## <a name="options"></a>Opzioni  
 **Database**  
 Nella griglia delle proprietà **Database** vengono visualizzati il nome e le proprietà di memorizzazione dei database di distribuzione nel server di distribuzione. **Periodo memorizzazione transazioni** rappresenta il periodo di tempo per cui le transazioni rimangono archiviate per la replica transazionale. Il periodo di memorizzazione della transazione è inoltre noto come periodo di memorizzazione per la distribuzione. **Periodo memorizzazione cronologia** equivale invece al periodo di tempo per cui rimangono archiviati i metadati della cronologia per ogni tipo di replica. Per altre informazioni sul periodo di memorizzazione, vedere [Scadenza e disattivazione delle sottoscrizioni](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 Fare clic sul pulsante delle proprietà **...** nella griglia delle proprietà **Database** per aprire la finestra di dialogo **Proprietà database di distribuzione** .  
  
 **Nuova**  
 Fare clic su questo pulsante per creare un nuovo database di distribuzione.  
  
 **Elimina**  
 Selezionare un database di distribuzione esistente nella griglia delle proprietà **Database** e scegliere **Elimina** per eliminarlo. Non è possibile eliminare il database di distribuzione se ne esiste uno solo, poiché ogni server di distribuzione deve disporre di almeno un database di distribuzione. Per eliminare tutti i database di distribuzione, è necessario disabilitare la distribuzione nel computer. Per altre informazioni, vedere [Disabilitare la pubblicazione e la distribuzione](../../relational-databases/replication/disable-publishing-and-distribution.md).  
  
 **Impostazioni predefinite profili**  
 Fare clic su questo pulsante per accedere ai profili dell'agente di replica nella finestra di dialogo **Profili agenti** . Per ulteriori informazioni sui profili, vedere [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Configura distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
