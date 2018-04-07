---
title: Edizioni e le funzionalità supportate di SQL Server 2017 ~ Linux | Documenti Microsoft
ms.custom: sql-linux
ms.date: 09/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: sql-linux
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- default components
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: ''
caps.latest.revision: 121
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: da867b1125d4ee444a0e04e34d729484bee43514
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="editions-and-supported-features-of-sql-server-2017-on-linux"></a>Edizioni e le funzionalità supportate di SQL Server 2017 su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo fornisce informazioni dettagliate delle funzionalità supportate dalle diverse edizioni di SQL Server 2017 in Linux. Per le edizioni e le funzionalità supportate di SQL Server in Windows, vedere [SQL Server 2017, Windows](../sql-server/editions-and-components-of-sql-server-2017.md).  
  
I requisiti di installazione variano in base alle esigenze dell'applicazione. Le diverse edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] consentono di soddisfare le esigenze specifiche di utenti e organizzazioni in termini di prezzo, esecuzione e prestazioni. I componenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installati dipendono inoltre dai requisiti specifici. Nelle sezioni seguenti vengono fornite tutte le informazioni necessarie per adottare la scelta migliore tra le edizioni e i componenti disponibili in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  

Per le note sulla versione più recenti e informazioni sulle novità, vedere quanto segue:
- [Note sulla versione di SQL Server in Linux](sql-server-linux-release-notes.md)
- [Novità di SQL Server in Linux](sql-server-linux-whats-new.md)

Per un elenco delle funzionalità di SQL Server non disponibile in Linux, vedere [non supportate funzionalità e i servizi](sql-server-linux-release-notes.md#Unsupported).

### <a name="try-sql-server"></a>Per provare SQL Server    
    
[Scaricare SQL Server 2017](http://www.microsoft.com/sql-server/sql-server-2017)

## <a name="includessnoversionincludesssnoversion-mdmd-editions"></a>Edizioni di [!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)]  
 La tabella seguente descrive tali edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 
  
|Edizione di[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] |Definizione|  
|---------------------------------------|----------------|  
|Enterprise|L'offerta premium, [!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Enterprise edition offre le funzionalità complete dei centri dati fascia alta con prestazioni velocissime abilitazione dei livelli di servizio elevati per carichi di lavoro di importanza critica.|  
|Standard|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Edizione standard offre la gestione dei dati di base per reparti e piccole organizzazioni di eseguire le applicazioni e supporta gli strumenti di sviluppo comuni locali e cloud, abilitando una gestione efficace del database con risorse IT minime.|  
|Web|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Web Edition costituisce un'opzione con un costo totale di proprietà ridotto per provider di servizi di hosting Web e VAP Web, offrendo funzionalità di scalabilità, convenienza e facilità di gestione per proprietà Web di ogni dimensione.|  
|Developer|L'edizione[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Developer consente agli sviluppatori di compilare qualsiasi tipo di applicazione in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Benché includa tutte le funzionalità dell'edizione Enterprise, ne è consentito l'utilizzo solo come sistema di sviluppo e di prova e non come server di produzione. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Developer rappresenta la scelta ideale per chi desidera compilare e testare applicazioni.|  
|Express edition|L'edizione Express è un database di base gratuito, ideale per l'apprendimento e la compilazione di applicazioni basate sui dati desktop e server di piccole dimensioni. Questa edizione costituisce la scelta ottimale per fornitori di software indipendenti, sviluppatori e sviluppatori amatoriali di applicazioni client. Se sono necessarie funzionalità di database più avanzate, è possibile aggiornare facilmente [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express a versioni di fascia superiore di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-clientserver-applications"></a>Uso di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con applicazioni client/server  

È possibile installare solo i componenti client di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in un computer in cui vengono eseguite applicazioni client/server connesse direttamente a un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. L'installazione di componenti client rappresenta una scelta ottimale anche se si amministra un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in un server di database o se si prevede di sviluppare applicazioni basate su [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="includessnoversionincludesssnoversion-mdmd-components"></a>Componenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  

2017 di SQL Server in Linux supporta il motore di database di SQL Server. Nella tabella seguente vengono descritte le funzionalità del motore di database.   
  
|Componenti server|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] include il [!INCLUDE[ssDE](../includes/ssde-md.md)], il servizio principale per l'archiviazione, elaborazione e la protezione dati, replica, ricerca full-text, strumenti per la gestione relazionali e dati XML e in integrazione analitica del database.|  

**Edizioni Developer, Enterprise Core e valutazione**  
Per le funzionalità supportate dalle Developer, Enterprise Core e versioni di valutazione, vedere le funzionalità elencate per l'edizione Enterprise di SQL Server nelle tabelle seguenti.

L'edizione Developer continua a supportare un solo client per la [riesecuzione distribuita di SQL Server](../tools/distributed-replay/sql-server-distributed-replay.md). 
  
##  <a name="Cross-BoxScaleLimits"></a> Limiti di scalabilità  
  
|Funzionalità|Enterprise|Standard|Web|Express| 
|-------------|----------------|--------------|---------|------------------------|
|Capacità di calcolo massima usata da una singola istanza - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|Valore massimo del sistema operativo|Limitato a meno di 4 socket o 24 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 1 socket o 4 core| 
|Capacità di calcolo massima usata da una singola istanza - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] oppure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Valore massimo del sistema operativo|Limitato a meno di 4 socket o 24 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 1 socket o 4 core|
|Memoria massima per il pool di buffer per ogni istanza di [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|valore massimo del sistema operativo|128 GB|64 GB|1410 MB|
|Memoria massima per la cache dei segmenti Columnstore per ogni istanza di [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Memoria illimitata| 32 GB| 16 GB| 352 MB|  
|Dimensione massima dati ottimizzati per la memoria per ogni database in [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Memoria illimitata| 32 GB| 16 GB| 352 MB|
|Dimensione massima del database relazionale|524 PB|524 PB|524 PB|10 GB|  
  
<sup>1</sup> Enterprise edition con Server + CAL Client Access License () in base licenze (non disponibile per nuovi contratti) è limitata a un massimo di 20 core per istanza di SQL Server. Non sono previsti limiti nel modello di licenza server basato su core. Per ulteriori informazioni, vedere [limiti di capacità di calcolo per edizione di SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
 
##  <a name="RDBMSHA"></a> Disponibilità elevata RDBMS  
  
|Funzionalità|Enterprise|Standard|Web|Express|  
|-------------|----------------|--------------|---------|------------------------|  
|Log shipping|Sì|Sì|Sì|no|  
|Compressione backup|Sì|Sì|No|no| 
|Snapshot del database|Sì|No|No|no|
|Always On istanza del cluster di failover<sup>1</sup>|Sì|Sì|No|no| 
|Gruppi di disponibilità Always On<sup>2</sup>|Sì|No|No|no|
|Gruppi di disponibilità di base <sup>3</sup>|no|Sì|No|no|
|Gruppo di disponibilità con commit di un numero minimo di repliche|Sì|Sì|No|no|
|Gruppo di disponibilità senza cluster|Sì|Sì|No|no|
|Ripristino di pagine e file online|Sì|No|No|no|
|Indicizzazione online|Sì|No|No|no|
|Ricompilazioni degli indici online ripristinabili|Sì|No|No|no|
|Modifica dello schema online|Sì|No|No|no|
|Recupero rapido|Sì|No|No|no|
|Backup con mirroring|Sì|No|No|no|
|Aggiunta di memoria a caldo e CPU|Sì|No|No|no|
|Backup crittografato|Sì|Sì|No|no|
|Backup ibrido in Microsoft Azure (backup nell'URL)|Sì|Sì|No|no|
  
<sup>1</sup> in Enterprise edition, il numero di nodi è il valore massimo del sistema operativo. In Standard Edition è presente il supporto per due nodi. 

<sup>2</sup> in Enterprise edition, fornisce il supporto per fino a 8 repliche secondarie, incluse 2 repliche secondarie sincrone. 

<sup>3</sup> standard edition supporta i gruppi di disponibilità di base. Un gruppo di disponibilità di base supporta due repliche, con un database. Per altre informazioni sui gruppi di disponibilità di base, vedere [Gruppi di disponibilità di base](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).    

##  <a name="RDBMSSP"></a> Scalabilità e prestazioni RDBMS  
  
|Funzionalità|Enterprise|Standard|Web|Express|  
|-------------|----------------|--------------|---------|------------------------| 
|Columnstore <sup>1</sup>|Sì|Sì|Sì|Sì|  
|File binari di oggetti di grandi dimensioni in indici columnstore cluster|Sì|Sì|Sì|Sì|  
|Ricompilazione degli indici columnstore non cluster online|Sì|No|No|no|
|OLTP in memoria <sup>1</sup>|Sì|Sì|Sì|Sì|
|Memoria principale persistente|Sì|Sì|Sì|Sì|
|Partizionamento di tabelle e indici|Sì|Sì|Sì|Sì|  
|Compressione dati|Sì|Sì|Sì|Sì|
|Resource Governor|Sì|No|No|no|  
|Parallelismo della tabella partizionata|Sì|No|No|no|
|Allocazione di una matrice di buffer e di memoria in pagine grandi con supporto NUMA|Sì|No|No|no|
|Governance delle risorse di I/O|Sì|No|No|no|  
|Durabilità posticipata|Sì|Sì|Sì|Sì|
|Ottimizzazione automatica|Sì|No|No|no|
|Join adattivi in modalità batch|Sì|No|No|no|
|Feedback delle concessioni di memoria in modalità batch|Sì|No|No|no|
|Esecuzione interleaved per funzioni con valori di tabella a più istruzioni|Sì|Sì|Sì|Sì|
|Miglioramenti dell'inserimento bulk|Sì|Sì|Sì|Sì|


<sup>1</sup> Le dimensioni dati OLTP in memoria e la cache dei segmenti Columnstore sono limitate alla quantità di memoria specificata dall'edizione nella sezione Limiti di scalabilità. I gradi di parallelismo (DOP) massimi sono limitati. I gradi di parallelismo (DOP) di processi per la compilazione di un indice è limitato a 2 grado di Parallelismo per Standard edition e 1 grado di Parallelismo per le edizioni Web ed Express. Questo si riferisce agli indici columnstore creati tramite le tabelle basate su disco e le tabelle ottimizzate per la memoria.

##  <a name="RDBMSS"></a> Sicurezza RDBMS  
  
|Funzionalità|Enterprise|Standard|Web|Express|
|-------------|----------------|--------------|---------|------------------------------------| 
|Sicurezza a livello di riga|Sì|Sì|Sì|Sì|  
|Crittografia sempre attiva|Sì|Sì|Sì|Sì| 
|Mascheramento dati dinamici|Sì|Sì|Sì|Sì|   
|Controllo di base|Sì|Sì|Sì|Sì| 
|Controllo con granularità fine|Sì|Sì|Sì|Sì| 
|Crittografia trasparente del database|Sì|No|No|no|   
|Ruoli definiti dall'utente|Sì|Sì|Sì|Sì| 
|Database indipendenti|Sì|Sì|Sì|Sì| 
|Crittografia per backup|Sì|Sì|No|no|  

##  <a name="RDBMSM"></a> Gestione RDBMS  
  
|Funzionalità|Enterprise|Standard|Web|Express|   
|-------------|----------------|--------------|---------|------------------------|  
|Connessione amministrativa dedicata|Sì|Sì|Sì|Sì, con flag di traccia|Sì, con flag di traccia|   
|Supporto per script di PowerShell|Sì|Sì|Sì|Sì| 
|Supporto per le operazioni del componente dell'applicazione livello dati (DAC) - estrazione, distribuzione, aggiornamento, eliminazione|Sì|Sì|Sì|Sì| 
|Automazione dei criteri (controllo pianificato e modifica)|Sì|Sì|Sì|No|no|   
|Agente di raccolta dati relativi alle prestazioni|Sì|Sì|Sì|No|no| 
|Report di prestazioni standard|Sì|Sì|Sì|No|no| 
|Guide di piano e blocco del piano per le guide di piano|Sì|Sì|Sì|No|no|   
|Query diretta di viste indicizzate (tramite hint NOEXPAND)|Sì|Sì|Sì|Sì| 
|Gestione automatica viste indicizzate|Sì|Sì|Sì|No|no| 
|Viste partizionate distribuite|Sì|No|No|no| 
|Operazioni indicizzate parallele|Sì|No|No|no|  
|Utilizzo automatico di viste indicizzate da Query Optimizer|Sì|No|No|no| 
|Verifica di coerenza parallela|Sì|No|No|no| 
|Punto di controllo dell'Utilità SQL Server|Sì|No|No|no|    

##  <a name="Programmability"></a> Programmability  
  
|Funzionalità|Enterprise|Standard|Web|Express 
|-------------|----------------|--------------|---------|------------------------|  
|JSON|Sì|Sì|Sì|Sì|   
|Archivio query|Sì|Sì|Sì|Sì|   
|Temporale|Sì|Sì|Sì|Sì|   
|Supporto XML nativo|Sì|Sì|Sì|Sì| 
|Indicizzazione XML|Sì|Sì|Sì|Sì| 
|Funzionalità MERGE e UPSERT|Sì|Sì|Sì|Sì|   
|Tipi di dati data e ora|Sì|Sì|Sì|Sì|  
|Supporto di internazionalizzazione|Sì|Sì|Sì|Sì| 
|Ricerca full-text e semantica|Sì|Sì|Sì|Sì|no| 
|Impostazione della lingua nelle query|Sì|Sì|Sì|Sì|no|   
|Service Broker (messaggistica)|Sì|Sì|No (solo client)|No (solo client)|No (solo client)|   
|Transact-SQL - endpoint|Sì|Sì|Sì|No|no| 
|Grafico|Sì|Sì|Sì|Sì|  


<sup>1</sup> La scalabilità orizzontale con più nodi di calcolo richiede un nodo head.

## <a name="IS"></a> Integration Services

Per informazioni sulle funzionalità di Integration Services (SSIS) supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)], vedere [funzionalità Servizi di integrazione supportate dalle edizioni di SQL Server](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md).

##  <a name="SLS"></a> Servizi spaziali e basati sulla posizione  
  
|Nome funzionalità|Enterprise|Standard|Web|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|Indici spaziali|Sì|Sì|Sì|Sì|   
|Tipi di dati planari e geodetici|Sì|Sì|Sì|Sì| 
|Librerie spaziali avanzate|Sì|Sì|Sì|Sì|   
|Importazione/esportazione di formati di dati spaziali standard del settore|Sì|Sì|Sì|Sì|   

  
## <a name="next-steps"></a>Passaggi successivi 
 [Edizioni e delle funzionalità supportate per SQL Server 2017 - Windows](../sql-server/editions-and-components-of-sql-server-2017.md)  
 [Edizioni e le funzionalità supportate per SQL Server 2016 - Windows](../sql-server/editions-and-components-of-sql-server-2016.md)  
 [Edizioni e le funzionalità supportate per SQL Server 2014 - Windows](http://msdn.microsoft.com/library/cc645993(v=sql.120).aspx)  
 [Installation for SQL Server](../database-engine/install-windows/installation-for-sql-server-2016.md) (Installazione per SQL Server)  
 [Specifiche del prodotto per SQL Server](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb) 

  
  
