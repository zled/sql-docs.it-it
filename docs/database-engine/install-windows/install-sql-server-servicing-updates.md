---
title: Installare gli aggiornamenti dei servizi di SQL Server 2016 | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 08/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c0e1316d3444a08aaf114de18d1b7d9f5450aa9f
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-servicing-updates"></a>Installare gli aggiornamenti di manutenzione per SQL Server
  In questo argomento vengono fornite informazioni sull'installazione degli aggiornamenti per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. In questa sezione vengono fornite informazioni sui seguenti argomenti:  
  
-   Installazione di aggiornamenti per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] durante una nuova installazione  
  
-   Installazione di aggiornamenti per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dopo che è stato installato.  
  
 Si consiglia agli clienti di valutare e installare tempestivamente gli ultimi aggiornamenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per assicurarsi che i sistemi dispongano degli aggiornamenti di sicurezza più recenti.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-during-a-new-installation"></a>Installazione di aggiornamenti per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] durante una nuova installazione  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Il programma di installazione integra gli aggiornamenti più recenti del pacchetto con l'installazione del prodotto principale in modo che quest'ultimo e i relativi aggiornamenti applicabili vengano installati contemporaneamente. Aggiornamento prodotto consente la ricerca degli aggiornamenti applicabili da:  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Windows Server Update Services (WSUS)  
  
-   Cartella locale  
  
-   Condivisione di rete  
  
 Dopo avere individuato le versioni più recenti degli aggiornamenti applicabili, questi vengono scaricati e integrati dal programma di installazione con il processo di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corrente. Tramite l'aggiornamento del prodotto è possibile includere un aggiornamento cumulativo, un Service Pack o un Service Pack con aggiornamento cumulativo.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>Installazione di aggiornamenti per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dopo che è stato installato  
 In un'istanza installata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]si consiglia di applicare gli aggiornamenti della sicurezza e gli aggiornamenti critici più recenti, inclusi General Distribution Release (GDR), Service Pack e aggiornamenti cumulativi. Per ulteriori informazioni, vedere l' [annuncio di marzo 2016 relativo al modello di manutenzione incrementale di SQL Server](http://blogs.msdn.microsoft.com/sqlreleaseservices/announcing-updates-to-the-sql-server-incremental-servicing-model-ism/). 
  
 Gli aggiornamenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update (MU), Windows Server Update Services (WSUS) e Area download Microsoft. Sicurezza e aggiornamenti Critici per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update. Per essere in grado di vedere questi aggiornamenti è necessario a scegliere MU tramite Windows Update nel Pannello Controllo.  
  
 Quando si riceve un aggiornamento tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, verrà effettuato l'aggiornamento in modalità automatica di tutte le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alla versione più recente. Per maggiore flessibilità o se non si dispone di Internet o dell'accesso a WSUS, sarà necessario ottenere gli aggiornamenti dall'Area download [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Installare SQL Server 2016 dall'Installazione guidata &#40;programma di installazione&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)   
 [Aggiungere funzionalità a un'istanza di SQL Server 2016 &#40;programma di installazione&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)   
 [Ripristinare un'installazione non riuscita di SQL Server 2016](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)  
  
  

