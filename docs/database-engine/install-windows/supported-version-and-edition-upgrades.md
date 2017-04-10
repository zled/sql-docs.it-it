---
title: "Aggiornamenti di versione ed edizione supportati | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "componenti [SQL Server], aggiunta a installazioni esistenti"
  - "versioni [SQL Server], aggiornamento"
  - "aggiornamento di SQL Server, aggiornamenti supportati"
  - "supporto di lingue diverse"
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
caps.latest.revision: 148
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 147
---
# Aggiornamenti di versione ed edizione supportati
  È possibile eseguire l'aggiornamento da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. In questo argomento sono elencati i percorsi di aggiornamento supportati da queste versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e gli aggiornamenti di edizione supportati per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## Elenco di controllo preliminare all'aggiornamento  
  
-   Prima di effettuare l'aggiornamento da un'edizione all'altra di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], verificare che le funzionalità attualmente utilizzate siano supportate nell'edizione da aggiornare.  
  
-   Prima di aggiornare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], abilitare l'autenticazione di Windows per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e verificare la configurazione predefinita, ovvero che l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sia membro del gruppo sysadmin di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Per effettuare l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è necessario che nel computer sia in esecuzione un sistema operativo supportato. Per altre informazioni, vedere [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md).  
  
-   L'aggiornamento verrà bloccato se è un riavvio è sospeso.  
  
-   L'aggiornamento verrà bloccato se il servizio Windows Installer non è in esecuzione.  
  
## Scenari non supportati  
  
-   La presenza di istanze di versioni diverse di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] non è supportata. I numeri di versione dei componenti del [!INCLUDE[ssDE](../../includes/ssde-md.md)], di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] devono essere identici in un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   SQL Server 2016 è disponibile solo per piattaforme a 64 bit. L'aggiornamento tra piattaforme diverse non è supportato. Non è possibile aggiornare un'istanza a 32 bit di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un'istanza a 64 bit nativa tramite il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tuttavia, è possibile eseguire il backup o scollegare database da un'istanza a 32 bit di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], quindi ripristinarli o collegarli a una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64 bit) se i database non sono pubblicati in replica. È necessario ricreare tutti gli account di accesso e gli altri oggetti utente nei database di sistema master, msdb e model.  
  
-   Non è possibile aggiungere nuove funzionalità durante l'aggiornamento dell'istanza esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dopo aver aggiornato un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è possibile aggiungere funzionalità tramite il programma di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per altre informazioni, vedere [Aggiungere funzionalità a un'istanza di SQL Server 2016 &#40;programma di installazione&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md).  
 
-   I cluster di failover non sono supportati nella modalità WOW.  
  
-   L'aggiornamento da una qualsiasi versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è supportato.  
  
## Aggiornamenti da versioni precedenti a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 
SQL Server 2016 supporta l'aggiornamento dalle versioni di SQL Server seguenti:
 
- SQL Server 2008 SP3 o versione successiva
- SQL Server 2008 R2 SP2 o versione successiva
- SQL Server 2012 SP2 o versione successiva
- SQL Server 2014 o versione successiva 
 

  
> [!NOTE]  
>  Per aggiornare i database in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vedere [il supporto per la versione 2005](#SupportFor2005).  
  
 Nella tabella seguente sono elencati gli scenari di aggiornamento supportati da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Aggiornamento da|Percorso di aggiornamento supportato|  
|------------------|----------------------------|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Small Business|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Workgroup|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Datacenter|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Small Business|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Workgroup|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Sviluppatore <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express <br/> <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Business Intelligence|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Valutazione di SP2|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Copia di valutazione <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Sviluppatore|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Sviluppatore|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Sviluppatore <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Sviluppatore|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Copia di valutazione|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Copia di valutazione <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Sviluppatore|  
|[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] versione finale candidata* |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise |  
|[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] Sviluppatore |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise | 

 \* Il supporto Microsoft per l'aggiornamento da software con versioni finali candidate è destinato ai clienti che hanno partecipato al programma TAP (Technology Adoption Program). 

   
###  <a name="SupportFor2005"></a> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Supporto per [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
 In questa sezione viene illustrato il supporto di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] è possibile effettuare le operazioni seguenti:  
  
-   Collegare un database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (file ldf/mdf) all'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] del motore di database.  
  
-   Ripristinare un database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] all'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] del motore di database da un backup.  
  
-   Eseguire il backup di un cubo di [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] e il ripristino in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Quando un database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] viene aggiornato a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], il livello di compatibilità del database viene modificato da 90 a 100. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] i valori validi per il livello di compatibilità del database sono 100, 110, 120 e 130. In [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md) viene illustrato in che modo la modifica del livello di compatibilità possa influire sulle applicazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Tutti gli scenari non specificati nell'elenco sopra indicato non sono supportati, inclusi, a titolo esemplificativo, i seguenti:  
  
-   Installazione di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nello stesso computer (side-by-side).  
  
-   Utilizzo di un'istanza di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] come membro della topologia di replica che implica un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Configurazione del mirroring del database tra istanze di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
-   Backup del log delle transazioni con log shipping tra istanze di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
-   Configurazione di server collegati tra istanze di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
-   Gestione di un'istanza di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Collegamento di un cubo di [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Connessione a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Gestione di un servizio [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Supporto per componenti personalizzati di terze parti di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Integration Services, ad esempio esecuzione e aggiornamento.  
  
## [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Aggiornamento delle edizioni  
 Nella tabella seguente sono elencati gli scenari di aggiornamento delle edizioni supportati in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Per istruzioni dettagliate sull'esecuzione di un aggiornamento dell'edizione, vedere [Eseguire l'aggiornamento a un'edizione diversa di SQL Server 2016 &#40;programma di installazione&#41;](../../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-2016-setup.md).  
  
|Aggiornamento da|Aggiornamento a|  
|------------------|----------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL e Core)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise |  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation Enterprise**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Server+CAL o Core) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> L'aggiornamento da Evaluation (edizione gratuita) a qualsiasi edizione a pagamento è supportato per le installazioni autonome, ma non per le installazioni cluster.|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Server+CAL o Core)|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Server+CAL o Core) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Server+CAL o Core) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express*|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Server+CAL o Core) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Sviluppatore <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
  
 È inoltre possibile inoltre eseguire un aggiornamento dell'edizione tra [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+licenza CAL) e [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Core):  
  
|Aggiornamento dell'edizione da|Aggiornamento delle edizioni a|  
|--------------------------|------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Server+CAL)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Core)|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Core)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licenza Server+CAL)|  
  
 \* Applicabile anche a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express with Tools e [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express with Advanced Services.  
  
 ** La modifica dell'edizione di un cluster di failover di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prevede alcune limitazioni. Gli scenari seguenti non sono supportati per i cluster di failover di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Da Enterprise a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer, Standard o Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Da Developer a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard o Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Da Standard a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Da Evaluation a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard.  
  
## Vedere anche  
 [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [Eseguire l'aggiornamento a SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
  
  