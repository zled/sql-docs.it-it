---
title: Accesso ai dati di modello tabulare | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ae74a8b-0025-450d-94a5-4e601831d420
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4763973d0ea4bf905b1c38ace337667c92186e3a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="tabular-model-data-access"></a>Accesso ai dati di modello tabulare
  L'accesso a database modello tabulare in Analysis Services può essere eseguito dalla maggior parte dei client, delle interfacce e dei linguaggi che si utilizzano per recuperare dati o metadati da un modello multidimensionale. Per altre informazioni, vedere [Accesso ai dati di modelli multidimensionali &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md).  
  
 In questo argomento vengono descritti i client, i linguaggi di query e le interfacce di programmazione che è possibile utilizzare con i modelli tabulari.  
  
## <a name="clients"></a>Client  
 Nelle applicazioni client Microsoft seguenti sono supportate connessioni native ai database modello tabulare di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
### <a name="power-bi"></a>Power BI
È possibile connettersi a un database modello tabulare di Analysis Services locale da [Power BI](https://powerbi.microsoft.com/). Power BI è una suite di strumenti di analisi business per analizzare e condividere dati. 

### <a name="excel"></a>Excel  
 È possibile connettersi ai database modello tabulare da Excel, utilizzando la visualizzazione dati e le funzionalità dell'analisi di Excel per l'elaborazione dei dati. Per accedere ai dati, è necessario definire una connessione dati di Analysis Services, specificare un server eseguito in modalità server tabulare, quindi scegliere il database che si desidera utilizzare. Per ulteriori informazioni, vedere [Creare una connessione o importare dati da SQL Server Analysis Services](http://go.microsoft.com/fwlink/?linkID=215150).  
  
 Excel è inoltre l'applicazione consigliata per l'esplorazione di modelli tabulari in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Nello strumento è disponibile un'opzione **Analizza in Excel** che consente di avviare una nuova istanza di Excel, creare una cartella di lavoro di Excel e aprire una connessione dati dalla cartella di lavoro al database dell'area di lavoro modello. In caso di esplorazione di dati del modello tabulare in Excel, tenere presente che in Excel vengono generate query sul modello utilizzando il client Tabella pivot di Excel. Di conseguenza, le operazioni all'interno della cartella di lavoro di Excel comportano l'invio al database dell'area di lavoro di query MDX, non di query DAX. Se si utilizza SQL Profiler o un altro strumento di monitoraggio per il monitoraggio di query, è possibile che nella traccia del profiler venga visualizzato MDX e non DAX. Per altre informazioni sulla funzionalità Analizza in Excel, vedere [Analizzare in Excel &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
### <a name="power-view"></a>Power View  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] è un'applicazione client di creazione di report di Reporting Services eseguita in un ambiente di SharePoint 2010, che combina esplorazione dei dati, progettazione di query e layout delle presentazioni in un'esperienza di reporting ad hoc integrata. [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] è possibile utilizzare modelli tabulari come origini dati, indipendentemente dal fatto che il modello sia ospitato in un'istanza di Analysis Services in esecuzione in modalità tabulare o recuperato da un archivio dati relazionale mediante la modalità DirectQuery. Per connettersi a un modello tabulare in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], è necessario creare un file di connessione contenente il percorso del server e il nome del database. È possibile creare un'origine dati condivisa di Reporting Services o un file di connessione BI Semantic Model in SharePoint. Per altre informazioni sulle connessioni BI Semantic Model, vedere [Connessione BI Semantic Model &#40;con estensione bism&#41; di PowerPivot](../../analysis-services/power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md).  
  
 Il client [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] determina la struttura del modello specificato inviando una richiesta all'origine dati specificata che restituisce uno schema utilizzabile dal client per creare query sul modello come origine dati ed eseguire operazioni basate sui dati. Le operazioni successive nell'interfaccia utente di [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] per filtrare dati, eseguire calcoli o aggregazioni e visualizzare i dati associati sono controllate dal client e non possono essere modificate a livello di codice.  
  
 Le query inviate dal client [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] al modello sono pubblicate come istruzioni DAX che è possibile monitorare impostando una traccia sul modello.  Il client pubblica inoltre una richiesta al server per la definizione dello schema iniziale, presentata in base al linguaggio Conceptual Schema Definition Language (CSDL). Per altre informazioni, vedere [Annotazioni CSDL per Business Intelligence &#40;CSDLBI&#41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 È possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per gestire le istanze che ospitano modelli tabulari ed eseguire query sui metadati e i dati che contengono. È possibile elaborare i modelli o gli oggetti in un modello, creare e gestire partizioni e impostare la sicurezza che può essere utilizzata per la gestione dell'accesso ai dati. Per altre informazioni, vedere gli argomenti seguenti:  
  
-   [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
-   [Connetti ad Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
-   [Monitorare un'istanza di Analysis Services](../../analysis-services/instances/monitor-an-analysis-services-instance.md)  
  
 È possibile utilizzare sia le finestre di query MDX e XMLA in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per recuperare dati e metadati da un database modello tabulare. Si tengano tuttavia in considerazione le restrizioni seguenti:  
  
-   Le istruzioni che utilizzano MDX e DMX non sono supportate per i modelli distribuiti in modalità DirectQuery; pertanto, per creare una query su un modello tabulare in modalità DirectQuery, è necessario utilizzare invece una finestra **Query XMLA** .  
  
-   Non è possibile modificare il contesto del database della finestra Query XMLA dopo avere aperto la finestra **Query** . Pertanto, se è necessario inviare una query a un database diverso o a un'istanza diversa, aprire tale database o istanza utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e aprire una nuova finestra **Query XMLA** all'interno di tale contesto.  
  
 È possibile creare tracce su un modello tabulare di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo analogo a quello utilizzato per una soluzione multidimensionale. In questa versione, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fornisce molti nuovi eventi che è possibile utilizzare per tenere traccia dell'utilizzo della memoria, delle operazioni di query ed elaborazione e dell'utilizzo dei file. Per altre informazioni, vedere [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md).  
  
> [!WARNING]  
>  Se si inserisce una traccia su un database modello tabulare, è possibile vedere alcuni eventi suddivisi in categorie come query DMX. Tuttavia, il data mining non è supportato sui dati di modelli tabulari e le query DMX eseguite sul database sono limitate alle istruzioni SELECT sui metadati del modello. Gli eventi sono suddivisi in categorie come DMX solo perché lo stesso framework del parser viene utilizzato per MDX.  
  
## <a name="query-languages"></a>Linguaggi di query  
 I modelli tabulari di Analysis Services supportano la maggior parte dei linguaggi di query forniti per l'accesso ai modelli multidimensionali. Fanno eccezione i modelli tabulari distribuiti in modalità DirectQuery che non recuperano dati da un archivio dati di Analysis Services ma direttamente da un'origine dati SQL Server. Non è possibile eseguire una query su tali modelli usando MDX, ma è necessario usare un client che supporti la conversione delle espressioni DAX in istruzioni Transact-SQL, ad esempio il client [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] .  
  
### <a name="dax"></a>DAX  
 È possibile usare DAX per creare espressioni e formule in tutti i tipi di modelli tabulari, indipendentemente dal fatto che il modello venga archiviato in SharePoint come cartella di lavoro di Excel abilitata per [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]o in un'istanza di Analysis Services.  
  
 Inoltre, è possibile utilizzare le espressioni DAX all'interno del contesto di un'istruzione di comando XMLA EXECUTE per inviare query a un modello tabulare distribuito in modalità DirectQuery.  
  
 Per esempi di esecuzione di query su un modello tabulare usando DAX, vedere [Riferimento alla sintassi di query DAX](http://msdn.microsoft.com/en-us/4dd0cf0e-191d-411d-987c-f606813fc39e).  
  
### <a name="mdx"></a>MDX  
 È possibile utilizzare MDX per creare query su modelli tabulari in cui si utilizza la cache in memoria come metodo di query preferito (vale a dire modelli che non sono stati distribuiti in modalità DirectQuery). Anche se i client quali [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] usano DAX sia per la creazione di aggregazioni sia per l'esecuzione di query sul modello come origine dati, se si ha familiarità con MDX può essere più rapido creare query di esempio in MDX, vedere [Compilazione di misure in MDX](../../analysis-services/multidimensional-models/mdx/mdx-building-measures.md).  
  
### <a name="csdl"></a>CSDL  
 Conceptual Schema Definition Language non è un linguaggio di query, di per sé, ma può essere utilizzato per recuperare informazioni relative al modello e ai metadati del modello, che potranno successivamente essere utilizzate per creare report o query sul modello.  
  
 Per informazioni sull'utilizzo di CSDL nei modelli tabulari, vedere [Annotazioni CSDL per Business Intelligence &#40;CSDLBI&#41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md).  
  
## <a name="programmatic-interfaces"></a>Interfacce programmatiche  
 Le interfacce principali utilizzate per l'interazione con i modelli tabulari di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sono i set di righe dello schema, XMLA e i client e gli strumenti per le query forniti da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
### <a name="data-and-metadata"></a>Dati e metadati  
 È possibile recuperare dati e metadati dai modelli tabulari in applicazioni gestite utilizzando ADOMD.NET. 
  
-   [Utilizzare DMV per monitorare Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
 Per supportare l'accesso OLE DB ai modelli tabulari, è possibile utilizzare il provider OLE DB per Analysis Services 9.0 in applicazioni client non gestite. Per abilitare l'accesso ai modelli tabulari, è necessaria una versione aggiornata del provider OLE DB di Analysis Services. Per altre informazioni sui provider usati con i modelli tabulari, vedere [Installazione del provider OLE DB di Analysis Services nei server di SharePoint](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859) .  
  
 È inoltre possibile recuperare i dati direttamente da un'istanza di Analysis Services in un formato basato su XML. È possibile recuperare lo schema del modello tabulare tramite il set di righe DISCOVER_CSDL_METADATA o utilizzare un comando EXECUTE o DISCOVER con elementi, oggetti o proprietà ASSL esistenti. Per altre informazioni, vedere le risorse seguenti:  
  
-   [Annotazioni CSDL per Business Intelligence &#40;CSDLBI&#41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
### <a name="manipulate-analysis-services-objects"></a>Gestire oggetti di Analysis Services  
 È possibile creare, modificare, eliminare ed elaborare i modelli tabulari e gli oggetti che contengono, tra cui tabelle, colonne, prospettive, misure e partizioni, utilizzando comandi XMLA o AMO. Sia AMO sia XMLA sono stati aggiornati per supportare proprietà aggiuntive utilizzate nei modelli tabulari per attività di reporting e modellazione avanzate.  
  
  
### <a name="schema-rowsets"></a>Set di righe dello schema  
 Le applicazioni client possono utilizzare i set di righe dello schema per esaminare i metadati di modelli tabulari e recuperare informazioni relative al supporto e al monitoraggio dal server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . In questa versione di SQL Server sono stati aggiunti nuovi set di righe dello schema e i set di righe dello schema esistenti sono stati estesi per supportare funzionalità correlate ai modelli tabulari e migliorare le operazioni di monitoraggio e analisi delle prestazioni in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   [Set di righe DISCOVER_CALC_DEPENDENCY](../../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md)  
  
     Nuovo set di righe dello schema per il rilevamento delle dipendenze tra le colonne e i riferimenti in un modello tabulare  
  
-   [Set di righe DISCOVER_CSDL_METADATA](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)  
  
     Nuovo set di righe dello schema per l'acquisizione della rappresentazione CSDL di un modello tabulare  
  
-   [Set di righe DISCOVER_XEVENT_TRACE_DEFINITION](http://msdn.microsoft.com/library/e1ce2d2d-f994-4318-801a-ee0385aecd84)  
  
     Nuovo set di righe dello schema per il monitoraggio di Eventi estesi di SQL Server. Per altre informazioni, vedere [Monitor Analysis Services with SQL Server Extended Events](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)(Utilizzo di eventi estesi di SQL Server per il monitoraggio di Analysis Services).  
  
-   [Set di righe DISCOVER_TRACES](../../analysis-services/schema-rowsets/xml/discover-traces-rowset.md)  
  
     La nuova colonna **Type** consente di filtrare le tracce in base alla categoria. Per altre informazioni, vedere [Creare tracce del profiler per la riproduzione &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md).  
  
-   [Set di righe MDSCHEMA_HIERARCHIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)  
  
     La nuova enumerazione **STRUCTURE_TYPE** supporta l'identificazione di gerarchie definite dall'utente create in modelli tabulari. Per altre informazioni, vedere [Gerarchie &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
 I set di righe dello schema OLE DB per data mining non sono stati aggiornati in questa versione.  
  
> [!WARNING]  
>  Non è possibile utilizzare query MDX o DMX in un database distribuito in modalità DirectQuery; pertanto per eseguire una query su un modello DirectQuery utilizzando i set di righe dello schema, è necessario utilizzare XMLA, non il DMV associato. Per i DMV che restituiscono risultati per il server nel suo complesso, ad esempio SELECT * da $system.DBSCHEMA_CATALOGS o DISCOVER_TRACES, è possibile eseguire la query nel contenuto di un database distribuito in una modalità memorizzata nella cache.  
  
## <a name="see-also"></a>Vedere anche  
 [Connettersi a un database modello tabulare &#40;SSAS&#41;](../../analysis-services/tabular-models/connect-to-a-tabular-model-database-ssas.md)   
 [Accesso ai dati PowerPivot](../../analysis-services/power-pivot-sharepoint/power-pivot-data-access.md)   
 [Connetti ad Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  

