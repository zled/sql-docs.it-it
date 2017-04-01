---
title: "Governance delle risorse per i servizi di R | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18c9978a-aa55-42bd-9ab3-8097030888c9
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Governance delle risorse per i servizi di R
  Un punto debole di R è che l'analisi di grandi quantità di dati nell'ambiente di produzione richiede hardware aggiuntivo e dati spesso viene spostati all'esterno del database per i computer non controllati dall'IT.  Per eseguire operazioni di analisi avanzata, i clienti desiderano sfruttare le risorse di server di database e di proteggere i dati, richiedono che tali operazioni soddisfino i requisiti di conformità a livello aziendale, ad esempio sicurezza e prestazioni.  
  
 In questa sezione vengono fornite informazioni su come gestire le risorse utilizzate dal runtime di R e i processi R in esecuzione utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza come contesto di calcolo.  
  
## Che cos'è la governance delle risorse?  
 Governance delle risorse è progettato per identificare e prevenire i problemi comuni in un ambiente server di database, in cui vi sono spesso più applicazioni dipendenti e più servizi per il supporto e bilanciare. Per [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], governance delle risorse include le attività:  
  
-   Identificazione di script che utilizzano risorse del server eccessive.  
  
     L'amministratore deve essere in grado di terminare o limitare i processi che utilizzano un numero eccessivo di risorse.  
  
-   Riduzione dei carichi di lavoro imprevedibili.  
  
     Ad esempio, se più processi R sono in esecuzione contemporaneamente sul server e i processi non sono isolati una da altra utilizzando i pool di risorse, la contesa tra risorse risultante potrebbe influire sulle prestazioni imprevedibili o compromettere il completamento del carico di lavoro.  
  
-   Priorità dei carichi di lavoro.  
  
     L'amministratore o il progettista deve essere in grado di specificare i carichi di lavoro che deve hanno la precedenza o garantire alcuni carichi di lavoro per il completamento nel caso di contesa di risorse.  
  
 In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è possibile utilizzare [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) per gestire le risorse utilizzate dal runtime di R e i processi R remoto.  
  
## Come utilizzare Resource Governor i processi di gestione  
 In generale, gestire le risorse allocate per i processi R creando *pool di risorse esterno* e l'assegnazione di carichi di lavoro per il pool o il pool. Un pool di risorse esterno è un nuovo tipo di pool di risorse introdotta in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], per gestire il runtime di R e altri processi esterni al motore di database.  
  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], esistono tre tipi di pool di risorse predefinito.  
  
-   Il *pool interno* rappresenta le risorse utilizzate da SQL Server e non possono essere modificate o limitate.  
  
-   Il *predefinito pool* è un pool utente predefinito che è possibile utilizzare per modificare l'utilizzo delle risorse per il server nel suo complesso. È inoltre possibile definire gruppi di utenti che appartengono al pool, per gestire l'accesso alle risorse.  
  
-   Il *predefinito pool esterni* è un pool utente predefinito per le risorse esterne. Inoltre, è possibile creare un nuovo pool di risorse esterni e definire gruppi di utenti per appartengono a questo pool.  
  
 Inoltre, è possibile creare *pool di risorse definito dall'utente* per allocare le risorse del motore di database o altre applicazioni e creare *pool di risorse esterne definite dall'utente* per gestire R e altri processi esterni.  
  
 Per un'ottima introduzione a concetti e terminologia, vedere [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md).  
  
> [!NOTE]  
>  Le nuove proprietà di Resource Governor non sono attualmente disponibili solo tramite istruzioni DDL o scripting. non è possibile creare gruppi di risorse esterne utilizzando l'interfaccia utente in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## Gestione delle risorse con Resource Governor 

   Se si è esperti di Resource Governor, vedere l'argomento per una procedura dettagliata su come modificare le risorse predefinite di istanza e creare un nuovo pool di risorse esterno:  [How To: creare un Pool di risorse per R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)   
  
 È possibile utilizzare il *pool di risorse esterno* meccanismo per gestire le risorse usate da file eseguibili R seguenti:  
  
-   Processi Rterm.exe e satellite  
  
-   Processi BxlServer.exe e satellite  
  
-   Processi satellite avviati dalla finestra di avvio  
  
 Tuttavia, non è supportata la gestione diretta di tale servizio con Resource Governor. Ciò accade perché il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] è un servizio attendibile che per impostazione predefinita può ospitare solo avvio fornite da Microsoft. Avvio attendibile viene configurati per evitare un utilizzo eccessivo di risorse.  
  
 Si consiglia di gestire i processi satellite tramite Resource Governor e ottimizzare in modo da soddisfare le esigenze di configurazione di singoli database e del carico di lavoro.  Qualsiasi processo satellite singoli, ad esempio, può essere creato o eliminato su richiesta durante l'esecuzione.  
  
## Disabilitare l'esecuzione dello Script esterno  
 Supporto per script esterni è facoltativo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione. Anche dopo l'installazione [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], la possibilità di eseguire script esterni è impostata su OFF per impostazione predefinita e manualmente è necessario riconfigurare le proprietà e riavviare l'istanza per consentire l'esecuzione di script.  
  
 Pertanto, se si verifica un problema di risorse che devono essere risolti immediatamente o un problema di sicurezza, un amministratore può immediatamente disabilitare qualsiasi esecuzione dello script esterno utilizzando [sp_configure & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) e impostando la proprietà `external scripts enabled` su FALSE o 0.  
  
## Vedere anche  
 [Gestione e monitoraggio di soluzioni R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
 [Procedura: Creare un Pool di risorse per R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)  
 [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
  