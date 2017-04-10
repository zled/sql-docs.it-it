---
title: "Configurazione superficie di attacco | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "riduzione di superficie di attacco"
  - "aggiornamento di SQL Server, sicurezza"
  - "Configurazione superficie di attacco [SQL Server]"
  - "configurazione della superficie di attacco [SQL Server], informazioni"
  - "superficie di attacco [SQL Server]"
  - "installazione di SQL Server, sicurezza"
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
caps.latest.revision: 79
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 79
---
# Configurazione superficie di attacco
  Nella configurazione predefinita delle nuove installazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] molte funzionalità non sono abilitate. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installa in modo selettivo e avvia solo le funzionalità e i servizi chiave in modo da ridurre al minimo il numero di funzionalità che potrebbero essere attaccate da un utente malintenzionato. L'amministratore di sistema può modificare i valori predefiniti al momento dell'installazione e abilitare o disabilitare in modo selettivo le caratteristiche di un'istanza in esecuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Alcuni componenti, inoltre, potrebbero non essere disponibili durante la connessione da altri computer fino a quando non si configurano i protocolli.  
  
> [!NOTE]  
>  Diversamente dalle nuove installazioni, durante un aggiornamento non è disabilitato alcun servizio o caratteristica esistente, ma è possibile applicare opzioni di configurazione della superficie di attacco aggiuntive al termine dell'aggiornamento.  
  
## Protocolli e opzioni di connessione e avvio  
 Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di avviare e arrestare servizi, configurare le opzioni di avvio e abilitare protocolli e altre opzioni di connessione.  
  
#### Per avviare Gestione configurazione SQL Server  
  
1.  Fare clic sul menu **Start** , scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Strumenti di configurazione**e quindi **Gestione configurazione SQL Server**.  
  
    -   Usare l'area **Servizi di SQL Server** per avviare i componenti e configurare le opzioni iniziali automatiche.  
  
    -   Usare l'area **Configurazione di rete SQL Server** per abilitare protocolli e opzioni di connessione, ad esempio le porte TCP/IP fisse, o per forzare la crittografia.  
  
 Per altre informazioni, vedere [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md). La connettività remota può dipendere anche dalla corretta configurazione di un firewall. Per altre informazioni, vedere [Configurare Windows Firewall per consentire l'accesso a SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## Abilitazione e disabilitazione di caratteristiche  
 L'abilitazione e la disabilitazione delle caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere configurata tramite facet in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Per configurare la superficie di attacco tramite facet  
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] connettersi a un componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  In Esplora oggetti fare clic con il pulsante destro del mouse sul server, quindi scegliere **Facet**.  
  
3.  Nella finestra di dialogo **Visualizza facet** espandere l'elenco **Facet** e selezionare il facet **Surface Area Configuration** appropriato tra **Configurazione superficie di attacco**, **Configurazione superficie di attacco per Analysis Services** o **Configurazione superficie di attacco per Reporting Services**.  
  
4.  Nell'area **Proprietà facet** selezionare i valori desiderati per ogni proprietà.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Per controllare periodicamente la configurazione di un facet, utilizzare la gestione basata su criteri. Per altre informazioni sulla gestione basata su criteri, vedere [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md).  
  
 È possibile impostare le opzioni del [!INCLUDE[ssDE](../../includes/ssde-md.md)] anche tramite la stored procedure **sp_configure**. Per altre informazioni, vedere [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 Per modificare la proprietà **EnableIntegrated Security** di [!INCLUDE[ssRS](../../includes/ssrs-md.md)], usare le impostazioni delle proprietà in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per modificare la proprietà **Pianificazione eventi e recapito report** e la proprietà **Accesso HTTP e servizi Web**, modificare il file di configurazione **RSReportServer.config**.  
  
## Opzioni del prompt dei comandi  
 Usare il cmdlet **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di PowerShell per richiamare i criteri di configurazione della superficie di attacco. Per altre informazioni, vedere [Utilizzo di cmdlet del motore di database](../../relational-databases/scripting/use-the-database-engine-cmdlets.md).  
  
## Endpoint SOAP e di Service Broker  
 Per disabilitare gli endpoint, utilizzare la gestione basata su criteri. Per creare e modificare le proprietà degli endpoint, usare [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md) e [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
## Contenuto correlato  
 [Centro di sicurezza per il motore di database di SQL Server e il database SQL di Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  