---
title: Password server di distribuzione | Microsoft Docs
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
- sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e1743e9d64d586feb735fdea05cf9bb57a2e06b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="distributor-password"></a>Password server di distribuzione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Se nella pagina **Server di pubblicazione** di questa procedura guidata uno più server di pubblicazione sono stati abilitati all'utilizzo del server corrente come server di distribuzione remoto, è necessario specificare una password per la connessione eseguita dalla replica tra il server di pubblicazione e il server di distribuzione remoto utilizzando l'account di accesso **distributor_admin** . È necessario specificare la stessa password per ogni server di pubblicazione che utilizza questo server di distribuzione remoto nella pagina **Password amministrativa** della Creazione guidata nuova pubblicazione o della Configurazione guidata distribuzione. Per altre informazioni sulla sicurezza dei database di distribuzione, vedere [Proteggere il database di distribuzione](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="options"></a>Opzioni  
 **Password**  
 Consente di immettere una password complessa per la connessione tra il server di pubblicazione e il server di distribuzione remoto.  
  
 **Conferma password**  
 Consente di immettere nuovamente la password per verificarne la corretta immissione.  
  
## <a name="see-also"></a>Vedere anche  
 [Configura distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
