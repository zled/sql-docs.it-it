---
title: "Note sulla versione di SQL Server 2016 | Microsoft Docs"
ms.date: "11/28/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "note sulla build"
  - "problemi della versione"
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
caps.latest.revision: 276
author: "craigg-msft"
ms.author: "craigg"
manager: "jhubbard"
caps.handback.revision: 276
---
# Note sulla versione di SQL Server 2016
  Questo argomento descrive i limiti e i problemi relativi a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .    
    
 **Per provarlo:**    
   
[![Download da Evaluation Center](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) Scaricare SQL Server 2016 da **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
[![Macchina virtuale di Azure piccola](../analysis-services/media/azure-virtual-machine-small.png)](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Se si ha un account di Azure,  fare clic **[qui](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** per creare rapidamente una macchina virtuale in cui è già installato SQL Server 2016 SP1.
    
[![Download di SSMS](../analysis-services/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **SSMS:** Per ottenere la versione più recente di SQL Server Management Studio, vedere **[Scaricare SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx)**.   
    
 Per informazioni sulle novità, vedere [Novità di SQL Server 2016](What's%20New%20in%20Report%20Builder%20for%20SQL%20Server%202016.md).
    
##  <a name="a-namebkmktopa-sections-in-this-topic"></a><a name="bkmk_top"></a> Sezioni dell'argomento:    

-   [SQL Server 2016 Service Pack 1 (SP1) disponibile](#bkmk_2016sp1)    
-   [SQL Server 2016 General Availability (GA)](#bkmk_2016_ga) 
-   [SQL Server 2016 Release Candidate 3 (RC3)](#bkmk_2016_rc3)     

## <a name="a-namebkmk2016sp1asql-server-2016-service-pack-1-sp1-available"></a><a name="bkmk_2016sp1"></a>SQL Server 2016 Service Pack 1 (SP1) disponibile
![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP1 consente di aggiornare tutte le edizioni e i livelli di servizio di SQL Server 2016 a SQL Server 2016 SP1. Oltre alle correzioni elencate in questo articolo, SQL Server 2016 SP1 include gli aggiornamenti rapidi inclusi in SQL Server 2016 Cumulative Update 1 (CU1) fino a SQL Server 2016 CU3.
    
- [Pagina di download di SQL Server 2016 SP1](https://www.microsoft.com/en-us/download/details.aspx?id=54276)
- [Informazioni sulla versione di SQL Server 2016 Service Pack 1](https://support.microsoft.com/en-us/kb/3182545) Elenca i singoli bug e problemi che sono stati risolti o modificati in SP1.
 - ![info_tip](../sql-server/media/info-tip.png) Vedere la pagina relativa al [centro aggiornamenti di SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) per collegamenti e informazioni per tutte le versioni supportate, compresi i Service Pack di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 
    
    
##  <a name="a-namebkmk2016gaa-sql-server-2016-release---general-availability-ga"></a><a name="bkmk_2016_ga"></a> SQL Server 2016 General Availability (GA)
-   [Motore di database (GA)](#bkmk_ga_instalpatch) 

-   [Estensione database (GA)](#bkmk_ga_stretch)

-   [Archivio query (GA)](#bkmk_ga_query_store)

-   [Documentazione del prodotto (GA)](#bkmk_ga_docs)
 
### <a name="repliconwarnimagerepliconwarngif-a-namebkmkgainstalpatcha-install-patch-requirement-ga"></a>![repl_icon_warn](../database-engine/availability-groups/windows/media/repl-icon-warn.png) <a name="bkmk_ga_instalpatch"></a> Requisito di installazione patch (GA) 
**Problema e impatto per i clienti:** Microsoft ha identificato un problema con i file binari di Microsoft VC++ 2013 Runtime che vengono installati come prerequisito da SQL Server 2016. È disponibile un aggiornamento per risolvere questo problema. Se questo aggiornamento dei file binari di VC++ Runtime non viene installato, potrebbero verificarsi problemi di stabilità di SQL Server 2016 in determinati scenari. Prima di installare SQL Server 2016, verificare se il computer richiede la patch descritta in [KB 3164398](http://support.microsoft.com/kb/3164398). La patch è inclusa anche nel [pacchetto di aggiornamento cumulativo 1 (CU1) per SQL Server 2016 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=53338). 

**Soluzione:** eseguire una delle operazioni seguenti:

- Installare l'aggiornamento per Visual C++ 2013 e Visual C++ Redistributable Package ([KB 3138367](http://support.microsoft.com/kb/3138367)). Questa è la soluzione consigliata. È possibile installarlo prima o dopo l'installazione di SQL Server 2016. 

    Se è già installato SQL Server 2016, eseguire i passaggi seguenti nell'ordine indicato:

    1.  Scaricare il file *vcredist_\*exe*.
    1.  Arrestare il servizio SQL Server per tutte le istanze del motore di database.
    1.  Installare **KB 3138367**.
    1.  Riavviare il computer.
 

 - Installare l'aggiornamento critico per i prerequisiti della libreria MSVCRT per SQL Server 2016 ([KB 3164398](http://support.microsoft.com/kb/3164398)).  
 
    Se si usa **KB 3164398**, è possibile installare durante l'installazione di SQL Server, tramite Microsoft Update o dall'Area download Microsoft. 

    - **Durante l'installazione di SQL Server 2016:** se il computer che esegue il programma di installazione di SQL Server ha accesso a Internet, l'aggiornamento verrà cercato durante il processo di installazione di SQL Server. Se si accetta l'aggiornamento, verranno scaricati e aggiornati i file binari durante l'installazione.

    - **Microsoft Update:** l'aggiornamento è disponibile tramite Microsoft Update come aggiornamento critico per SQL Server 2016 non correlato alla sicurezza. Quando si esegue l'installazione tramite Microsoft Update dopo SQL Server 2016, al termine dell'aggiornamento verrà richiesto il riavvio del server. 

    - **Area download:** infine, l'aggiornamento è disponibile nell'Area download Microsoft. È possibile scaricare il software per l'aggiornamento e installarlo nei server in cui è presente SQL Server 2016. 


### <a name="a-namebkmkgastretchastretch-database"></a><a name="bkmk_ga_stretch"></a>Estensione database

#### <a name="problem-with-a-specific-character-in-a-database-or-table-name"></a>Problema con un carattere specifico in un nome di database o tabella

**Problema e impatto per i clienti:** se si cerca di abilitare Estensione database in un database o in una tabella, l'operazione non riesce e viene visualizzato un errore se il nome dell'oggetto include un carattere che viene considerato come carattere diverso quando viene convertito da minuscolo a maiuscolo. Un esempio di un carattere che causa questo problema è il carattere "ƒ" (creato digitando ALT+159).

**Soluzione alternativa:** se si vuole abilitare Estensione database nel database o nella tabella, l'unica possibilità è rinominare l'oggetto e rimuovere il carattere che causa il problema.

#### <a name="problem-with-an-index-that-uses-the-include-keyword"></a>Problema relativo a un indice che usa la parola chiave INCLUDE

**Problema e impatto per i clienti:** se si cerca di abilitare Estensione database in una tabella che include un indice che usa la parola chiave INCLUDE per includere altre colonne nell'indice, l'operazione non riesce e viene visualizzato un errore.

**Soluzione alternativa:** eliminare l'indice che include la parola chiave INCLUDE, abilitare Estensione database nella tabella, quindi ricreare l'indice. In questo caso, assicurarsi di seguire i criteri e le procedure di manutenzione dell'organizzazione per eliminare o ridurre al minimo l'impatto per gli utenti della tabella interessata.

### <a name="a-namebkmkgaquerystoreaquery-store"></a><a name="bkmk_ga_query_store"></a>Archivio query

#### <a name="problem-with-automatic-data-cleanup-on-editions-other-than-enterprise-and-developer"></a>Problema relativo alla pulizia automatica dei dati nelle edizioni diverse da Enterprise e Developer

 **Problema e impatto per i clienti:** la pulizia automatica dei dati ha esito negativo nelle edizioni diverse da Enterprise e Developer. Di conseguenza, lo spazio usato dall'archivio query aumenterà nel tempo fino a quando non viene raggiunto il limite configurato, se i dati non vengono eliminati manualmente. Se non viene risolto, questo problema determinerà anche l'esaurimento dello spazio su disco allocato per i log degli errori, dato che a ogni tentativo di pulizia viene generato un file di dump. Il periodo di attivazione della pulizia dipende dalla frequenza del carico di lavoro, ma non supera i 15 minuti.

 **Soluzione alternativa:** se si prevede di usare l'archivio query in edizioni diverse da Enterprise e Developer, è necessario disattivare i criteri di pulizia in modo esplicito. Questa operazione si può eseguire da SQL Server Management Studio (pagina delle proprietà del database) oppure tramite script Transact-SQL:

```ALTER DATABASE <database name> SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 0), SIZE_BASED_CLEANUP_MODE = OFF)```

Inoltre, prendere in considerazione le opzioni per la pulizia manuale per evitare che l'archivio query passi alla modalità di sola lettura. Ad esempio, eseguire periodicamente la query seguente per pulire l'intero spazio dati:

```ALTER DATABASE <database name> SET QUERY_STORE CLEAR```

Inoltre, eseguire periodicamente le stored procedure dell'archivio query per pulire statistiche di runtime, query specifiche o piani:

-    ```sp_query_store_reset_exec_stats```

-    ```sp_query_store_remove_plan```

-    ```sp_query_store_remove_query```


###  <a name="a-namebkmkgadocsa-product-documentation-ga"></a><a name="bkmk_ga_docs"></a> Documentazione del prodotto (GA) 
 **Problema e impatto per i clienti:** una versione scaricabile della documentazione di SQL Server 2016 non è ancora disponibile. Quando si usa Gestione librerie della Guida per provare a **installare contenuto online**, viene visualizzata la documentazione di SQL Server 2012 e SQL Sever 2014, mentre non è disponibile alcuna opzione per la documentazione di SQL Server 2016.    
    
 **Soluzione alternativa:** usare una delle opzioni seguenti:    
    
 ![Manage Help Settings for SQL Server](../sql-server/media/docs-sql2016-managehelpsettings.png "Manage Help Settings for SQL Server")    
    
-   Usare l'opzione **Scegliere di utilizzare la Guida online o locale** e configurare la Guida per l'uso della Guida online.    
    
-   Usare l'opzione **Installa contenuto da online** e scaricare i contenuti relativi a SQL Server 2014.    
    
 **Guida sensibile al contesto:** da progettazione, quando si preme F1 in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] viene visualizzata la versione online degli argomenti della Guida sensibile al contesto nel browser. Ciò si verifica anche se è stata installata la Guida locale.    
     
**Aggiornamento del contenuto:**    
In SQL Server Management Studio e Visual Studio l'applicazione Visualizzatore della Guida potrebbe bloccarsi durante l'aggiunta della documentazione. Per risolvere il problema, eseguire le operazioni seguenti. Per altre informazioni su questo problema, vedere [Il visualizzatore della Guida di Visual Studio si blocca](https://msdn.microsoft.com/library/mt654096.aspx).    
    
* Aprire il file %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings nel Blocco note e impostare una data futura nel codice seguente.    
    
     
```    
     Cache LastRefreshed="12/31/2017 00:00:00"    
``` 
![horizontal_bar](../sql-server/media/horizontal-bar.png "horizontal_bar")  
##  <a name="a-namebkmk2016rc3a-sql-server-2016-release-candidate-3-rc3"></a><a name="bkmk_2016_rc3"></a> SQL Server 2016 Release Candidate 3 (RC3)    
-   [Documentazione del prodotto (RC2)](#bkmk_rc3_docs)    
-   [PolyBase (RC3)](#bkmk_rc3_polybase) 

    
###  <a name="a-namebkmkrc3docsa-product-documentation-rc3"></a><a name="bkmk_rc3_docs"></a> Documentazione del prodotto (RC3)    
 **Problema e impatto per i clienti:** una versione scaricabile della documentazione di SQL Server 2016 non è ancora disponibile. Quando si usa Gestione librerie della Guida per provare a **installare contenuto online**, viene visualizzata la documentazione di SQL Server 2012 e SQL Sever 2014, mentre non è disponibile alcuna opzione per la documentazione di SQL Server 2016.    
    
 **Soluzione alternativa:** usare una delle opzioni seguenti:    
    
 ![Manage Help Settings for SQL Server](../sql-server/media/docs-sql2016-managehelpsettings.png "Manage Help Settings for SQL Server")    
    
-   Usare l'opzione **Scegliere di utilizzare la Guida online o locale** e configurare la Guida per l'uso della Guida online.    
    
-   Usare l'opzione **Installa contenuto da online** e scaricare i contenuti relativi a SQL Server 2014.    
    
 **Guida sensibile al contesto:** da progettazione, quando si preme F1 in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] viene visualizzata la versione online degli argomenti della Guida sensibile al contesto nel browser. Ciò si verifica anche se è stata installata la Guida locale.    
     
**Aggiornamento del contenuto:**    
In SQL Server Management Studio e Visual Studio l'applicazione Visualizzatore della Guida potrebbe bloccarsi durante l'aggiunta della documentazione. Per risolvere il problema, eseguire le operazioni seguenti. Per altre informazioni su questo problema, vedere [Il visualizzatore della Guida di Visual Studio si blocca](https://msdn.microsoft.com/library/mt654096.aspx).    
    
* Aprire il file %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings nel Blocco note e impostare una data futura nel codice seguente.    
    
     
```    
     Cache LastRefreshed="12/31/2017 00:00:00"    
```    
    
###  <a name="a-namebkmkrc3polybasea-polybase-rc3"></a><a name="bkmk_rc3_polybase"></a> PolyBase (RC3)        
 Le query PolyBase possono avere esito negativo dopo l'aggiornamento da RC1 o versioni precedenti.    
    
 **Problema e impatto per i clienti**: dopo l'aggiornamento da SQL Server 2016 RC1 o versioni precedenti, le query PolyBase, l'importazione e l'esportazione possono avere esito negativo e generare l'errore seguente: "Errore interno di Query Processor: errore imprevisto durante l'elaborazione di una fase di query remota".    
    
 **Soluzione alternativa**    
    
-   Disinstallare PolyBase. Nel **Pannello di controllo** fare clic su **Disinstalla un programma**, su **Microsoft SQL Server 2016** e quindi su **Rimuovi**. Nella procedura guidata Rimuovi SQL Server 2016 selezionare l'istanza con l'installazione di PolyBase non riuscita e fare clic su **Avanti**. In Funzionalità fare clic su **Servizio query PolyBase per i dati esterni**. Non è necessario rimuovere altre funzionalità installate correttamente. Completare i passaggi della procedura guidata Rimuovi SQL Server 2016.    
    
-   Reinstallare PolyBase. Eseguire il programma di installazione e aggiungere funzionalità PolyBase nella stessa istanza di SQL Server.    
    
 **Si applica a**: SQL Server 2016 RC3 in caso di aggiornamento da RC1 o versioni precedenti.    
 
## <a name="additional-information"></a>Informazioni aggiuntive
- [Installazione per SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)
    
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png "MS_Logo_X-Small")    
    
  