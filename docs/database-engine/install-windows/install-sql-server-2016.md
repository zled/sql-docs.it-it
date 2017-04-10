---
title: "Installare SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "database di esempio AdventureWorks"
  - "installazione di SQL Server, preparazione per l'installazione"
  - "installazione [SQL Server]"
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
caps.latest.revision: 59
ms.author: "mikeray"
manager: "jhubbard"
---
# Installare SQL Server 2016
  SQL Server 2016 è un'applicazione a 64 bit. Di seguito sono riportati importanti dettagli su come ottenere SQL Server e su come eseguire l'installazione.

## <a name="installation-details"></a>Informazioni sull'installazione
  
*  **Opzioni**: eseguire l'installazione con l'Installazione guidata, il prompt dei comandi oppure sysprep
 
*  **Requisiti**: prima di eseguire l'installazione, rivedere i requisiti di installazione, i controlli di configurazione del sistema e le considerazioni sulla sicurezza in [Pianificazione di un'installazione di SQL Server](../../sql-server/install/planning-a-sql-server-installation.md) 

* **Processo**: per istruzioni dettagliate sul processo di installazione, vedere [Installazione per SQL Server](../../database-engine/install-windows/installation-for-sql-server-2016.md)

* **Esempi di database e di codice**: 
    * Non sono installati come parte predefinita dell'installazione di SQL Server 
    * Per installare tali elementi per edizioni non Express di SQL Server, vedere il [sito Web di CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843).
    * Per informazioni sul supporto per il codice di esempio e i database di esempio di SQL Server per SQL Server Express, vedere [Databases and Samples Overview](http://go.microsoft.com/fwlink/?LinkId=110391) (Panoramica di database ed esempi).
    

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

La posizione per il download di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dipende dall'edizione:

- **SQL Server Enterprise Edition, Standard Edition ed Express Edition** sono concessi in licenza per l'uso in ambienti di produzione. Per l'Enterprise Edition e la Standard Edition, richiedere il supporto di installazione al fornitore di software di fiducia. È possibile trovare informazioni sull'acquisto e una directory per i partner Microsoft nel [sito Web Microsoft per gli acquisti](https://www.microsoft.com/en-us/server-cloud/products/sql-server/overview.aspx). 

- Le **edizioni gratuite** sono disponibili nei collegamenti seguenti:

| Edizione | Description
|---------|--------
|[Developer Edition](http://myprodscussu1.app.vssubscriptions.visualstudio.com/Downloads?q=SQL%20Server%20Developer) | Set gratuito e completo di tutte le funzionalità del software SQL Server 2016 Enterprise Edition che consente agli sviluppatori di compilare, testare ed eseguire demo di applicazioni in un ambiente non di produzione. 
|[Express Edition](http://www.microsoft.com/download/details.aspx?id=52679)|  Database gratuito di base, ideale per la distribuzione di database di piccole dimensioni in ambienti di produzione. Consente di creare applicazioni guidate dai dati per desktop e server di piccole dimensioni, fino a 10 GB di spazio su disco. 
| [Evaluation Edition](http://technet.microsoft.com/evalcenter/mt130694) | Set completo di funzionalità del software SQL Server Enterprise Edition con un periodo di valutazione di 180 giorni.
   
 
  

## <a name="how-to-install-sql-server"></a>Come installare SQL Server
 
|Title|Description|  
|-----------|-----------------|  
|[Installare SQL Server 2016 in Server Core](../../database-engine/install-windows/install-sql-server-2016-on-server-core.md)|Vedere questo argomento per installare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in Windows Server Core.|  
|[Parametri di controllo di Controllo configurazione sistema](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|Descrive la funzione di controllo configurazione sistema (SCC).|  
|[Installare SQL Server 2016 dall'Installazione guidata &#40;programma di installazione&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)|Argomento contenente le procedure per un'installazione tipica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite l'Installazione guidata.|  
|[Installazione di SQL Server 2016 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|Argomento contenente le procedure, la sintassi di esempio e i parametri di installazione per l'esecuzione dell'installazione automatica.|  
|[Installare SQL Server 2016 tramite un file di configurazione](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|Argomento contenente procedure in cui vengono forniti la sintassi di esempio e i parametri di installazione per l'esecuzione del programma di installazione tramite un file di configurazione.|  
|[Installare SQL Server 2016 con SysPrep](../../database-engine/install-windows/install-sql-server-2016-using-sysprep.md)|Argomento contenente procedure che fornisce la sintassi di esempio e i parametri di installazione per l'esecuzione del programma di installazione con SysPrep.|  
|[Aggiungere funzionalità a un'istanza di SQL Server 2016 &#40;programma di installazione&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|Argomento contenente le procedure per l'aggiornamento dei componenti di un'istanza esistente di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Ripristinare un'installazione non riuscita di SQL Server 2016](../../database-engine/install-windows/repair-a-failed-sql-server-2016-installation.md)|Argomento contenente le procedure per il ripristino di un'installazione danneggiata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Rinominare un computer che ospita un'istanza autonoma di SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|Argomento contenente le procedure per l'aggiornamento dei metadati di sistema archiviati in sys.servers.|  
|[Installare gli aggiornamenti dei servizi di SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016-servicing-updates.md)|Argomento contenente le procedure per l'installazione di aggiornamenti per SQL Server 2016.|  
|[Visualizzare e leggere i file di log del programma di installazione di SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)|Argomento contenente le procedure per la verifica degli errori nei file di log del programma di installazione.|  
|[Convalidare un'installazione di SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)|Esaminare l'utilizzo del report SQL Discovery per verificare la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate nel computer.|  
  
  
## <a name="how-to-install-individual-components"></a>Come installare i singoli componenti  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Installare il motore di database di SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)|Viene descritto come installare e configurare il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Installare la replica di SQL Server](../../database-engine/install-windows/install-sql-server-replication.md)|Viene descritto come installare e configurare la replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Install Distributed Replay - Overview](../../tools/distributed-replay/install-distributed-replay-overview.md) (Installare Riesecuzione distribuita - Panoramica)|Vengono elencati gli argomenti sull'installazione della funzionalità Riesecuzione distribuita.|  
|[Install SQL Server Management Tools with SSMS](Install%20SQL%20Server%20Management%20Tools%20\(SSMS\).md) (Installare gli strumenti di gestione di SQL Server con SSMS)|Viene descritto come installare e configurare gli strumenti di gestione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Installare SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)|Vengono fornite considerazioni per l'installazione dei componenti di PowerShell per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  

## <a name="how-to-configure-sql-server"></a>Per configurare SQL Server  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Configurare Windows Firewall per consentire l'accesso a SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|In questo argomento viene fornita una panoramica della configurazione dei firewall e viene illustrato come configurare Windows Firewall.|  
|[Configurare un computer multihomed per l'accesso a SQL Server](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|In questo argomento viene descritto come configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e Windows Firewall con sicurezza avanzata per fornire le connessioni di rete a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un ambiente multihomed.|  
|[Configurare Windows Firewall per consentire l'accesso ad Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|Le procedure descritte in questo argomento consentono di configurare le impostazioni delle porte e del firewall necessarie per accedere ad [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint.|  
  
## <a name="related-sections"></a>Sezioni correlate  
[Funzionalità supportate dalle edizioni di SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
[Installare le funzionalità di business intelligence di SQL Server 2016](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
  [Installazione del cluster di failover di SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 
  
## <a name="see-also"></a>Vedere anche  

[Pianificazione di un'installazione di SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Eseguire l'aggiornamento a SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)   
 [Disinstallare SQL Server 2016](../../sql-server/install/uninstall-sql-server-2016.md)   
 [Soluzioni a disponibilità elevata &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  