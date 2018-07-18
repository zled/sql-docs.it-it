---
title: Password server di distribuzione | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a352eef0c9be945133d1883fd93f63f54f80e697
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309331"
---
# <a name="distributor-password"></a>Password server di distribuzione
  Se nella pagina **Server di pubblicazione** di questa procedura guidata uno più server di pubblicazione sono stati abilitati all'utilizzo del server corrente come server di distribuzione remoto, è necessario specificare una password per la connessione eseguita dalla replica tra il server di pubblicazione e il server di distribuzione remoto utilizzando l'account di accesso **distributor_admin** . È necessario specificare la stessa password per ogni server di pubblicazione che utilizza questo server di distribuzione remoto nella pagina **Password amministrativa** della Creazione guidata nuova pubblicazione o della Configurazione guidata distribuzione. Per altre informazioni sulla sicurezza dei database di distribuzione, vedere [Proteggere il database di distribuzione](security/secure-the-distributor.md).  
  
## <a name="options"></a>Opzioni  
 **Password**  
 Consente di immettere una password complessa per la connessione tra il server di pubblicazione e il server di distribuzione remoto.  
  
 **Conferma password**  
 Consente di immettere nuovamente la password per verificarne la corretta immissione.  
  
## <a name="see-also"></a>Vedere anche  
 [Configura distribuzione](configure-distribution.md)   
 [Configurare la pubblicazione e la distribuzione](configure-publishing-and-distribution.md)  
  
  
