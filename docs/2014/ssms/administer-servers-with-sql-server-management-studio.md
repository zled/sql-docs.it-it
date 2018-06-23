---
title: Amministrare server con SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9b14e5ecd7cc10a5a3cb5b50b847e3945f9633ae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157886"
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Amministrazione di server con SQL Server Management Studio
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] è un client di amministrazione completo e integrato progettato per soddisfare il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] i requisiti di gestione di server dell'amministratore. In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]le attività di amministrazione vengono eseguite utilizzando Esplora oggetti, che consente di connettersi a qualsiasi server del gruppo [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e di visualizzarne graficamente il contenuto. Un server può essere un'istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)], di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] o [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 I componenti di [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] includono Server registrati, Esplora oggetti, Esplora soluzioni, Esplora modelli, la pagina Dettagli Esplora oggetti e la finestra del documento. Per visualizzare uno strumento, scegliere il nome desiderato dal menu **Visualizza** . Per visualizzare lo strumento Editor di query, fare clic sul pulsante **Nuova query** sulla barra degli strumenti.  
  
> [!IMPORTANT]  
>  Per impostazione predefinita, il traffico di rete tra [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non è crittografato. In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] lavorare con dati sensibili (comprese le password) solo dopo aver stabilito una connessione crittografata. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 Utilizzare [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] per:  
  
-   Registrare server.  
  
-   Connettersi a un'istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)], di [!INCLUDE[ssAS](../includes/ssas-md.md)], [!INCLUDE[ssRS](../includes/ssrs-md.md)] o [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
-   Configurare le proprietà del server.  
  
-   Gestire database e oggetti [!INCLUDE[ssAS](../includes/ssas-md.md)] come ad esempio cubi, dimensioni e assembly.  
  
-   Creare oggetti come ad esempio database, tabelle, cubi, utenti di database e account di accesso.  
  
-   Gestire file e filegroup.  
  
-   Collegare o scollegare database.  
  
-   Avviare strumenti di scripting.  
  
-   Gestire la sicurezza.  
  
-   Visualizzare registri di sistema.  
  
-   Monitorare l'attività corrente.  
  
-   Configurare la replica.  
  
-   Gestire indici full-text.  
  
 Per avviare e arrestare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)   
 [Visualizzare o modificare le proprietà del server &#40;SQL Server&#41;](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
  
  