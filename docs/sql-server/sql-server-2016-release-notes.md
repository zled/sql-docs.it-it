---
title: Note sulla versione di SQL Server 2016 | Microsoft Docs
ms.date: 03/14/2018
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: sql-non-specified
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- server-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- build notes
- release issues
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
caps.latest.revision: ''
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 1a6d422098fdacb3a7bc6392b99fe63bb25c2c36
ms.sourcegitcommit: 6e16d1616985d65484c72f5e0f34fb2973f828f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2018
---
# <a name="sql-server-2016-release-notes"></a>Note sulla versione di SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
  Questo articolo descrive le limitazioni e i problemi relativi alle versioni di SQL Server 2016, inclusi i Service Pack. Per informazioni sulle novità, vedere [Novità di SQL Server 2016](https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2016).

> [![Download da Evaluation Center](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)  Scaricare SQL Server 2016 da **[Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**
>
> [![Macchina virtuale di Azure piccola](../includes/media/azure-vm.png)](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Se si ha un account di Azure,  fare clic **[qui](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** per creare rapidamente una macchina virtuale in cui è già installato SQL Server 2016 SP1.
>
> [![Download di SSMS](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) Per ottenere la versione più recente di SQL Server Management Studio, vedere **[Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)**.

## <a name="bkmk_2016sp1"></a>SQL Server 2016 Service Pack 1 (SP1)
![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP1 include tutte le correzioni fino a SQL Server 2016 RTM CU3, incluso l'aggiornamento della protezione MS16-136. Contiene un rollup delle soluzioni disponibili negli aggiornamenti cumulativi di SQL Server 2016 fino all'aggiornamento cumulativo più recente, CU3, incluso e all'aggiornamento della protezione MS16-136 rilasciato l'8 novembre 2016. 

Le funzionalità seguenti sono disponibili nelle edizioni Standard, Web, Express e database locale di SQL Server SP1 (ad eccezione dei casi indicati):
- Always Encrypted
- Changed Data Capture (non disponibile in Express)
- columnstore
- Compressione
- Mascheramento dati dinamici
- Controllo con granularità fine
- OLTP in memoria (non disponibile nel database locale)
- Più contenitori FileStream (non disponibili nel database locale)
- Partizionamento
- PolyBase
- Protezione a livello di riga

La tabella seguente contiene un riepilogo dei principali miglioramenti disponibili in SQL Server 2016 SP1.

|Funzionalità|Description|Per ulteriori informazioni|
|---|---|---|
|Inserimento in blocco negli heap con TABLOCK automatico in TF 715| Trace Flag 715 abilita il blocco della tabella per le operazioni di caricamento bulk in heap senza indici non cluster.|[La migrazione dei carichi di lavoro SAP a SQL Server è 2,5 volte più veloce](https://blogs.msdn.microsoft.com/sql_server_team/migrating-sap-workloads-to-sql-server-just-got-2-5x-faster/)|
|CREATE o ALTER|Consentono la distribuzione di oggetti, ad esempio stored procedure, trigger, funzioni definite dall'utente e visualizzazioni.|[Blog sul motore di database di SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/11/17/create-or-alter-another-great-language-enhancement-in-sql-server-2016-sp1/)|
|Supporto DROP TABLE per la replica|Supporto DDL DROP TABLE per la replica per consentire l'eliminazione degli articoli relativi alla replica.|[KB 3170123](https://support.microsoft.com/help/3170123/supports-drop-table-ddl-for-articles-that-are-included-in-transactiona)|
|Firma del driver RsFx FileStream|Il driver RsFx FileStream viene firmato e certificato usando il dashboard del centro per sviluppatori di hardware Windows (portale per sviluppatori) che consente di installare il driver RsFx FileStream di SQL Server 2016 SP1 in Windows Server 2016 o Windows 10 senza alcun problema.|[La migrazione dei carichi di lavoro SAP a SQL Server è 2,5 volte più veloce](https://blogs.msdn.microsoft.com/sql_server_team/migrating-sap-workloads-to-sql-server-just-got-2-5x-faster/)|
|Privilegi LPIM per l'account del servizio SQL, identificazione a livello di codice|Consentono agli amministratori di database di verificare a livello di programmazione se il privilegio Blocco di pagine in memoria (LPIM) è attivo al momento dell'avvio di servizio.|[Scelta degli sviluppatori: identificare a livello di codice i privilegi LPIM e IFI in SQL Server](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-programmatically-identify-lpim-and-ifi-privileges-in-sql-server)|
|Pulizia manuale rilevamento modifiche|Una nuova stored procedure elimina su richiesta la tabella interna del rilevamento delle modifiche.| [KB 3173157](https://support.microsoft.com/help/3173157/adds-a-stored-procedure-for-the-manual-cleanup-of-the-change-tracking)|
|Modifiche dell'operatore parallelo INSERT...SELECT per le tabelle temporanee locali|Nuovo operatore INSERT parallelo nelle operazioni INSERT..SELECT.|[Team di consulenza clienti di SQL Server](https://blogs.msdn.microsoft.com/sqlcat/2016/07/21/real-world-parallel-insert-what-else-you-need-to-know/)|
|Showplan XML|Diagnostica ampliata che include avvisi di concessione e memoria massima abilitata per una query, flag di traccia abilitati e altre informazioni di diagnostica. | [KB 3190761](https://support.microsoft.com/help/3190761/update-to-improve-diagnostics-by-expose-data-type-of-the-parameters-fo)|
|Storage Class Memory|Ottimizzare l'elaborazione delle transazioni usando Storage Class Memory in Windows Server 2016, che consente di accelerare i tempi di commit delle transazioni per ordini di grandezza.|[Blog sul motore di database di SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/12/02/transaction-commit-latency-acceleration-using-storage-class-memory-in-windows-server-2016sql-server-2016-sp1/)|
|USE HINT|Usare l'opzione di query `OPTION(USE HINT('<option>'))` per modificare il comportamento di Query Optimizer usando hint supportati per il livello di query. A differenza di QUERYTRACEON, l'opzione USE HINT non richiede privilegi sysadmin.|[Scelta degli sviluppatori: hint USE HINT per la query](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-use-hint-query-hints/)|
|Aggiunte di XEvent|Nuove funzionalità di diagnostica di XEvent e Perfmon migliorano la risoluzione dei problemi di latenza.|[Eventi estesi](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)|

Inoltre, tenere presenti le correzioni seguenti:
- In base ai suggerimenti degli amministratori di database e della community di SQL, a partire da SQL 2016 SP1 i messaggi di registrazione Hekaton sono ridotti al minimo.
- Esaminare i nuovi [flag di traccia](https://docs.microsoft.com/en-us/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).
- Le versioni complete dei database di esempio WideWorldImporters ora funzionano con le edizioni Standard ed Express, a partire da SQL Server 2016 SP1, e sono disponibili su [GitHub]( https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0). Non sono necessarie modifiche nell'esempio. I backup del database creati in RTM per l'edizione Enterprise funzionano con le edizioni Standard ed Express in SP1. 

L'installazione di SQL Server 2016 SP1 può richiedere il riavvio dopo l'installazione. Come procedura consigliata, è opportuno pianificare ed eseguire un riavvio dopo l'installazione di SQL Server 2016 SP1.

### <a name="download-pages-and-more-information"></a>Scaricare le pagine e altre informazioni

- [Download del Service Pack 1 per Microsoft SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=54276)
- [Blog sul rilascio di SQL Server 2016 Service Pack 1 (SP1)](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/)
- [Informazioni sulla versione di SQL Server 2016 Service Pack 1](https://support.microsoft.com/kb/3182545)
- ![info_tip](../sql-server/media/info-tip.png) [Centro aggiornamenti di SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) per collegamenti e informazioni per tutte le versioni supportate, compresi i Service Pack di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 

##  <a name="bkmk_2016_ga"></a> SQL Server 2016 Release - General Availability (GA)
-   [Motore di database (GA)](#bkmk_ga_instalpatch) 
-   [Stretch Database (GA)](#bkmk_ga_stretch)
-   [Archivio query (GA)](#bkmk_ga_query_store)
-   [Documentazione del prodotto (GA)](#bkmk_ga_docs)
 
### ![repl_icon_warn](../database-engine/availability-groups/windows/media/repl-icon-warn.gif) <a name="bkmk_ga_instalpatch"></a> Install Patch Requirement (GA) 
**Problema e impatto per i clienti:** Microsoft ha identificato un problema con i file binari di Microsoft VC++ 2013 Runtime che vengono installati come prerequisito da SQL Server 2016. È disponibile un aggiornamento per risolvere questo problema. Se questo aggiornamento dei file binari di VC++ Runtime non viene installato, potrebbero verificarsi problemi di stabilità di SQL Server 2016 in determinati scenari. Prima di installare SQL Server 2016, verificare se il computer richiede la patch descritta in [KB 3164398](http://support.microsoft.com/kb/3164398). La patch è inclusa anche nell'[aggiornamento cumulativo 1 (CU1) per SQL Server 2016 RTM](https://www.microsoft.com/download/details.aspx?id=53338). 

**Risoluzione:** usare una delle soluzioni seguenti:

- Installare l'aggiornamento per Visual C++ 2013 e Visual C++ Redistributable Package ( [KB 3138367](http://support.microsoft.com/kb/3138367)). La soluzione nella KB è la soluzione consigliata. È possibile installarlo prima o dopo l'installazione di SQL Server 2016. 

    Se è già installato SQL Server 2016, eseguire i passaggi seguenti nell'ordine indicato:

    1.  Scaricare il file *vcredist_\*exe*.
    1.  Arrestare il servizio SQL Server per tutte le istanze del motore di database.
    1.  Installare **KB 3138367**.
    1.  Riavviare il computer.
 

 - Installare l'aggiornamento critico per i prerequisiti della libreria MSVCRT per SQL Server 2016 (  [KB 3164398](http://support.microsoft.com/kb/3164398)).  
 
    Se si usa **KB 3164398**, è possibile installare durante l'installazione di SQL Server, tramite Microsoft Update o dall'Area download Microsoft. 

    - **Durante l'installazione di SQL Server 2016:** se il computer che esegue il programma di installazione di SQL Server ha accesso a Internet, l'aggiornamento viene cercato durante il processo di installazione di SQL Server. Se si accetta l'aggiornamento, i file binari vengono scaricati e aggiornati durante l'installazione.

    - **Microsoft Update:** l'aggiornamento è disponibile tramite Microsoft Update come aggiornamento critico per SQL Server 2016 non correlato alla sicurezza. Quando si esegue l'installazione tramite Microsoft Update, SQL Server 2016 richiede quindi il riavvio del server. 

    - **Area download:** infine, l'aggiornamento è disponibile nell'Area download Microsoft. È possibile scaricare il software per l'aggiornamento e installarlo nei server in cui è presente SQL Server 2016. 


### <a name="bkmk_ga_stretch"></a>Stretch Database

#### <a name="problem-with-a-specific-character-in-a-database-or-table-name"></a>Problema con un carattere specifico in un nome di database o tabella

**Problema e impatto per i clienti:** se si tenta di abilitare Stretch Database in un database o in una tabella, si ottiene un errore. Il problema si verifica se il nome dell'oggetto include un carattere che viene considerato come un carattere diverso quando viene convertito da minuscolo a maiuscolo. Un esempio di carattere che causa questo problema è il carattere "ƒ" (creato digitando ALT+159).

**Soluzione alternativa:** se si vuole abilitare Stretch Database nel database o nella tabella, l'unica possibilità è rinominare l'oggetto e rimuovere il carattere che causa il problema.

#### <a name="problem-with-an-index-that-uses-the-include-keyword"></a>Problema relativo a un indice che usa la parola chiave INCLUDE

**Problema e impatto per i clienti:** se si cerca di abilitare Stretch Database in una tabella che include un indice che usa la parola chiave INCLUDE per includere altre colonne nell'indice, l'operazione non riesce e viene visualizzato un errore.

**Soluzione alternativa:** eliminare l'indice che include la parola chiave INCLUDE, abilitare Stretch Database nella tabella, quindi ricreare l'indice. In questo caso, assicurarsi di seguire i criteri e le procedure di manutenzione dell'organizzazione per eliminare o ridurre al minimo l'impatto per gli utenti della tabella interessata.

### <a name="bkmk_ga_query_store"></a>Query Store

#### <a name="problem-with-automatic-data-cleanup-on-editions-other-than-enterprise-and-developer"></a>Problema relativo alla pulizia automatica dei dati nelle edizioni diverse da Enterprise e Developer

 **Problema e impatto per i clienti:** la pulizia automatica dei dati ha esito negativo nelle edizioni diverse da Enterprise e Developer. Di conseguenza, se i dati non vengono eliminati manualmente, lo spazio usato da Query Store aumenterà nel tempo fino a quando non viene raggiunto il limite configurato. Se non viene risolto, questo problema determinerà anche l'esaurimento dello spazio su disco allocato per i log degli errori, dato che a ogni tentativo di pulizia viene generato un file di dump. Il periodo di attivazione della pulizia dipende dalla frequenza del carico di lavoro, ma non supera i 15 minuti.

 **Soluzione alternativa:** se si prevede di usare l'archivio query in edizioni diverse da Enterprise e Developer, è necessario disattivare i criteri di pulizia in modo esplicito. Questa operazione si può eseguire da SQL Server Management Studio (pagina delle proprietà del database) oppure tramite script Transact-SQL:

```ALTER DATABASE <database name> SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 0), SIZE_BASED_CLEANUP_MODE = OFF)```

Inoltre, prendere in considerazione le opzioni per la pulizia manuale per evitare che l'archivio query passi alla modalità di sola lettura. Ad esempio, eseguire periodicamente la query seguente per pulire l'intero spazio dati:

```ALTER DATABASE <database name> SET QUERY_STORE CLEAR```

Inoltre, eseguire periodicamente le stored procedure dell'archivio query per pulire statistiche di runtime, query specifiche o piani:

- `sp_query_store_reset_exec_stats`

- `sp_query_store_remove_plan`

- `sp_query_store_remove_query`


###  <a name="bkmk_ga_docs"></a> Documentazione del prodotto (GA) 
 **Problema e impatto per i clienti:** una versione scaricabile della documentazione di SQL Server 2016 non è ancora disponibile. Quando si usa Gestione librerie della Guida per provare a **installare contenuto online**, viene visualizzata la documentazione di SQL Server 2012 e SQL Server 2014, ma non è disponibile alcuna opzione per la documentazione di SQL Server 2016.    
    
 **Soluzione alternativa:** usare una delle soluzioni alternative seguenti:    
    
 ![Gestire le impostazioni della Guida per SQL Server](../sql-server/media/docs-sql2016-managehelpsettings.png "Gestire le impostazioni della Guida per SQL Server")    
    
-   Usare l'opzione **Scegliere di utilizzare la Guida online o locale** e configurare la Guida per l'uso della Guida online.    
    
-   Usare l'opzione **Installa contenuto da online** e scaricare i contenuti relativi a SQL Server 2014.    
    
 **Guida sensibile al contesto:** in base alla progettazione, quando si preme F1 in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] viene visualizzata nel browser la versione online degli articoli della Guida sensibile al contesto. Il problema è costituito dalla visualizzazione della Guida basata su browser anche se è stata installata e configurata la Guida locale. 
     
**Aggiornamento del contenuto:**    
In SQL Server Management Studio e Visual Studio l'applicazione Visualizzatore della Guida potrebbe bloccarsi durante l'aggiunta della documentazione. Per risolvere questo problema, eseguire la procedura seguente. Per altre informazioni su questo problema, vedere [Il visualizzatore della Guida di Visual Studio si blocca](https://msdn.microsoft.com/library/mt654096.aspx).    
    
* Aprire il file %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings nel Blocco note e impostare una data futura nel codice seguente.    
    
     
```    
     Cache LastRefreshed="12/31/2017 00:00:00"    
``` 

## <a name="additional-information"></a>Informazioni aggiuntive
+ [Installazione di SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)
+ [SQL Server Update Center (Centro aggiornamenti di SQL Server): collegamenti e informazioni per tutte le versioni supportate](https://msdn.microsoft.com/library/ff803383.aspx)


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]    

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png "MS_Logo_X-Small")    
