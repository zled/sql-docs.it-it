---
title: "propriet&#224; server in Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SSAS, proprietà di configurazione"
  - "Analysis Services, proprietà di configurazione"
  - "SQL Server Analysis Services, proprietà di configurazione"
  - "opzioni di configurazione [Analysis Services]"
  - "proprietà server [Analysis Services]"
  - "proprietà [Analysis Services], configurazione"
  - "proprietà [Analysis Services]"
ms.assetid: 274b89cd-14ed-4666-bc13-eedf1de51e18
caps.latest.revision: 21
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 21
---
# propriet&#224; server in Analysis Services
  Un amministratore di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] può modificare le proprietà di configurazione del server predefinite di un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ogni istanza ha proprietà di configurazione proprie, impostate in modo indipendente rispetto ad altre istanze presenti nello stesso server.  
  
 Per configurare il server, usare SQL Server Management Studio oppure modificare il file msmdsrv.ini di un'istanza specifica.  
 
Le pagine delle proprietà di SQL Server Management Studio mostrano un subset di proprietà che hanno maggiori probabilità di essere modificate. L'elenco completo delle proprietà è disponibile nel file msmdsrv.ini.   
  
> [!NOTE]  
>  In un'installazione predefinita il file msmdsrv.ini si trova nella cartella \Programmi\Microsoft SQL Server\MSAS13.MSSQLSERVER\OLAP\Config.
> 
> Altre proprietà in grado di influenzare la configurazione del server includono le proprietà di distribuzione della configurazione riportate in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Per altre informazioni su queste proprietà, vedere [Definizione delle impostazioni di configurazione per la distribuzione di soluzioni](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md).
 
##  <a name="bkmk_config"></a> Configurare le proprietà in Management Studio 
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] connettersi a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
2. In Esplora oggetti di fare clic con il pulsante destro del mouse sull'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e quindi scegliere **Proprietà**. Viene visualizzata la pagina Generale con le proprietà più di uso comune.  

3.  Per visualizzare proprietà aggiuntive, selezionare la casella di controllo **Mostra proprietà avanzate** nella parte inferiore della pagina.  
  
     La modifica delle proprietà del server è supportata solo per i server in modalità tabulare e multidimensionale. Se è stato installato [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], usare sempre i valori predefiniti, a meno che il supporto tecnico Microsoft non fornisca istruzioni diverse.  
  
     Per informazioni su come risolvere problemi operativi o riguardanti le prestazioni usando le proprietà del server, vedere la Guida operativa di [SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
     Per ottenere informazioni sulle proprietà del server, molte delle quali sono rimaste invariate rispetto alle diverse versioni precedenti, leggere il white paper Microsoft [Proprietà server di SQL Server 2005 Analysis Services (SSAS)](http://go.microsoft.com/fwlink/?LinkID=199102).    
  
##  <a name="bkmk_msmdsrvini"></a> Configurare le proprietà nel file msmdsrv.ini
  Alcune proprietà possono essere impostate solo nel file msmdsrv.ini. Se la proprietà che si desidera impostare non è visibile anche dopo aver visualizzato le proprietà avanzate, potrebbe essere necessario modificare direttamente il file msmdsrv.ini.
  
1.  Controllare la proprietà **DataDir** nella pagina delle proprietà Generale di Management Studio per verificare il percorso dei file di programma di Analysis Services, incluso il file msmdsrv.ini.

     Su un server con più istanze, la verifica del percorso del file di programma consente di determinare se si sta modificando il file corretto.  
  
2.  Passare alla cartella **config** del percorso cartella dei file di programma.

3. Creare un backup del file nel caso sia necessario ripristinare il file originale.  
  
4.  Utilizzare un editor di testo per visualizzare o modificare il file msmdsrv.ini.  
  
5.  Salvare il file e riavviare il servizio.  
  
##  <a name="bkmk_ref"></a> Guida di riferimento alle proprietà del server  
  
 Gli argomenti seguenti descrivono le varie proprietà di configurazione di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]:  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Proprietà generali](../../analysis-services/server-properties/general-properties.md)|Le proprietà generali comprendono proprietà di base e proprietà avanzate, comprese le proprietà che consentono di definire la directory dei dati, la directory di backup e altre caratteristiche di funzionamento del server.|  
|[Proprietà di data mining](../../analysis-services/server-properties/data-mining-properties.md)|Le proprietà di data mining controllano quali algoritmi di data mining vengono abilitati e quali disabilitati. Per impostazione predefinita, tutti gli algoritmi sono abilitati.| 
|[Proprietà DAX](../../analysis-services/server-properties/dax-properties.md)|Definisce le proprietà correlate alle query DAX.|
|DSO|DSO non è più supportato. Le proprietà DSO vengono ignorate.|  
|[Proprietà di funzionalità](../../analysis-services/server-properties/feature-properties.md)|Le proprietà di funzionalità controllano le funzionalità di un prodotto e nella maggior parte dei casi si tratta di proprietà avanzate, comprese le proprietà che controllano i collegamenti tra istanze di server.|  
|[Proprietà della cache dei file](../../analysis-services/server-properties/filestore-properties.md)|Le proprietà di archiviazione di file sono riservate ad utenti esperti. Queste proprietà comprendono le impostazioni avanzate di gestione della memoria.|  
|[Proprietà di Gestione blocchi](../../analysis-services/server-properties/lock-manager-properties.md)|Le proprietà di gestione dei blocchi consentono di definire il comportamento del server in relazione a blocchi e timeout. La maggior parte di queste proprietà è riservata ad utenti esperti.|  
|[Proprietà dei log](../../analysis-services/server-properties/log-properties.md)|Le proprietà di registrazione controllano se, dove e come vengono registrati gli eventi sul server. Queste proprietà riguardano anche la registrazione degli errori, delle eccezioni e delle query, l'utilità Traccia eventi e le tracce.|  
|[Proprietà della memoria](../../analysis-services/server-properties/memory-properties.md)|Le proprietà della memoria controllano come il server utilizza la memoria. Queste proprietà sono destinate principalmente ad utenti esperti.|  
|[Proprietà di rete](../../analysis-services/server-properties/network-properties.md)|Le proprietà di rete controllano il comportamento del server in relazione alle reti, comprese le proprietà che controllano la compressione e l'XML binario. La maggior parte di queste proprietà è riservata ad utenti esperti.|  
|[Proprietà OLAP](../../analysis-services/server-properties/olap-properties.md)|Le proprietà OLAP controllano l'elaborazione delle dimensioni e del cubo, l'elaborazione lenta, la memorizzazione dei dati nella cache e il comportamento delle query. Comprendono sia proprietà di base che proprietà avanzate.|  
|[Proprietà di sicurezza](../../analysis-services/server-properties/security-properties.md)|La sezione sulla sicurezza comprende proprietà di base e proprietà avanzate che consentono di definire le autorizzazioni di accesso. Comprendono anche proprietà riguardanti amministratori ed utenti.|  
|[Proprietà dei pool di thread](../../analysis-services/server-properties/thread-pool-properties.md)|Le proprietà di pooling dei thread controllano il numero di thread creati dal server. Queste proprietà sono destinate principalmente ad utenti esperti.|  
  
## Vedere anche  
 [Gestione di un'istanza di Analysis Services](../../analysis-services/instances/analysis-services-instance-management.md)   
 [Definizione delle impostazioni di configurazione per la distribuzione di soluzioni](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)  
  
  