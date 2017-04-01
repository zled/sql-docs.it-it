---
title: "Aggiornare gli strumenti di gestione di SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti di gestione, aggiornamento"
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
caps.latest.revision: 19
author: "stevestein"
ms.author: "sstein"
manager: "jhubbard"
caps.handback.revision: 19
---
# Aggiornare gli strumenti di gestione di SQL Server
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supporta l'aggiornamento da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive. In questo argomento vengono fornite informazioni sul supporto e il comportamento dell'aggiornamento degli strumenti e i componenti di gestione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], quali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Posta elettronica database, Piani di manutenzione, XPStar e XPWeb.  
  
> [!IMPORTANT]  
>  Per le installazioni locali, è necessario eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come amministratore. Se si esegue il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio che dispone di autorizzazioni di lettura ed esecuzione per tale condivisione remota.  
  
## Problemi di aggiornamento noti  
 Prima di eseguire l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], considerare i problemi indicati di seguito.  
  
### Per tutti gli scenari di aggiornamento:  
  
-   Tutti i server TSX devono essere aggiornati prima dell'aggiornamento del server MSX. Per altre informazioni su MSX/TSX in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Amministrazione automatizzata in un'organizzazione](../../ssms/agent/automated-administration-across-an-enterprise.md).  
  
-   Tutti i componenti inclusi in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere aggiornati simultaneamente. I numeri di versione dei componenti del [!INCLUDE[ssDE](../../includes/ssde-md.md)], di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] devono essere identici in un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   È possibile aggiungere componenti a un'installazione esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel momento in cui si esegue l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per altre informazioni, vedere [Eseguire l'aggiornamento a SQL Server 2016 usando l'Installazione guidata &#40;Programma di installazione&#41;](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gli strumenti client ad esempio [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], [!INCLUDE[ssDE](../../includes/ssde-md.md)]Ottimizzazione guidata, sqlcmd e osql, non vengono aggiornati a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Gli strumenti client vengono invece eseguiti in modalità affiancata con gli strumenti delle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supporta l'importazione delle impostazioni dalle versioni precedenti degli strumenti client di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Durante l'aggiornamento, l'autenticazione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà aggiornata dall'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'autenticazione di Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] L'autenticazione non è supportata in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   I dati per processi e avvisi verranno mantenuti durante l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Se nell'istanza da aggiornare viene utilizzato SQLMail, le stored procedure estese associate saranno supportate e attivate in seguito all'aggiornamento. In caso contrario, saranno disattivate.  
  
-   Posta elettronica database, anche noto come SQLiMail, verrà aggiornato con il componente [!INCLUDE[ssDE](../../includes/ssde-md.md)] di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per impostazione predefinita, Posta elettronica database verrà utilizzato in seguito all'aggiornamento. Qualsiasi aggiornamento dello schema deve essere riconciliato con uno script di aggiornamento in seguito all'aggiornamento.  
  
## Vedere anche  
 [Aggiornamenti di versione ed edizione supportati](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)   
 [Eseguire l'aggiornamento a SQL Server 2016 usando l'Installazione guidata &#40;Programma di installazione&#41;](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)  
  
  