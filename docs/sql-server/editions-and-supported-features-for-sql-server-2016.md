---
title: "Edizioni e funzionalità supportate per SQL Server 2016 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- edizione di sql
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
caps.latest.revision: 175
author: sabotta
ms.author: carlasab
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b9b9db3ca911b8fd8eed6304b9d3a8f51e9e9ba2
ms.lasthandoff: 04/11/2017

---
# <a name="editions-and-supported-features-for-sql-server-2016"></a>Edizioni e funzionalità supportate per SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In questo argomento vengono forniti i dettagli delle funzionalità supportate dalle diverse edizioni di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 SQL Server Evaluation Edition è disponibile per un periodo di valutazione di 180 giorni.  
  
 Per le note sulla versione più recenti e informazioni sulle novità, vedere quanto segue:
- [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
- [Novità di SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)

    
 **Try SQL Server 2016!**    
    
 > [![Download from Evaluation Center](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Download SQL Server 2016  from the Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Azure Virtual Machine small](../analysis-services/media/azure-virtual-machine-small.png) **[Spin up a Virtual Machine with SQL Server 2016 already installed](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.SQL2016SP1-WS2016?tab=Overview?wt.mc_id=sqL16_vm)**    
    
**Edizioni Developer ed Evaluation**  
 Per le funzionalità supportate dalle edizioni Developer ed Evaluation, vedere le funzionalità elencate per SQL Server Enterprise Edition nelle tabelle seguenti.
Per un elenco delle funzionalità aggiunte a Developer Edition per [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1, vedere [SQL Server 2016 SP1 editions](https://aka.ms/uw6cw4) (Edizioni di SQL Server 2016 SP1).   
  
##  <a name="Cross-BoxScaleLimits"></a> Scale Limits  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|Capacità di calcolo massima usata da una singola istanza - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|valore massimo del sistema operativo|Limitato a meno di 4 socket o 24 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 1 socket o 4 core|Limitato a meno di 1 socket o 4 core| 
|Capacità di calcolo massima usata da una singola istanza - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] oppure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|valore massimo del sistema operativo|Limitato a meno di 4 socket o 24 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 1 socket o 4 core|Limitato a meno di 1 socket o 4 core|  
|Memoria massima per il pool di buffer per ogni istanza di [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|valore massimo del sistema operativo|128 GB|64 GB|1410 MB|1410 MB|
|Memoria massima per la cache dei segmenti Columnstore per ogni istanza di [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Memoria illimitata| 32 GB<sup>2</sup>| 16 GB<sup>2</sup>| 352 MB<sup>2</sup>| 352 MB<sup>2</sup>|  
|Dimensione massima dati con ottimizzazione per la memoria per ogni database in [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Memoria illimitata| 32 GB<sup>2</sup>| 16 GB<sup>2</sup>| 352 MB<sup>2</sup>| 352 MB<sup>2</sup>|  
|Memoria massima usata per ogni istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|valore massimo del sistema operativo|Tabella: 16 GB<br /><br /> MOLAP: 64 GB|N/D|N/D|N/D|  
|Memoria massima usata per ogni istanza di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|valore massimo del sistema operativo|64 GB|64 GB|4 GB|N/D|
|Dimensione massima del database relazionale|524 PB|524 PB|524 PB|10 GB|10 GB|  
  
<sup>1</sup> La licenza basata su Enterprise Edition con Server + Licenza CAL (Client Access License), non disponibile per nuovi contratti, è limitata a un massimo di 20 core per istanza di SQL Server. Non sono previsti limiti nel modello di licenza server basato su core. Per altre informazioni, vedere [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
<sup>2</sup> Si applica a [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. 

##  <a name="RDBMSHA"></a> RDBMS High Availability  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Supporto di Server Core <sup>1</sup>|Sì|Sì|Sì|Sì|Sì|  
|Log shipping|Sì|Sì|Sì|No|No|  
|Mirroring del database|Sì|Sì<br /><br /> Solo modalità di protezione Full|Solo server di controllo|Solo server di controllo|Solo server di controllo| 
|Compressione backup|Sì|Sì|No|No|No| 
|Snapshot del database|Sì|Sì <sup>3</sup>|Sì <sup>3</sup>|Sì <sup>3</sup>|Sì <sup>3</sup>|
|Istanze del cluster di failover Always On|Sì<br /><br /> Il numero di nodi è il valore massimo del sistema operativo|Sì<br /><br /> Supporto per 2 nodi|No|No|No|  
|Gruppi di disponibilità Always On|Sì<br /><br /> Fino a 8 repliche secondarie, incluse 2 repliche secondarie sincrone|No|No|No|No|
|Gruppi di disponibilità di base <sup>2</sup>|No|Sì<br /><br /> Supporto per 2 nodi|No|No|No|
|Ripristino di pagine e file online|Sì|No|No|No|No|
|Indicizzazione online|Sì|No|No|No|No|
|Modifica dello schema online|Sì|No|No|No|No|
|Recupero rapido|Sì|No|No|No|No|
|Backup con mirroring|Sì|No|No|No|No|
|Aggiunta di memoria a caldo e CPU|Sì|No|No|No|No|
|Database Recovery Advisor|Sì|Sì|Sì|Sì|Sì|
|Backup crittografato|Sì|Sì|No|No|No|
|Backup ibrido in Microsoft Azure (backup nell'URL)|Sì|Sì|No|No|No|  
  
 <sup>1</sup> Per altre informazioni sull'installazione di SQL Server 2016 in Server Core, vedere [Installare SQL Server 2016 in Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md). 

<sup>2</sup> Per altre informazioni sui gruppi di disponibilità di base, vedere [Gruppi di disponibilità di base](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).  

<sup>3</sup> Si applica a [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1.
  
##  <a name="RDBMSSP"></a> RDBMS Scalability and Performance  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Columnstore <sup>1</sup>|Sì|Sì <sup>2</sup>|Sì <sup>2</sup>|Sì<sup>2</sup>|Sì<sup>2</sup>|  
|OLTP in memoria <sup>1</sup>|Sì|Sì <sup>2</sup>|Sì <sup>2</sup>|Sì <sup>2</sup>, <sup>3</sup>|Sì <sup>2</sup>|
|Estensione database|Sì|Sì|Sì|Sì|Sì|
|Memoria principale persistente|Sì|Sì|Sì|Sì|Sì|
|Supporto di più istanze|50|50|50|50|50|
|Partizionamento di tabelle e indici|Sì|Sì <sup>2</sup>|Sì <sup>2</sup>|Sì <sup>2</sup>|Sì <sup>2</sup>|  
|Compressione dati|Sì|Sì <sup>2</sup>|Sì <sup>2</sup>|Sì <sup>2</sup>|Sì <sup>2</sup>|
|Resource Governor|Sì|No|No|No|No|  
|Parallelismo della tabella partizionata|Sì|No|No|No|No|
|Più contenitori Filestream|Sì|Sì <sup>2</sup>|Sì <sup>2</sup>|Sì <sup>2</sup>|Sì <sup>2</sup>|
|Allocazione di una matrice di buffer e di memoria in pagine grandi con supporto NUMA|Sì|No|No|No|No|
|Estensione pool di buffer|Sì|Sì|No|No|No|
|Governance delle risorse di I/O|Sì|No|No|No|No|  
|Durabilità posticipata|Sì|Sì|Sì|Sì|Sì|

<sup>1</sup> Le dimensioni dati OLTP in memoria e la cache dei segmenti Columnstore sono limitate alla quantità di memoria specificata dall'edizione nella sezione Limiti di scalabilità. I gradi di parallelismo (DOP) massimi sono limitati. I gradi di parallelismo del processo (DOP) per una compilazione indice sono limitati a 2 DOP per l'edizione Standard e 1 DOP per le edizioni Web ed Express. Questo si riferisce agli indici columnstore creati tramite le tabelle basate su disco e le tabelle con ottimizzazione per la memoria.

<sup>2</sup> Si applica a [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. 

<sup>3</sup> Questa funzionalità non è inclusa nell'opzione di installazione LocalDB.
##  <a name="RDBMSS"></a> RDBMS Security  
  
|Funzionalità|Enterprise|Standard|Web|Express|Express with Advanced Services|  
|-------------|----------------|--------------|---------|-------------|------------------------------------| 
|Sicurezza a livello di riga|Sì|Sì|Sì <sup>1</sup>|Sì <sup>1</sup>|Sì <sup>1</sup>|  
|Crittografia sempre attiva|Sì|Sì <sup>1</sup>|Sì <sup>1</sup>|Sì <sup>1</sup>|Sì <sup>1</sup>| 
|Mascheramento dati dinamici|Sì|Sì|Sì <sup>1</sup>|Sì <sup>1</sup>|Sì <sup>1</sup>|   
|Controllo di base|Sì|Sì|Sì|Sì|Sì| 
|Controllo con granularità fine|Sì|Sì <sup>1</sup>|Sì <sup>1</sup>|Sì <sup>1</sup>|Sì <sup>1</sup>| 
|Crittografia trasparente del database|Sì|No|No|No|No|   
|Extensible Key Management|Sì|No|No|No|No| 
|Ruoli definiti dall'utente|Sì|Sì|Sì|Sì|Sì| 
|Database indipendenti|Sì|Sì|Sì|Sì|Sì| 
|Crittografia per backup|Sì|Sì|No|No|No|  

<sup>1</sup> Si applica a [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1.  
##  <a name="Replication"></a> Replication  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Sottoscrittori eterogenei|Sì|Sì|No|No|No|  
|Replica di tipo merge|Sì|Sì|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|   
|Pubblicazione Oracle|Sì|No|No|No|No| 
|Replica transazionale peer-to-peer|Sì|No|No|No|No|   
|Replica snapshot|Sì|Sì|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|   
|Rilevamento delle modifiche in SQL Server|Sì|Sì|Sì|Sì|Sì| 
|Replica transazionale|Sì|Sì|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|   
|Replica transazionale in Azure|Sì|Sì|No|No|No|   
|Sottoscrizione aggiornabile con replica transazionale|Sì|No|No|No|No|  
  
##  <a name="SSMS"></a> Management Tools  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SMO (SQL Management Objects)|Sì|Sì|Sì|Sì|Sì|  
|Gestione configurazione SQL Server|Sì|Sì|Sì|Sì|Sì|   
|CMD SQL (strumento da riga di comando)|Sì|Sì|Sì|Sì|Sì|      
|Riesecuzione distribuita - Strumento di amministrazione|Sì|Sì|Sì|Sì|No|  
|Riesecuzione distribuita - Client|Sì|Sì|Sì|No|No|  
|Distributed Replay - Controller|Sì (fino a 16 client)|Sì (1 client)|Sì (1 client)|No|No|   
|SQL Profiler|Sì|Sì|No <sup>1</sup>|No <sup>1</sup>|No <sup>1</sup>|  
|SQL Server Agent|Sì|Sì|Sì|No|No| 
|Management Pack di Microsoft System Center Operations Manager|Sì|Sì|Sì|No|No|  
|Ottimizzazione guidata motore di database (DTA)|Sì|Sì <sup>2</sup>|Sì <sup>2</sup>|No|No|      
  
 <sup>1</sup> È possibile eseguire il profiling di SQL Server Web, SQL Server Express, SQL Server Express with Tools ed SQL Server Express with Advanced Services usando le edizioni SQL Server Standard ed SQL Server Enterprise Edition.  
  
 <sup>2</sup> Ottimizzazione abilitata solo sulle funzionalità dell'edizione Standard.  
  
##  <a name="RDBMSM"></a> RDBMS Manageability  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Istanze utente|No|No|No|Sì|Sì| 
|Database locale|No|No|No|Sì|No| 
|Connessione amministrativa dedicata|Sì|Sì|Sì|Sì, con flag di traccia|Sì, con flag di traccia|   
|Supporto per script di PowerShell|Sì|Sì|Sì|Sì|Sì| 
|Supporto SysPrep <sup>1</sup>|Sì|Sì|Sì|Sì|Sì| 
|Supporto per le operazioni del componente dell'applicazione livello dati (DAC) - estrazione, distribuzione, aggiornamento, eliminazione|Sì|Sì|Sì|Sì|Sì| 
|Automazione dei criteri (controllo pianificato e modifica)|Sì|Sì|Sì|No|No|   
|Agente di raccolta dati relativi alle prestazioni|Sì|Sì|Sì|No|No| 
|Possibilità di registrarsi come un'istanza gestita in una gestione a più istanze|Sì|Sì|Sì|No|No|   
|Report di prestazioni standard|Sì|Sì|Sì|No|No| 
|Guide di piano e blocco del piano per le guide di piano|Sì|Sì|Sì|No|No|   
|Query diretta di viste indicizzate (tramite hint NOEXPAND)|Sì|Sì|Sì|Sì|Sì| 
|Gestione automatica viste indicizzate|Sì|Sì|Sì|No|No| 
|Viste partizionate distribuite|Sì|No|No|No|No| 
|Operazioni indicizzate parallele|Sì|No|No|No|No|  
|Utilizzo automatico di viste indicizzate da Query Optimizer|Sì|No|No|No|No| 
|Verifica di coerenza parallela|Sì|No|No|No|No| 
|Punto di controllo dell'Utilità SQL Server|Sì|No|No|No|No|    
|Estensione pool di buffer|Sì|Sì|No|No|No| 
  
 <sup>1</sup> Per altre informazioni, vedere [Considerazioni sull'installazione di SQL Server tramite SysPrep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
 
<sup>2</sup> Si applica a [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1. 
  
##  <a name="DevTools"></a> Development Tools  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Integrazione con Microsoft Visual Studio|Sì|Sì|Sì|Sì|Sì| 
|Intellisense (Transact-SQL e MDX)|Sì|Sì|Sì|Sì|Sì| 
|SQL Server Data Tools (SSDT)|Sì|Sì|Sì|Sì|No|    
|Strumenti di progettazione, debug e modifica MDX|Sì|Sì|No|No|No|   
  
##  <a name="Programmability"></a> Programmability  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Integrazione di R di base|Sì|Sì|Sì|Sì|No|   
|Integrazione di R avanzato|Sì|No|No|No|No| 
|R Server (Standalone)|Sì|No|No|No|No|   
|Nodo di calcolo Polybase|Sì|Sì <sup>1</sup>|Sì <sup>1</sup>, <sup>2</sup>|Sì <sup>1</sup>, <sup>2</sup>|Sì <sup>1</sup>, <sup>2</sup>| 
|Nodo head Polybase|Sì|No|No|No|No| 
|JSON|Sì|Sì|Sì|Sì|Sì|   
|Archivio query|Sì|Sì|Sì|Sì|Sì|   
|Temporale|Sì|Sì|Sì|Sì|Sì|   
|Integrazione con Common Language Runtime (CLR)|Sì|Sì|Sì|Sì|Sì|   
|Supporto XML nativo|Sì|Sì|Sì|Sì|Sì| 
|Indicizzazione XML|Sì|Sì|Sì|Sì|Sì| 
|Funzionalità MERGE e UPSERT|Sì|Sì|Sì|Sì|Sì|   
|Supporto FILESTREAM|Sì|Sì|Sì|Sì|Sì| 
|FileTable|Sì|Sì|Sì|Sì|Sì| 
|Tipi di dati data e ora|Sì|Sì|Sì|Sì|Sì|  
|Supporto di internazionalizzazione|Sì|Sì|Sì|Sì|Sì| 
|Ricerca full-text e semantica|Sì|Sì|Sì|Sì|No| 
|Impostazione della lingua nelle query|Sì|Sì|Sì|Sì|No|   
|Service Broker (messaggistica)|Sì|Sì|No (solo client)|No (solo client)|No (solo client)|   
|Transact-SQL - endpoint|Sì|Sì|Sì|No|No| 

<sup>1</sup> La scalabilità orizzontale con più nodi di calcolo richiede un nodo head.

<sup>2</sup> Si applica a [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1.
  
## <a name="IS"></a> Integration Services

Per informazioni sulle funzionalità di Integration Services (SSIS) supportate dalle edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)], vedere [Integration Services Features Supported by the Editions of SQL Server](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md) (Funzionalità di Integration Services supportate dalle edizioni di SQL Server).

##  <a name="MDS"></a> Master Data Services  
 Per informazioni sulle funzionalità di [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] e Data Quality Services supportate dalle edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Master Data Services and Data Quality Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Master Data Services e Data Quality Services supportate dalle edizioni di SQL Server 2016)](../master-data-services/master-data-services-and-data-quality-services-features-support.md). 

  
##  <a name="DW"></a> Data Warehouse  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Creazione di cubi senza database|Sì|Sì|No|No|No |   
|Generazione automatica dello schema della gestione temporanea e del data warehouse|Sì|Sì|No|No|No| 
|Change Data Capture|Sì|Sì <sup>1</sup>|No|No|No| 
|Ottimizzazione query join a stella|Sì|No|No|No|No| 
|Configurazione scalabile di Analysis Services di sola lettura|Sì|No|No|No|No| 
|Elaborazione di query parallela su tabelle e indici partizionati|Sì|No|No|No|No|   
|Aggregazione batch globale|Sì|No|No|No|No| 

<sup>1</sup> Si applica a [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] SP1.  
##  <a name="SSAS"></a> Analysis Services  
  
Per informazioni sulle funzionalità di Analysis Services supportate dalle edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Analysis Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Analysis Services supportate dalle edizioni di SQL Server 2016)](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md). 
  
##  <a name="BIMD"></a> BI Semantic Model (Multi Dimensional)  
  
Per informazioni sulle funzionalità di Analysis Services supportate dalle edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Analysis Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Analysis Services supportate dalle edizioni di SQL Server 2016)](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
   
##  <a name="BIT"></a> BI Semantic Model (Tabular)  
  
Per informazioni sulle funzionalità di Analysis Services supportate dalle edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Analysis Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Analysis Services supportate dalle edizioni di SQL Server 2016)](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="PPSP"></a> Power Pivot for SharePoint  
  
Per informazioni sulle funzionalità di PowerPivot per SharePoint supportate dalle edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Analysis Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Analysis Services supportate dalle edizioni di SQL Server 2016)](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="DM"></a> Data Mining  
  
Per informazioni sulle funzionalità di data mining supportate dalle edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Analysis Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Analysis Services supportate dalle edizioni di SQL Server 2016)](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="SSRS"></a> Reporting Services  
  
Per informazioni sulle funzionalità di Reporting Services supportate dalle edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Reporting Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Reporting Services supportate dalle edizioni di SQL Server 2016)](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md).

##  <a name="BIC"></a> Business Intelligence Clients  

Per informazioni sulle funzionalità del client di Business Intelligence supportate dalle edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Analysis Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Analysis Services supportate dalle edizioni di SQL Server 2016)](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) o [Reporting Services Features Supported by the Editions of SQL Server 2016 (Funzionalità di Reporting Services supportate dalle edizioni di SQL Server 2016)](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="SLS"></a> Spatial and Location Services  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|Indici spaziali|Sì|Sì|Sì|Sì|Sì|   
|Tipi di dati planari e geodetici|Sì|Sì|Sì|Sì|Sì| 
|Librerie spaziali avanzate|Sì|Sì|Sì|Sì|Sì|   
|Importazione/esportazione di formati di dati spaziali standard del settore|Sì|Sì|Sì|Sì|Sì|   
  
##  <a name="ADS"></a> Additional Database Services  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------| 
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|Sì|Sì|Sì|Sì|Sì|   
|Posta elettronica database|Sì|Sì|Sì|No|No| 
  
##  <a name="Other"></a> Other Components  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|No|No| 
|StreamInsight HA|StreamInsight Premium Edition|No|No|No|No|   
  
> [![Download SSMS](../analysis-services/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[Download the latest version of SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**    
  
## <a name="see-also"></a>Vedere anche  
 [Specifiche di prodotto per SQL Server 2016](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)   
 [Installazione per SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)  
  
  

