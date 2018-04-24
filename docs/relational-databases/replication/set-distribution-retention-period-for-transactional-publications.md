---
title: Impostare il periodo di memorizzazione per la distribuzione per le pubblicazioni transazionali | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
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
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d31de0f0406b0900f2bc84fee4f0a8f97cc19b7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Impostare il periodo di memorizzazione per la distribuzione per le pubblicazioni transazionali
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  È possibile specificare i periodi minimo e massimo di memorizzazione per la distribuzione nella finestra di dialogo **Proprietà database di distribuzione - \<DatabaseDistribuzione>**, a cui è possibile accedere dalla pagina **Generale** della finestra di dialogo **Proprietà database di distribuzione - \<ServerDistribuzione>**. Per altre informazioni sull'accesso a questa finestra di dialogo, vedere [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Per specificare il periodo di memorizzazione per la distribuzione  
  
1.  Nella pagina **Generale** della finestra di dialogo **Proprietà database di distribuzione - \<DatabaseDistribuzione>** fare clic sul pulsante delle proprietà (**…**) relativo al database di distribuzione.  
  
2.  Per specificare il periodo minimo di memorizzazione per la distribuzione, immettere un valore nella casella **per almeno** . Per specificare il periodo massimo di memorizzazione per la distribuzione, immettere un valore nella casella **non oltre** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Configura distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Scadenza e disattivazione delle sottoscrizioni](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
