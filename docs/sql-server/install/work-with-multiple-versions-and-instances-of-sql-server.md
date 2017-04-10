---
title: "Utilizzare pi&#249; versioni e istanze di SQL Server | Microsoft Docs"
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
  - "installazioni coesistenti [SQL Server]"
  - "versioni [SQL Server], multiple"
  - "installazioni side-by-side [SQL Server]"
  - "più versioni di componenti di SQL Server"
  - "installazioni side-by-side di SQL Server"
  - "programma di installazione [SQL Server], installazioni side-by-side"
  - "edizione a 64 bit [SQL Server]"
  - "edizione a 32 bit [SQL Server]"
  - "edizioni [SQL Server], installazioni side-by-side"
ms.assetid: 93acefa8-bb41-4ccc-b763-7801f51134e0
caps.latest.revision: 67
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 67
---
# Utilizzare pi&#249; versioni e istanze di SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta più istanze del [!INCLUDE[ssDE](../../includes/ssde-md.md)], di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nello stesso computer. È inoltre possibile aggiornare versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o installare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un computer in cui sono già installate versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per gli scenari di aggiornamento supportati, vedere [Aggiornamenti di versione ed edizione supportati](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
## Numerazione e componenti della versione  
 I concetti seguenti sono utili per comprendere il comportamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le istanze side-by-side di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Il formato della versione del prodotto standard per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è MM.nn.bbbb.rr dove ogni segmento è definito come indicato di seguito:  
  
 MM: versione principale  
  
 nn: versione secondaria  
  
 bbbb: numero di build  
  
 rr - numero revisione build  
  
 In ogni versione principale o secondaria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il numero di versione viene aumentato per differenziarlo dalle versioni precedenti. Questa modifica alla versione viene utilizzata per diversi scopi. Ciò include la visualizzazione delle informazioni sulla versione nell'interfaccia utente, il controllo della modalità di sostituzione dei file durante l'aggiornamento, l'applicazione di Service Pack e un meccanismo per una differenziazione funzionale tra le versioni successive.  
  
### Componenti condivisi da tutte le versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Alcuni componenti sono condivisi da tutte le istanze di tutte le versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate. Quando si esegue l'installazione affiancata di versioni diverse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nello stesso computer, questi componenti vengono aggiornati automaticamente alla versione più recente. Tali componenti in genere vengono disinstallati automaticamente quando viene disinstallata l'ultima istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Esempi: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser e Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer.  
  
### Componenti condivisi da tutte le istanze della stessa versione principale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le versioni con la stessa versione principale condividono alcuni componenti in tutte le istanze. Se i componenti condivisi vengono selezionati durante l'aggiornamento, i componenti esistenti vengono aggiornati alla versione più recente.  
  
 Esempi: documentazione online di: [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Componenti condivisi nelle versioni secondarie  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le versioni con componenti che condividono la stessa versione principale e secondaria.  
  
 Esempio: file di supporto per l'installazione.  
  
### Componenti specifici di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Alcuni componenti o servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono specifici di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Essi sono anche noti come specifici dell'istanza. Condividono la stessa versione dell'istanza che li ospita e vengono utilizzati esclusivamente per quell'istanza.  
  
 Esempi: [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
### Componenti indipendenti dalle versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Alcuni componenti vengono installati durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma sono indipendenti dalle versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Essi possono essere condivisi dalle versioni principali o da tutte le versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Esempi: Microsoft Sync Framework, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Per altre informazioni sull'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, vedere [Installare SQL Server 2016 dall'Installazione guidata &#40;programma di installazione&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md). Per altre informazioni su come disinstallare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, vedere [Disinstallare un'istanza esistente di SQL Server &#40;programma di installazione&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md).  
  
## Utilizzo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] insieme a versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 È possibile installare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un computer in cui sono già in esecuzione istanze di una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se nel computer è già presente un'istanza predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere installato come istanza denominata.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep non supporta l'installazione side-by-side di istanze predisposte di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] con versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nello stesso computer. Ad esempio, non è possibile preparare un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] side-by-side a un'istanza predisposta di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Tuttavia, nello stesso computer, è possibile installare side-by-side più istanze predisposte della stessa versione principale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Considerazioni sull'installazione di SQL Server tramite SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
>   
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] non può essere installato side-by-side con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un computer in cui è in esecuzione Windows Server 2008 R2 Server Core SP1. Per altre informazioni sulle installazioni di Server Core, vedere [Installare SQL Server 2016 in Server Core](../../database-engine/install-windows/install-sql-server-2016-on-server-core.md).  
  
 Nella tabella seguente viene descritto il supporto per installazioni side-by-side di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|Istanza esistente di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|Supporto installazioni side-by-side|  
|--------------------------------------------------|----------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (64 bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (32 bit)<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (64 bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (32 bit)<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (64 bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (32 bit)<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (64 bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (32 bit)<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (64 bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (32 bit)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (64 bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|  
  
## Metodi per evitare conflitti di indirizzi IP  
 Quando si esegue un'installazione side-by-side di un'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con un'istanza autonoma del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], prestare attenzione per evitare conflitti del numero di porta TCP negli indirizzi IP. Di solito i conflitti si verificano quando due istanze del [!INCLUDE[ssDE](../../includes/ssde-md.md)] sono entrambe configurate per utilizzare la porta TCP predefinita (1433). Per evitare conflitti, configurare un'istanza in modo che venga utilizzata una porta fissa non predefinita. La configurazione di una porta fissa è di solito più facile nell'istanza autonoma. Configurare il [!INCLUDE[ssDE](../../includes/ssde-md.md)] in modo che vengano utilizzate porte diverse per evitare un conflitto di indirizzo IP o di porta TCP non previsto che blocca l'avvio di un'istanza quando si verifica un errore dell'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel nodo di standby.  
  
## Vedere anche  
 [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [Installare SQL Server 2016 dall'Installazione guidata &#40;programma di installazione&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)   
 [Aggiornamenti di versione ed edizione supportati](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Eseguire l'aggiornamento a SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)   
 [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)  
  
  