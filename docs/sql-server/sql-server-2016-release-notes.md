---
title: Note sulla versione di SQL Server 2016 | Microsoft Docs
ms.date: 02/27/2018
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-non-specified
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- build notes
- release issues
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
caps.latest.revision: 
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 6485ef83b940ab9d04b9406e461517d5254aec7f
ms.sourcegitcommit: 1a3584a60c12521ba5b4b12a18d8cb32b1f2d555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="sql-server-2016-release-notes"></a>Note sulla versione di SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
Questo articolo descrive le limitazioni e i problemi relativi alle versioni di SQL Server 2016. Per informazioni sulle novità, vedere [Novità di SQL Server 2016](https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2016).

> [![Download da Evaluation Center](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)  Scaricare SQL Server 2016 da **[Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**
>
> [![Macchina virtuale di Azure piccola](../includes/media/azure-vm.png)](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Se si ha un account di Azure,  fare clic **[qui](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** per creare rapidamente una macchina virtuale in cui è già installato SQL Server 2016 SP1.
>
> [![Download di SSMS](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) Per ottenere la versione più recente di SQL Server Management Studio, vedere **[Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)**.

## <a name="bkmk_2016sp1"></a>SQL Server 2016 Service Pack 1 (SP1) disponibile
![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP1 consente di aggiornare tutte le edizioni e i livelli di servizio di SQL Server 2016 a SQL Server 2016 SP1. Oltre alle correzioni elencate in questo articolo, SQL Server 2016 SP1 include gli aggiornamenti rapidi inclusi in SQL Server 2016 Cumulative Update 1 (CU1) fino a SQL Server 2016 CU3.

- [Pagina di download di SQL Server 2016 SP1](https://www.microsoft.com/download/details.aspx?id=54276)
- [Informazioni sulla versione di SQL Server 2016 Service Pack 1](https://support.microsoft.com/kb/3182545) Elenca i singoli bug e problemi che sono stati risolti o modificati in SP1.
 - ![info_tip](../sql-server/media/info-tip.png) Vedere [SQL Server Update Center](https://msdn.microsoft.com/library/ff803383.aspx) (Centro aggiornamenti di SQL Server) per collegamenti e informazioni per tutte le versioni supportate, compresi i Service Pack di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 

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
