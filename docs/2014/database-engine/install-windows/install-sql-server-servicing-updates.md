---
title: Installare gli aggiornamenti di manutenzione di SQL Server 2014 | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c7601914ed32def54b153282a90b51629b1380b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169266"
---
# <a name="install-sql-server-2014-servicing-updates"></a>Installare gli aggiornamenti dei servizi di SQL Server 2014
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
  
 Dopo avere individuato le versioni più recenti degli aggiornamenti applicabili, questi vengono scaricati e integrati dal programma di installazione con il processo di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corrente. Tramite l'aggiornamento del prodotto è possibile includere un aggiornamento cumulativo, un Service Pack o un Service Pack con aggiornamento cumulativo. Funzionalità Aggiornamento prodotto è un'estensione del [funzionalità di integrazione](http://go.microsoft.com/fwlink/?LinkId=219945) disponibile in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>Installazione di aggiornamenti per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dopo che è stato installato  
 In un'istanza installata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], si consiglia di applicare tutti gli aggiornamenti disponibili: General Distribution Release (GDR - gli aggiornamenti critici/sicurezza), Service Pack (SP), nonché il CU disponibile più recente Cumulative Update ().  
  
 A seconda del tipo di rilascio di manutenzione, gli aggiornamenti di SQL Server sono disponibili tramite Microsoft Update (MU), Microsoft Download Center e/o l'hotfix di supporto tecnico clienti Server. Gli aggiornamenti critici e della protezione per SQL Server sono forniti automaticamente da Microsoft Update (per essere in grado di vedere questi aggiornamenti che è necessario registrarsi a Microsoft Update tramite Windows Update nel Pannello di controllo). Service Pack sono disponibili in Microsoft Update come download facoltativo/importante, nonché nell'area download. Gli aggiornamenti cumulativi sono disponibili nel server di download dell'hotfix Microsoft fornite negli articoli CU Knowledge Base.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare SQL Server 2014 dall'installazione guidata di &#40;programma di installazione&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [Aggiungere funzionalità a un'istanza di SQL Server 2014 &#40;programma di installazione&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [Rimuovere un'installazione di SQL Server 2014](repair-a-failed-sql-server-installation.md)  
  
  