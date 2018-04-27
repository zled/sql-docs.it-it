---
title: Amministrare server con SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba0256a3cf46fe00015901137699cca7820c31fe
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Amministrazione di server con SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] è un client di amministrazione completo e integrato progettato per soddisfare i requisiti di gestione del server dell'amministratore di database SQL di Azure e [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] . In [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)]le attività di amministrazione vengono eseguite utilizzando Esplora oggetti, che consente di connettersi a qualsiasi server del gruppo [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] e di visualizzarne graficamente il contenuto. Un server può essere un'istanza del [!INCLUDE[ssDE](../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] o di database SQL di Azure.  
  
I componenti di [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] includono Server registrati, Esplora oggetti, Esplora soluzioni, Esplora modelli, la pagina Dettagli Esplora oggetti e la finestra del documento. Per visualizzare uno strumento, scegliere il nome desiderato dal menu **Visualizza** . Per visualizzare lo strumento Editor di query, fare clic sul pulsante **Nuova query** sulla barra degli strumenti.  
  
> [!IMPORTANT]  
> Per impostazione predefinita, il traffico di rete tra [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] e [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] non è crittografato. In [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] lavorare con dati sensibili (comprese le password) solo dopo aver stabilito una connessione crittografata. Per altre informazioni, vedere [Procedura: Abilitazione di connessioni crittografate al Motore di database (Gestione configurazione SQL Server)](http://msdn.microsoft.com/en-us/e1e55519-97ec-4404-81ef-881da3b42006).  
  
Utilizzare [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] per:  
  
-   Registrare server.  
  
-   Connettersi a un'istanza del [!INCLUDE[ssDE](../includes/ssde_md.md)], [!INCLUDE[ssAS](../includes/ssas_md.md)], [!INCLUDE[ssRS](../includes/ssrs_md.md)],  [!INCLUDE[ssIS](../includes/ssis_md.md)] o di database SQL di Azure.  
  
-   Configurare le proprietà del server.  
  
-   Gestire database e oggetti [!INCLUDE[ssAS](../includes/ssas_md.md)] come ad esempio cubi, dimensioni e assembly.  
  
-   Creare oggetti come ad esempio database, tabelle, cubi, utenti di database e account di accesso.  
  
-   Gestire file e filegroup.  
  
-   Collegare o scollegare database.  
  
-   Avviare strumenti di scripting.  
  
-   Gestire la sicurezza.  
  
-   Visualizzare registri di sistema.  
  
-   Monitorare l'attività corrente.  
  
-   Configurare la replica.  
  
-   Gestire indici full-text.  
  
Per avviare e arrestare [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] o [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] Agent, utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
[Utilizzo di SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Procedura: Visualizzazione o modifica delle proprietà del server (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/55f3ac04-5626-4ad2-96bd-a1f1b079659d)  
  
