---
title: Funzionalità supportate dalle edizioni di SQL Server 2014 | Documenti Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- data-quality-services
- database-engine
- integration-services
- master-data-services
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
caps.latest.revision: 126
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9fea176058eeb35d13ab3e104652fdeb13979238
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069696"
---
# <a name="features-supported-by-the-editions-of-sql-server-2014"></a>Funzionalità supportate dalle edizioni di SQL Server 2014
  In questo argomento vengono forniti i dettagli delle funzionalità supportate dalle diverse edizioni di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
> **Nota:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è disponibile in una versione di valutazione per un periodo di prova di 180 giorni. Per altre informazioni, vedere la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [sito Web Software di prova](http://go.microsoft.com/fwlink/?LinkId=190955).  
  
> **Nota:** per le funzionalità supportate dalle edizioni Evaluation e Developer, vedere il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] set di funzionalità aziendali.  
  
 Per passare alla tabella per una tecnologia [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , fare clic sul relativo collegamento:  
  
 [Limiti di scalabilità tra prodotti](#CrossBoxScale)  
  
 [Disponibilità elevata](#High_availability)  
  
 [Scalabilità e prestazioni](#Scalability)  
  
 [Security](#Enterprise_security)  
  
 [Replica](#Replication)  
  
 [Strumenti di gestione](#Mgmt_Tools)  
  
 [Gestione RDBMS](#RDBMS_mgmt)  
  
 [Strumenti di sviluppo](#Dev_tools)  
  
 [Programmabilità](#Programmability)  
  
 [Integration Services](#SSIS)  
  
 [Integration Services adattatori avanzati](#SSIS_AA)  
  
 [Integration Services trasformazioni avanzate](#SSIS_AT)  
  
 [Master Data Services](#MDS)  
  
 [Data warehouse](#Data_warehouse)  
  
 [Analysis Services](#SSAS)  
  
 [BI Semantic Model (multidimensionale)](#BISemModel_multi)  
  
 [BI Semantic Model (tabulare)](#BISemModel_tabular)  
  
 [PowerPivot per SharePoint](#PowerPivot)  
  
 [Data mining](#DataMining)  
  
 [Reporting Services](#Reporting)  
  
 [Client di Business Intelligence](#BIClients)  
  
 [Spaziali e i servizi di posizione](#Spatial)  
  
 [Servizi di Database aggiuntivi](#Add_DBServices)  
  
 [Altri componenti](#Other_Components)  
  
##  <a name="CrossBoxScale"></a> Limiti di scalabilità tra prodotti  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Capacità di calcolo massima utilizzata da una sola istanza ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] motore di Database)<sup>1</sup>|Valore massimo del sistema operativo|Limitato a meno di 4 socket o 16 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 1 socket o 4 core|Limitato a meno di 1 socket o 4 core|Limitato a meno di 1 socket o 4 core|  
|Capacità di calcolo massima utilizzata da una sola istanza (Analysis Services, Reporting Services) <sup>1</sup>|Valore massimo del sistema operativo|Valore massimo del sistema operativo|Limitato a meno di 4 socket o 16 core|Limitato a meno di 4 socket o 16 core|Limitato a meno di 1 socket o 4 core|Limitato a meno di 1 socket o 4 core|Limitato a meno di 1 socket o 4 core|  
|Memoria massima usata (per ogni istanza del motore di database di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)])|Valore massimo del sistema operativo|128 GB|128 GB|64 GB|1 GB|1 GB|1 GB|  
|Memoria massima usata (per ogni istanza [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)])|Valore massimo del sistema operativo|Valore massimo del sistema operativo|64 GB|N/D|N/D|N/D|N/D|  
|Memoria massima usata (per ogni istanza [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)])|Valore massimo del sistema operativo|Valore massimo del sistema operativo|64 GB|64 GB|4 GB|N/D|N/D|  
|Dimensione massima del database relazionale|524 PB|524 PB|524 PB|524 PB|10 GB|10 GB|10 GB|  
  
 <sup>1</sup> Enterprise Edition con Server + CAL Client Access License () in base licenze (non disponibile per nuovi contratti) è limitata a un massimo di 20 core per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] istanza. Non sono previsti limiti nel modello di licenza server basato su core. Per altre informazioni, vedere [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
##  <a name="High_availability"></a> Disponibilità elevata  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Supporto di Server Core<sup>1</sup>|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Log shipping|Sì|Sì|Sì|Sì||||  
|Mirroring del database|Sì|Sì (solo protezione FULL)|Sì (solo protezione FULL)|Solo server di controllo|Solo server di controllo|Solo server di controllo|Solo server di controllo|  
|Compressione backup|Sì|Sì|Sì|||||  
|Snapshot del database|Sì|||||||  
|Istanze del cluster di failover AlwaysOn|Sì (supporto del nodo: valore massimo del sistema operativo|Sì (supporto del nodo: 2)|Sì (supporto del nodo: 2)|||||  
|Gruppi di disponibilità AlwaysOn|Sì (fino a 8 repliche secondarie, incluse 2 repliche secondarie sincrone)|||||||  
|Connection Director|Sì|||||||  
|Ripristino di pagine e file online|Sì|||||||  
|Indicizzazione online|Sì|||||||  
|Modifica dello schema online|Sì|||||||  
|Recupero rapido|Sì|||||||  
|Backup con mirroring|Sì|||||||  
|Aggiunta a caldo di memoria e CPU<sup>2</sup>|Sì|||||||  
|Database Recovery Advisor|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Backup crittografato|Sì|Sì|Sì|||||  
|Backup intelligente|Sì|Sì|Sì|no||||  
  
 <sup>1</sup>per ulteriori informazioni sull'installazione [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] in Server Core, vedere [installare SQL Server 2014 in Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
 <sup>2</sup>questa funzionalità è disponibile solo per 64 bit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Scalability"></a> Scalabilità e prestazioni  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Supporto di più istanze|50|50|50|50|50|50|50|  
|Partizionamento di tabelle e indici|Sì|||||||  
|Compressione dati|Sì|||||||  
|Resource Governor|Sì|||||||  
|Parallelismo di tabelle delle partizioni|Sì|||||||  
|Più contenitori Filestream|Sì|||||||  
|Allocazione di una matrice di buffer e di memoria in pagine grandi con supporto NUMA|Sì|||||||  
|Estensione del Pool di buffer <sup>1</sup>|Sì|Sì|Sì|||||  
|Governance delle risorse di I/O|Sì|||||||  
|OLTP in memoria <sup>1</sup>|Sì|||||||  
|Durabilità posticipata|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
  
 <sup>1</sup> questa funzionalità è disponibile solo per 64 bit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Enterprise_security"></a> Security  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Controllo di base|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Controllo con granularità fine|Sì|||||||  
|Crittografia trasparente del database|Sì|||||||  
|Extensible Key Management|Sì|||||||  
|Ruoli definiti dall'utente|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Database indipendenti|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Crittografia per backup|Sì|Sì|Sì|||||  
  
##  <a name="Replication"></a> Replication  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] il rilevamento delle modifiche|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Replica di tipo merge|Sì|Sì|Sì|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|  
|Replica transazionale|Sì|Sì|Sì|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|  
|Replica snapshot|Sì|Sì|Sì|Sì (solo sottoscrittore|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|Sì (solo sottoscrittore)|  
|Sottoscrittori eterogenei|Sì|Sì|Sì|||||  
|Pubblicazione Oracle|Sì|||||||  
|Replica transazionale peer-to-peer|Sì|||||||  
  
##  <a name="Mgmt_Tools"></a> Management Tools  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|SMO (SQL Management Objects)|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Gestione configurazione SQL Server|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|CMD SQL (strumento da riga di comando)|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Studio|Sì|Sì|Sì|Sì|Sì|Sì||  
|Riesecuzione distribuita – Strumento di amministrazione|Sì|Sì|Sì|Sì|Sì|Sì||  
|Distributed Replay - Client|Sì|no|Sì|Sì||||  
|Distributed Replay - Controller|Sì (Enterprise supporta fino a 16 client, Developer supporta solo 1 client)|no|Sì (supporto di 1 solo client)|Sì (supporto di 1 solo client)||||  
|SQL Profiler|Sì|Sì|Sì|Non<sup>2</sup>|Non<sup>2</sup>|Non<sup>2</sup>|Non<sup>2</sup>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent|Sì|Sì|Sì|Sì||||  
|Management Pack di Microsoft System Center Operations Manager|Sì|Sì|Sì|Sì||||  
|Ottimizzazione guidata motore di database (DTA)|Sì|Sì|Sì <sup>3</sup>|Sì <sup>3</sup>||||  
|Procedura guidata Distribuire un database di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a una macchina virtuale di Windows Azure|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] File di dati in Microsoft Azure|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
  
 <sup>2</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] web [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Tools e [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services può essere eseguito usando [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition.  
  
 <sup>3</sup> ottimizzazione abilitata solo sulle funzionalità di Standard edition.  
  
##  <a name="RDBMS_mgmt"></a> RDBMS Manageability  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Istanze utente|||||Sì|Sì|Sì|  
|Database locale|||||Sì|Sì||  
|Connessione amministrativa dedicata|Sì|Sì|Sì|Sì|Sì (con flag di traccia)|Sì (con flag di traccia)|Sì (con flag di traccia)|  
|Supporto per script di PowerShell|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Supporto SysPrep<sup>1</sup>|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Supporto per le operazioni del componente dell'applicazione livello dati (DAC) – estrazione, distribuzione, aggiornamento, eliminazione|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Automazione dei criteri (controllo pianificato e modifica)|Sì|Sì|Sì|Sì||||  
|Agente di raccolta dati relativi alle prestazioni|Sì|Sì|Sì|Sì||||  
|In grado di registrarsi come un'istanza gestita in una gestione a più istanze|Sì|Sì|Sì|Sì||||  
|Report di prestazioni standard|Sì|Sì|Sì|Sì||||  
|Guide di piano e blocco del piano per le guide di piano|Sì|Sì|Sì|Sì||||  
|Query diretta di viste indicizzate (tramite hint NOEXPAND)|Sì|Sì|Sì|Sì||||  
|Gestione automatica viste indicizzate|Sì|Sì|Sì|Sì||||  
|Viste partizionate distribuite|Sì|Parziale. Le viste partizionate distribuite non sono aggiornabili|Parziale. Le viste partizionate distribuite non sono aggiornabili|Parziale. Le viste partizionate distribuite non sono aggiornabili|Parziale. Le viste partizionate distribuite non sono aggiornabili|Parziale. Le viste partizionate distribuite non sono aggiornabili|Parziale. Le viste partizionate distribuite non sono aggiornabili|  
|Operazioni indicizzate parallele|Sì|||||||  
|Utilizzo automatico di viste indicizzate da Query Optimizer|Sì|||||||  
|Verifica di coerenza parallela|Sì|||||||  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Punto di controllo dell'utilità|Sì|||||||  
|Database indipendenti|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Estensione del Pool di buffer<sup>2</sup>|Sì|Sì|Sì|||||  
  
 <sup>1</sup> Per altre informazioni, vedere [Considerazioni sull'installazione di SQL Server tramite SysPrep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
  
 <sup>2</sup> questa funzionalità è disponibile solo per 64 bit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Dev_tools"></a> Development Tools  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio Integration|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|IntelliSense ([!INCLUDE[tsql](../includes/tsql-md.md)] e MDX)|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|Sì|Sì|Sì|Sì|Sì|||  
|Strumenti di progettazione e modifica di query SQL<sup>1</sup>|Sì|Sì|Sì|||||  
|Supporto controllo versione<sup>1</sup>|Sì|Sì|Sì|||||  
|Modifica MDX, eseguire il debug e strumenti di progettazione<sup>1</sup>|Sì|Sì|Sì|||||  
  
 <sup>1</sup> questa funzionalità non è disponibile per la versione a 64 bit di Standard edition.  
  
##  <a name="Programmability"></a> Programmability  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Integrazione con Common Language Runtime (CLR)|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Supporto XML nativo|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Indicizzazione XML|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Funzionalità MERGE e UPSERT|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Supporto FILESTREAM|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|FileTable|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Tipi di dati data e ora|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Supporto di internazionalizzazione|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Ricerca full-text e semantica|Sì|Sì|Sì|Sì|Sì|||  
|Impostazione della lingua nelle query|Sì|Sì|Sì|Sì|Sì|||  
|Service Broker (messaggistica)|Sì|Sì|Sì|No (solo client)|No (solo client)|No (solo client)|No (solo client)|  
|Endpoint [!INCLUDE[tsql](../includes/tsql-md.md)]|Sì|Sì|Sì|Sì||||  
  
##  <a name="SSIS"></a> Integration Services  
  
|Funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Connettori origine dati incorporati|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Progettazione SSIS e SSIS Runtime|Sì|Sì|Sì|||||  
|Trasformazioni di base|Sì|Sì|Sì|||||  
|Strumenti di profiling dei dati di base|Sì|Sì|Sì|||||  
|Servizio Change Data Capture per Oracle di Attunity|Sì|||||||  
|Progettazione Change Data Capture per Oracle di Attunity|Sì|||||||  
  
###  <a name="SSIS_AA"></a> Integration Services - Adattatori avanzati  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Destinazione Oracle a prestazioni elevate|Sì|||||||  
|Destinazione Teradata a prestazioni elevate|Sì|||||||  
|Origine e destinazione SAP BW|Sì|||||||  
|Adattatore di destinazione per il training del modello di data mining|Sì|||||||  
|Adattatore di destinazione dell'elaborazione dimensione|Sì|||||||  
|Adattatore di destinazione dell'elaborazione partizione|Sì|||||||  
|Componenti Change Data Capture di Attunity|Sì|||||||  
|Connettore per ODBC (Open Database Connectivity) di Attunity|Sì|||||||  
  
###  <a name="SSIS_AT"></a> Integration Services - Trasformazioni avanzate  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Ricerche persistenti (prestazioni elevate)|Sì|||||||  
|Trasformazione di query di data mining|Sì|||||||  
|Trasformazioni di Ricerca fuzzy e Raggruppamento fuzzy|Sì|||||||  
|Trasformazioni di estrazioni e ricerca termini|Sì|||||||  
  
##  <a name="MDS"></a> Master Data Services  
  
> [!NOTE]  
>  -   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] sono disponibili sul solo le edizioni a 64 bit di Business Intelligence ed Enterprise.  
  
|Funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Sì|Sì||||||  
|Applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]|Sì|Sì||||||  
  
##  <a name="Data_warehouse"></a> Data Warehouse  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Creazione di cubi senza database|Sì|Sì|Sì|||||  
|Generazione automatica dello schema della gestione temporanea e del data warehouse|Sì|Sì|Sì|||||  
|Change Data Capture|Sì|||||||  
|Ottimizzazione query join a stella|Sì|||||||  
|Configurazione scalabile di Analysis Services di sola lettura|Sì|||||||  
|Elaborazione di query parallela su tabelle e indici partizionati|Sì|||||||  
|indici columnstore ottimizzati memoria xVelocity|Sì|||||||  
|Aggregazione batch globale|Sì|||||||  
  
##  <a name="SSAS"></a> Analysis Services  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Database condiviso scalabile (collegamento/scollegamento, database di sola lettura)|Sì|Sì||||||  
|Backup/ripristino, Collegamento/Scollegamento di database|Sì|Sì|Sì|||||  
|Sincronizzare database|Sì|Sì||||||  
|Disponibilità elevata|Sì|Sì|Sì|||||  
|Programmabilità (AMO, ADOMD.Net, OLEDB, XML/A, ASSL)|Sì|Sì|Sì|||||  
  
###  <a name="BISemModel_multi"></a> BI Semantic Model (multidimensionale)  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Misure semiadditive|Sì|Sì|Non<sup>1</sup>|||||  
|Gerarchie|Sì|Sì|Sì|||||  
|KPI|Sì|Sì|Sì|||||  
|prospettive|Sì|Sì||||||  
|Azioni|Sì|Sì|Sì|||||  
|Funzionalità di Business Intelligence per la contabilità|Sì|Sì|Sì|||||  
|Business Intelligence per gerarchie temporali|Sì|Sì|Sì|||||  
|Rollup personalizzati|Sì|Sì|Sì|||||  
|Cubo writeback|Sì|Sì|Sì|||||  
|Dimensioni writeback|Sì|Sì||||||  
|Celle writeback|Sì|Sì|Sì|||||  
|Drill-through|Sì|Sì|Sì|||||  
|Tipi di gerarchia avanzati (padre-figlio, gerarchie incomplete)|Sì|Sì|Sì|||||  
|Dimensioni avanzate (dimensioni di riferimento, dimensioni molti-a-molti|Sì|Sì|Sì|||||  
|Dimensioni e misure collegate|Sì|Sì||||||  
|Traduzioni|Sì|Sì|Sì|||||  
|Aggregations|Sì|Sì|Sì|||||  
|Più partizioni|Sì|Sì|Sì, fino a 3|||||  
|Memorizzazione nella cache attiva|Sì|Sì||||||  
|Assembly personalizzati (procedure archiviate)|Sì|Sì|Sì|||||  
|Query e script MDX|Sì|Sì|Sì|||||  
|Query DAX|Sì|Sì||||||  
|Modello di sicurezza basato su ruoli|Sì|Sì|Sì|||||  
|Sicurezza a livello di cella e dimensione|Sì|Sì|Sì|||||  
|Archivio di stringhe scalabile|Sì|Sì|Sì|||||  
|MOLAP, ROLAP, modalità di archiviazione HOLAP|Sì|Sì|Sì|||||  
|Trasporto XML binario e compresso|Sì|Sì|Sì|||||  
|Elaborazione in modalità push|Sì|Sì||||||  
|Writeback diretto|Sì|Sì||||||  
|Espressioni di misura|Sì|Sì||||||  
  
 <sup>1</sup>misura semiadattiva LastChild the è supportata nell'edizione standard, ma altre misure semiadattive come None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren e ByAccount non lo sono. Le misure additive, ad esempio Sum, Count, Min, Max e quelle non additive (DistinctCount) sono supportate in tutte le edizioni.  
  
###  <a name="BISemModel_tabular"></a> BI Semantic Model (Tabular)  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Gerarchie|Sì|Sì||||||  
|KPI|Sì|Sì||||||  
|prospettive|Sì|Sì||||||  
|Traduzioni|Sì|Sì||||||  
|Calcoli DAX, query DAX, query MDX|Sì|Sì||||||  
|Sicurezza a livello di riga|Sì|Sì||||||  
|Partizioni|Sì|Sì||||||  
|Modalità di archiviazione In-Memory e DirectQuery (solo tabulare)|Sì|Sì||||||  
  
###  <a name="PowerPivot"></a> PowerPivot per SharePoint  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Integrazione di farm SharePoint basata sull'architettura di servizi condivisi|Sì|Sì||||||  
|Report sull'utilizzo|Sì|Sì||||||  
|Regole di monitoraggio dell'integrità|Sì|Sì||||||  
|Raccolta PowerPivot|Sì|Sì||||||  
|Aggiornamento dei dati PowerPivot|Sì|Sì||||||  
|Feed di dati PowerPivot|Sì|Sì||||||  
  
###  <a name="DataMining"></a> Data Mining  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Algoritmi standard|Sì|Sì|Sì|||||  
|Strumenti di data mining (procedure guidate, editor, generatori di query)|Sì|Sì|Sì|||||  
|Convalida incrociata|Sì|Sì||||||  
|Modelli in base a subset filtrati dei dati della struttura di data mining|Sì|Sì||||||  
|Time Series: combinazione personalizzata tra metodi ARTXP e ARIMA|Sì|Sì||||||  
|Time Series: stima con nuovi dati|Sì|Sì||||||  
|Query di data mining simultanee illimitate|Sì|Sì||||||  
|Opzioni di configurazione e ottimizzazione avanzate per algoritmi di data mining|Sì|Sì||||||  
|Supporto per algoritmi plug-in|Sì|Sì||||||  
|Elaborazione parallela dei modelli|Sì|Sì||||||  
|Time Series: stima incrociata tra serie|Sì|Sì||||||  
|Attributi illimitati per Association Rules|Sì|Sì||||||  
|Stima basata su sequenze|Sì|Sì||||||  
|Più destinazioni di stima per gli algoritmi Logistic Regression, Neural Network e Naïve Bayes|Sì|Sì||||||  
  
##  <a name="Reporting"></a> Reporting Services  
  
###  <a name="Reporting_features"></a> Funzionalità di Reporting Services  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Edizione supportata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per il database del catalogo|Standard o versione successiva|Standard o versione successiva|Standard o versione successiva|Web|Express|||  
|Edizione supportata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per le origini dati|Tutte le edizioni di   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Tutte le edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Tutte le edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Web|Express|||  
|Server di report|Sì|Sì|Sì|Sì|Sì|||  
|Progettazione report|Sì|Sì|Sì|Sì|Sì|||  
|Gestione report|Sì|Sì|Sì|Sì|Sì|||  
|Sicurezza basata sui ruoli|Sì|Sì|Sì|Sì|Sì|||  
|Esportazione in Word e supporto formato RTF|Sì|Sì|Sì|Sì|Sì|||  
|Misuratori e grafici migliorati|Sì|Sì|Sì|Sì|Sì|||  
|Esportazione nei formati Excel, PDF e immagine|Sì|Sì|Sì|Sì|Sì|||  
|Autenticazione personalizzata|Sì|Sì|Sì|Sì|Sì|||  
|Dati del report come feed di dati|Sì|Sì|Sì|Sì|Sì|||  
|Supporto modelli|Sì|Sì|Sì|Sì||||  
|Creare ruoli personalizzati per la sicurezza basata sui ruoli|Sì|Sì|Sì|||||  
|Sicurezza elemento modello|Sì|Sì|Sì|||||  
|Click-through illimitato|Sì|Sì|Sì|||||  
|Libreria componenti condivisa|Sì|Sì|Sì|||||  
|Sottoscrizioni e pianificazione posta elettronica e condivisione file|Sì|Sì|Sì|||||  
|Cronologia report, esecuzione snapshot e memorizzazione nella cache|Sì|Sì|Sì|||||  
|Integrazione con SharePoint|Sì|Sì|Sì|||||  
|Supporto origini dati remote e non SQL<sup>1</sup>|Sì|Sì|Sì|||||  
|Estensibilità RDCE per il rendering, il recapito e le origini dati|Sì|Sì|Sì|||||  
|Sottoscrizione di report guidate dai dati|Sì|Sì||||||  
|Distribuzione con scalabilità orizzontale (Web farm)|Sì|Sì||||||  
|Avvisi<sup>2</sup>|Sì|Sì||||||  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] <sup>2</sup>|Sì|Sì||||||  
  
 <sup>1</sup>per ulteriori informazioni sulle origini dati supportate in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)], vedere [origini dati supportate da Reporting Services &#40;SSRS&#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
 <sup>2</sup>richiede [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in modalità SharePoint. Per altre informazioni, vedere [installazione in modalità SharePoint di Reporting Services &#40;SharePoint 2010 e SharePoint 2013&#41;](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
### <a name="report-server-database-server-edition-requirements"></a>Requisiti dell'edizione server del database del server di report  
 Quando si crea un database del server di report, non tutte le edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] possono essere usate per ospitare il database. Nella tabella seguente sono illustrate le edizioni del [!INCLUDE[ssDE](../includes/ssde-md.md)] che è possibile usare per le edizioni specifiche di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Per questa edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Edizione dell'istanza del Motore di database da usare per ospitare il database|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Edizioni Standard, Business Intelligence Enterprise (locali o remote)|  
|Business Intelligence|Edizioni Standard, Business Intelligence Enterprise (locali o remote)|  
|Standard|Edizioni Standard, Enterprise (locali o remote)|  
|Web|Web Edition (solo locale)|  
|Express with Advanced Services|Express with Advanced Services (solo locale).|  
|Copia di valutazione|Copia di valutazione|  
  
##  <a name="BIClients"></a> Client di Business Intelligence  
 Le seguenti applicazioni client software sono disponibili nel centro Downloads Microsoft e vengono fornite per la creazione di documenti di business intelligence eseguiti in un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] istanza. Quando si ospitano i documenti in un ambiente server, usare un'edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supportata per tale tipo di documento. Nella tabella seguente viene indicata l'edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contenente le funzionalità del server richieste per ospitare i documenti creati in queste applicazioni client.  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)]|Sì|Sì|Sì|||||  
|Componenti aggiuntivi di data mining per Excel e Visio 2010|Sì|Sì|Sì|||||  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 2010|Sì|Sì||||||  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]|Sì|Sì||||||  
  
> [!NOTE]  
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] è un componente aggiuntivo di Excel e non dipende da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Tuttavia [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] è richiesto per la condivisione e collaborazione con le cartelle di lavoro [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] in SharePoint e questa funzionalità è disponibile come parte delle edizioni [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise e Business Intelligence.  
> 2.  La tabella sopra riportata identifica le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] edizioni necessarie per abilitare gli strumenti client; tuttavia queste funzionalità possono accedere ai dati ospitati in qualsiasi edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Spatial"></a> Spatial and Location Services  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Indici spaziali|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Tipi di dati planari e geodetici|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Librerie spaziali avanzate|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Importazione/esportazione di formati di dati spaziali standard del settore|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
  
##  <a name="Add_DBServices"></a> Additional Database Services  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Posta elettronica database|Sì|Sì|Sì|Sì||||  
  
##  <a name="Other_Components"></a> Altri componenti  
  
|Nome funzionalità|Enterprise|Business Intelligence|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Data Quality Services|Sì|Sì||||||  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|StreamInsight Standard Edition||||  
|StreamInsight HA|StreamInsight Premium Edition|||||||  
  
## <a name="see-also"></a>Vedere anche  
 [Specifiche di prodotto per SQL Server 2014](../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [Installazione di SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Guida introduttiva all'installazione di SQL Server 2014](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  