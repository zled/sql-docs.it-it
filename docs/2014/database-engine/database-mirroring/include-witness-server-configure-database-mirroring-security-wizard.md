---
title: Aggiunta server di controllo del mirroring (Configurazione guidata sicurezza mirroring del database) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6d5adcdc5d038dac082c27888e78db3578b1f307
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157589"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a>Aggiunta server di controllo del mirroring (Configurazione guidata sicurezza mirroring del database)
  Utilizzare questa pagina per specificare se si desidera aggiungere un server di controllo del mirroring in questa configurazione di sicurezza per il mirroring del database.  
  
 **Per configurare il mirroring del database tramite SQL Server Management Studio**  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Avvio della Configurazione guidata sicurezza mirroring del database &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Opzioni  
 **Sì**  
 Fare clic su questo pulsante per aggiungere un'istanza del server di controllo del mirroring nella configurazione di sicurezza. Il server di controllo del mirroring è necessario per la modalità a disponibilità elevata con failover automatico, che supporta il failover automatico sull'istanza del server mirror in caso si verifichi un errore nell'istanza del server principale.  
  
 **No**  
 Fare clic su questo pulsante per impostare la configurazione di sicurezza senza un server di controllo del mirroring.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del database &#40;Pagina Mirroring&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Mirroring del database &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Server di controllo del mirroring del database](database-mirroring-witness.md)  
  
  