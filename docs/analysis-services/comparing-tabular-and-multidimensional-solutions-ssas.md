---
title: "Confronto tra soluzioni tabulari e multidimensionali (SSAS) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 76ee5e96-6a04-49af-a88e-cb5fe29f2e9a
caps.latest.revision: 49
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 47
---
# Confronto tra soluzioni tabulari e multidimensionali (SSAS)
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fornisce diversi approcci per la creazione di Business Intelligence Semantic Model: multidimensionale, tabulare e PowerPivot.  
  
 La disponibilità di più approcci consente esperienze di modellazione commisurate ai diversi requisiti di aziende e utenti. L'approccio multidimensionale è una tecnologia avanzata basata su standard aperti, adottato da numerosi fornitori di software di Business Intelligence, ma può essere difficile da gestire. L'approccio tabulare offre una modellazione relazionale che molti sviluppatori trovano più intuitiva. PowerPivot è ancora più semplice, poiché offre una modellazione dei dati visiva in Excel, con supporto server tramite SharePoint.  
  
 Tutti i modelli vengono distribuiti come database eseguiti in un'istanza di Analysis Services, a cui è possibile accedere con gli strumenti client usando un singolo set di provider di dati e possono essere visualizzati in report interattivi e statici tramite Excel, Reporting Services, Power BI e strumenti di Business Intelligence di altri fornitori.  
  
 A causa delle differenze nell'architettura di memoria e nei metadati, nessuno dei tipi di modello è intercambiabile, anche se è possibile aggiornare in modo semplice un modello tabulare 1050-1103 a un modello tabulare 1200 e importare PowerPivot per creare un modello completamente nuovo come progetto tabulare.  
  
 Le soluzioni tabulare e multidimensionale vengono compilate mediante [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] e devono essere usate per progetti di Business Intelligence aziendali che vengono eseguiti in un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] autonoma. Entrambe le soluzioni garantiscono database analitici a prestazioni elevate che si integrano facilmente con i client di Business Intelligence. Ogni soluzione tuttavia viene creata, utilizzata e distribuita in modo diverso. In questo argomento si mettono a confronto questi due tipi di modellazioni in modo da identificare l'approccio giusto per l'utente.  
  
 Per i nuovi progetti di sviluppo, è consigliabile in genere usare la modellazione tabulare, con cui sarà possibile progettare, testare e distribuire più velocemente. Consente prestazioni migliori con le applicazioni di Business Intelligence e con i servizi cloud dotati delle più recenti modalità self-service di Microsoft.  
  
##  <a name="a-namebkmkoverviewa-overview-of-modeling-types"></a><a name="bkmk_overview"></a> Panoramica dei tipi di modellazione  
 Se non si ha familiarità con Analysis Services La tabella seguente elenca i diversi modelli, riepiloga l'approccio e identifica il veicolo della versione iniziale.  
  
||||  
|-|-|-|  
|**Tipo**|**Descrizione della modellazione**|**Versione**|  
|Multidimensionale|Costrutti di modellazione OLAP (cubi, dimensioni, misure).|SQL Server 2000 e versioni successive|  
|Tabella|Costrutti di modellazione relazionale (modello, tabelle, colonne).<br /><br /> Internamente, i metadati vengono ereditati dai costrutti di modellazione OLAP (cubi, dimensioni, misure). Codice e script usano i metadati OLAP.|SQL Server 2012 e versione successiva (livelli di compatibilità 1050 - 1103) <sup>1</sup>|  
|Tabulare in SQL Server 2016|Costrutti di modellazione relazionale (modello, tabelle, colonne), articolati in definizioni di oggetti di metadati tabulari in script e codice.|SQL Server 2016 (livello di compatibilità: 1200)|  
|Power Pivot|Inizialmente componente aggiuntivo, ma ora completamente integrato in Excel. Solo modellazione visiva attraverso un'infrastruttura tabulare interna. È possibile importare un modello PowerPivot in SSDT per creare un nuovo modello tabulare eseguibile su un'istanza di Analysis Services.|tramite Excel e PowerPivot BI Desktop|  
  
 <sup>1</sup> I livelli di compatibilità, introdotti in SQL Server 2012, sono importanti nella versione corrente grazie al nuovo motore di metadati tabulari e al supporto di funzioni per l'abilitazione dello scenario, disponibili solo a livello superiore. I miglioramenti principali includono DirectQuery, gli script e la programmabilità. Per informazioni dettagliate, vedere [What's New in Analysis Services](../analysis-services/what-s-new-in-analysis-services.md) .  
  
##  <a name="a-namebkmkmodelsa-model-features"></a><a name="bkmk_models"></a> Funzionalità del modello  
  Nella tabella seguente viene riepilogata la disponibilità delle funzionalità al livello del modello. Consultare questo elenco per assicurarsi che la funzionalità che si desidera usare sia disponibile per il tipo di modello da compilare.  
  
|||||  
|-|-|-|-|  
||Multidimensionale|Tabella|Power Pivot|  
|Azioni|Sì|No|No|  
|Aggregations|Sì|No|No|  
|Colonna calcolata|No|Sì|Sì|  
|Misure calcolate|Sì|Sì|Sì|  
|Tabelle calcolate|No|Sì <sup>1</sup>|No|  
|Assembly personalizzati|Sì|No|No|  
|Rollup personalizzati|Sì|No|No|  
|Membro predefinito|Sì|No|No|  
|Cartelle di visualizzazione|Sì|Sì <sup>1</sup>|No|  
|Distinct Count|Sì|Sì (tramite DAX)|Sì (tramite DAX)|  
|Drill-through|Sì|Sì (dettagli visualizzati in un foglio di lavoro separato)|Sì|  
|Gerarchie|Sì|Sì|Sì|  
|KPI|Sì|Sì|Sì|  
|Oggetti collegati|Sì|Sì (tabelle collegate)|No|  
|Relazioni molti-a-molti|Sì|No (ma è presente [bidirezionalità tra i filtri](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md) a livello di compatibilità pari a 1200)|No|  
|Set denominati|Sì|No|No|  
|Gerarchie padre-figlio|Sì|Sì (tramite DAX)|Sì (tramite DAX)|  
|Partizioni|Sì|Sì|Sì|  
|Prospettive|Sì|Sì|Sì|  
|Misure semiadditive|Sì|Sì|Sì|  
|Traduzioni|[Sì](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|Sì|[Sì](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)|  
|Gerarchie definite dall'utente|Sì|Sì|Sì|  
|Writeback|Sì|No|No|  
  
 <sup>1</sup> Per informazioni sulle differenze funzionali all'interno del gruppo tabulare, vedere [Livello di compatibilità per i modelli tabulari in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
##  <a name="a-namebkmkdsa-data-considerations"></a><a name="bkmk_ds"></a> Considerazioni sui dati  
 I modelli tabulari e multidimensionali usano dati importati da origini esterne. La quantità e il tipo di dati da importare sono fattori di primaria importanza per decidere quale tipo di modello è più adatto ai dati in uso.  
  
 **Compressione**  
  
 Sia nelle soluzioni tabulari sia in quelle multidimensionali viene usata la compressione dati che consente di ridurre le dimensioni del database di Analysis Services correlate al data warehouse da cui si importano i dati. Poiché la compressione effettiva varierà in base alle caratteristiche dei dati sottostanti, non vi è alcun modo per sapere con precisione la quantità di spazio su disco e di memoria che sarà richiesta da una soluzione una volta che i dati vengono elaborati e utilizzati nelle query.  
  
 Molti sviluppatori di Analysis Services stimano che le dimensioni dell'archiviazione primaria di un database multidimensionale saranno pari a circa un terzo rispetto a quelle dei dati iniziali. I database tabulari possono talvolta richiedere quantità di compressione maggiori, circa un decimo delle dimensioni, specialmente se la maggior parte dei dati viene importata dalle tabelle dei fatti.  
  
 **Dimensione del modello e distorsione delle risorse (in memoria o disco)**  
  
 La dimensione di un database di Analysis Services è limitata solo dalle risorse disponibili per l'esecuzione. Il tipo di modello e la modalità di archiviazione giocano un ruolo anche nel potenziale di crescita del database.  
  
 I database tabulari vengono eseguiti sia in modalità in memoria che tramite DirectQuery, che trasferisce l'esecuzione delle query a un database esterno. Per l'analisi in memoria tabulare, il database viene archiviato completamente nella memoria, pertanto è necessario disporre di memoria sufficiente non solo per caricare tutti i dati, ma anche per le strutture di dati aggiuntive create a supporto delle query.  
  
 DirectQuery, rinnovato in questa versione, vanta un numero minore di restrizioni e prestazioni migliori rispetto alla versione precedente. L'uso del database relazionale di back-end per l'archiviazione e l'esecuzione di query semplifica la compilazione di un modello tabulare su larga scala rispetto alle possibilità offerte dalla versione precedente.  
  
 Storicamente, i più grandi database [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in produzione sono multidimensionali, con l'elaborazione e i carichi di lavoro delle query in esecuzione in modo indipendente su hardware dedicato, ognuno ottimizzato per il rispettivo uso.  I database tabulari stanno recuperando rapidamente e i nuovi miglioramenti di DirectQuery aiutano ancor di più a colmare il divario.  
  
 Per la ripartizione del carico di lavoro nei modelli multidimensionali, l'archiviazione dati e l'esecuzione delle query è disponibile tramite ROLAP.   In un server di query, i set di righe possono essere memorizzati nella cache e quelli obsoleti vengono scartati. Un uso efficiente ed equilibrato delle risorse di memoria e disco spesso conduce i clienti verso soluzioni multidimensionali.  
  
 In fase di caricamento, è possibile prevedere un aumento sia per i requisiti del disco sia per quelli della memoria di entrambi i tipi di soluzione quando tramite Analysis Services vengono memorizzati nella cache, archiviati, analizzati e sottoposti a query i dati. Per altre informazioni sulle opzioni di paging della memoria, vedere [Memory Properties](../analysis-services/server-properties/memory-properties.md). Per altre informazioni sulla scalabilità, vedere [High availability and Scalability in Analysis Services](../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md).  
  
 PowerPivot per Excel dispone di un limite di dimensioni di file artificiale di 2 gigabyte, che viene imposto in modo che le cartelle di lavoro create in PowerPivot per Excel possano essere caricate in SharePoint, in cui vengono impostati i limiti massimi sulle dimensioni di caricamento del file. Uno dei motivi principali per l'esecuzione della migrazione di una cartella di lavoro di PowerPivot a una soluzione tabulare in un'istanza di Analysis Services autonoma è risolvere la limitazione delle dimensioni del file. Per altre informazioni sulla configurazione delle dimensioni massime di caricamento dei file, vedere [Configurare le dimensioni massime di caricamento dei file &#40;Power Pivot per SharePoint&#41;](../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).  
  
 **Origini dati supportate**  
  
 Con le soluzioni multidimensionali è possibile importare i dati da origini dati relazionali usando provider gestiti e nativi OLE DB.  
  
 I modelli tabulari possono importare dati da origini dati relazionali, feed di dati e alcuni formati del documento. È anche possibile usare OLE DB per i provider ODBC con modelli tabulari.  
  
 Per visualizzare l'elenco delle origini dati esterne che è possibile importare in ogni modello, vedere gli argomenti riportati di seguito.  
  
-   [Origini dati supportate &#40;SSAS - multidimensionale&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
-   [Origini dati supportate &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
##  <a name="a-namebkmklanga-query-and-scripting-language-support"></a><a name="bkmk_lang"></a> Supporto dei linguaggi di query e di scripting  
 Analysis Services include MDX, DMX, DAX, XML/A, ASSL e TMSL. Il supporto di tali linguaggi potrebbe variare in base al tipo di modello. Se i requisiti di linguaggi di query e di scripting sono una considerazione importante, esaminare l'elenco seguente.  
  
-   Le cartelle di lavoro di PowerPivot usano DAX per i calcoli e DAX o MDX per le query.  
  
-   I database modello tabulare supportano calcoli DAX, query DAX e query MDX. Questo vale per tutti i livelli di compatibilità. I linguaggi di script sono ASSL (tramite XMLA) per i livelli di compatibilità 1103-1050 e TMSL (tramite XMLA) per il livello di compatibilità 1200.  
  
-   I database modello multidimensionale supportano calcoli MDX e query MDX, nonché ASSL.  
  
-   I modelli di data mining supportano DMX e ASSL.  
  
-   PowerShell per Analysis Services è supportato per modelli e database tabulari e multidimensionali.  
  
 Tutti i database supportano XML/A. Vedere [Riferimento al linguaggio di query ed espressioni &#40;Analysis Services&#41;](../Topic/Query%20and%20Expression%20Language%20Reference%20\(Analysis%20Services\).md) e [Guida per gli sviluppatori (Analysis Services)](../analysis-services/analysis-services-developer-documentation.md).  
  
##  <a name="a-namebkmkseca-security-features"></a><a name="bkmk_sec"></a> Funzionalità di sicurezza  
 Tutte le soluzioni di Analysis Services possono essere protette a livello di database. Opzioni di sicurezza più granulari variano in base alla modalità. Se le impostazioni di sicurezza granulari sono un requisito per la soluzione, esaminare l'elenco seguente per verificare che il livello di sicurezza desiderato sia supportato nel tipo di soluzione da compilare:  
  
-   Le cartelle di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] sono protette a livello di file, mediante le autorizzazioni di SharePoint.  
  
-   I database modello tabulare possono utilizzare la sicurezza a livello di riga, mediante le autorizzazioni basate sul ruolo in Analysis Services.  
  
-   I database modello multidimensionale possono utilizzare la sicurezza a livello di cella e di dimensione, mediante le autorizzazioni basate sui ruoli in Analysis Services.  
  
 Le cartelle di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] possono essere ripristinate in un server in modalità tabulare. Dopo il ripristino, il file viene separato da SharePoint consentendo di usare tutte le funzionalità della modellazione tabulare, inclusa la sicurezza a livello di riga.  
  
##  <a name="a-namebkmkdesignera-design-tools"></a><a name="bkmk_designer"></a> Strumenti di progettazione  
 Le competenze di modellazione dei dati e l'esperienza tecnica possono variare molto tra gli utenti che si occupano della compilazione di modelli analitici. Se in una soluzione la familiarità di uno strumento o l'esperienza degli utenti è una considerazione importante, confrontare le esperienze seguenti per la creazione del modello.  
  
|Strumento di modellazione|Modalità di utilizzo|  
|-------------------|--------------|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|Utilizzare per creare soluzioni tabulari, multidimensionali e di data mining. In questo ambiente di creazione viene utilizzata la shell di Visual Studio per fornire aree di lavoro, riquadri delle proprietà e navigazione degli oggetti. Gli utenti tecnici che già utilizzano Visual Studio preferiranno probabilmente questo strumento per la compilazione di applicazioni di Business Intelligence.|  
|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per Excel|Usare per creare una cartella di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] da distribuire successivamente in una farm SharePoint in cui sia presente un'installazione di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per SharePoint. [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per Excel presenta un'area di lavoro dell'applicazione separata visualizzata sopra Excel. Vengono utilizzate le stesse metafore visive (pagine a schede, layout griglia e barra della formula) di Excel. Gli utenti con esperienza nell'utilizzo di Excel preferiranno questo strumento rispetto a [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].|  
  
##  <a name="a-namebkmkclienta-client-application-support"></a><a name="bkmk_client"></a> Supporto delle applicazioni client  
 Se si utilizza Reporting Services, la disponibilità delle funzionalità di report varia tra le edizioni e le modalità server. Per questo motivo, il tipo di report che si desidera compilare potrebbe influire sulla modalità server che si sceglie di installare.  
  
 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], uno strumento di creazione di Reporting Services in esecuzione in SharePoint, è disponibile in un server di report distribuito in una farm di SharePoint 2010. L'unico tipo di origine dati che può essere usato con questo report è un database modello tabulare di Analysis Services o una cartella di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] . Ciò significa che è necessario disporre di un server in modalità tabulare o di un server [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per SharePoint per ospitare l'origine dati usata da questo tipo di report. Non è possibile utilizzare un modello multidimensionale come origine dati per un report [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] . È necessario creare una connessione BISM [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] o un'origine dati condivisa di Reporting Services da usare come origine dati per un report [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] .  
  
 In Generatore report e Progettazione report è possibile usare qualsiasi database di Analysis Services, incluse le cartelle di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ospitate in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per SharePoint.  
  
 I report Tabella pivot di Excel sono supportati da tutti i database di Analysis Services. Le funzionalità di Excel non cambiano se si usa un database tabulare, un database multidimensionale o una cartella di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] , anche se la funzionalità writeback è supportata solo per i database multidimensionali.  
  
 Dai dashboard di PerformancePoint è possibile connettersi a tutti i database di Analysis Services, incluse le cartelle di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] . Per ulteriori informazioni, vedere la pagina relativa alla [creazione di connessioni dati (PerformancePoint Services)](http://go.microsoft.com/fwlink/?linkdID=218155).  
  
##  <a name="a-namebkmkdeploymentmodea-server-deployment-modes-for-multidimensional-and-tabular-solutions"></a><a name="bkmk_deploymentmode"></a> Modalità di distribuzione di server per soluzioni multidimensionali e tabulari  
 Un'istanza di Analysis Services viene installata in una delle tre modalità che impostano il contesto operativo del server. La modalità server installata determinerà il tipo di soluzioni che è possibile distribuire in tale server. Archiviazione e architettura della memoria sono le differenze principali tra le modalità, ma ne esistono altre. Le tre modalità server disponibili sono descritte brevemente nella tabella riportata di seguito. Per altre informazioni, vedere [Determinare la modalità server di un'istanza di Analysis Services](../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md).  
  
|Modalità di distribuzione|Descrizione|  
|---------------------|-----------------|  
|0 - Multidimensionale e data mining|Vengono eseguite soluzioni multidimensionali e di data mining che vengono distribuite in un'istanza predefinita di Analysis Services. La modalità di distribuzione 0 è l'impostazione predefinita per un'installazione di Analysis Services.|  
|1 - [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per SharePoint|In caso di accesso ai dati [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] , Analysis Services è un componente interno di un'installazione di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per SharePoint. Analysis Services viene installato in modalità di distribuzione 1 e viene usato esclusivamente dai servizi [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] in un ambiente SharePoint.|  
|2 - Tabulare|Vengono eseguite soluzioni tabulari in un'istanza autonoma di Analysis Services configurata per la modalità di distribuzione 2.|  
  
 Per altre informazioni, vedere [Installare Analysis Services](../analysis-services/instances/install-windows/install-analysis-services.md).  
  
##  <a name="a-namebkmksharepointa-sharepoint-requirements"></a><a name="bkmk_sharePoint"></a> Requisiti di SharePoint  
 SQL Server si integra con SharePoint aggiungendo supporto per l'accesso ai dati [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] e a quelli tabulari. L'investimento in termini di integrazione di SharePoint e SQL Server cresce all'aumentare del numero di funzionalità utilizzate da ciascun prodotto. Se si dispone di SharePoint, è possibile installare SQL Server [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per SharePoint per abilitare l'accesso ai dati [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] e ottenere i file di connessione con estensione bism di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] usati per accedere a database tabulari in esecuzione in un'istanza di Analysis Services esterna su un server di rete.  
  
 La creazione di report Power View, in cui si usano database [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] e tabulari come origine dati, è sia una funzionalità di SharePoint fornita da SQL Server che una funzionalità integrata in Excel. Anche se i database tabulari vengono eseguiti in un'istanza di Analysis Services al di fuori di SharePoint, i dati in questione vengono utilizzati dai report Power View che vengono eseguiti in SharePoint.  
  
 Se non si usa SharePoint, è comunque possibile usare [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per Excel per creare cartelle di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ; tuttavia, non si disporrà di una visualizzazione dei dati coesiva. Ogni utente che usa la cartella di lavoro deve scaricare e visualizzare ciascuna cartella di lavoro in Excel mediante il componente aggiuntivo [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per Excel per ottenere l'esplorazione e l'interazione dei dati tramite filtri dei dati, filtri e pivot. In caso contrario, la visualizzazione della cartella di lavoro sarà limitata ai dati statici come vengono visualizzati al momento dell'apertura della cartella di lavoro.  
  
 Le soluzioni tabulari, multidimensionali e di data mining vengono eseguite in istanze di Analysis Services su una rete, senza la dipendenza da SharePoint.  
  
##  <a name="a-namebkmkexta-programmability-and-extensibility-support"></a><a name="bkmk_ext"></a> Supporto di programmabilità ed estendibilità  
 Anche se è disponibile il supporto per gli sviluppatori per Power BI, non è disponibile supporto per le cartelle di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] . Se si usano cartelle di lavoro di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], è necessario usare le applicazioni client e server predefinite come parte della soluzione. La programmazione Excel e quella SharePoint sono le uniche opzioni.  
  
 Per Power BI, vedere [Power BI Embedded (Power BI incorporato)](https://azure.microsoft.com/services/power-bi-embedded/).  
  
 Le soluzioni tabulari supportano solo un file model.bim per soluzione, pertanto tutto il lavoro deve essere eseguito in un singolo file. I team di sviluppo abituati all'utilizzo di più progetti in una sola soluzione potrebbero dover rivedere la modalità con cui operano quando si compila una soluzione tabulare condivisa.  
  
 Le soluzioni tabulari con livello di compatibilità 1200 eseguono il mapping di un nuovo modello di oggetto che usa metadati tabulari. I modelli tabulari e tutti i modelli multidimensionali precedenti usano i metadati multidimensionali come descrittori. È consigliabile aggiornare i modelli tabulari precedenti al livello di compatibilità 1200 per poter usare gli spazi dei nomi in formato tabulare in AMO per script e codice personalizzati.  
  
 Per altre informazioni, vedere [Analysis Services Developer Documentation (Documentazione per gli sviluppatori di Analysis Services)](https://msdn.microsoft.com/library/bb500153.aspx) .  
  
##  <a name="a-namebkmknexta-next-step-build-a-solution"></a><a name="bkmk_Next"></a> Passaggio successivo: compilare una soluzione  
 Dopo aver compreso come confrontare le soluzioni, provare le esercitazioni seguenti per apprendere i passaggi relativi alla creazione di ciascuna soluzione. Nei collegamenti seguenti sono disponibili le esercitazioni in cui vengono illustrati i passaggi.  
  
-   Compilare un modello di [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]. Vedere [Get started with Power Pivot in Microsoft Excel (Introduzione a Power Pivot in Microsoft Excel)](https://support.office.com/article/Get-started-with-Power-Pivot-in-Microsoft-Excel-fdfcf944-7876-424a-8437-1a6c1043a80b).  
  
-   Compilare un modello tabulare. Vedere [Modellazione tabulare &#40;esercitazione di AdventureWorks&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md).  
  
-   Compilare un modello multidimensionale. Vedere [Modellazione multidimensionale &#40;esercitazione di AdventureWorks&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md).  
  
-   Compilare un modello di data mining. Vedere [Esercitazione di base sul data mining](../Topic/Basic%20Data%20Mining%20Tutorial.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di un'istanza di Analysis Services](../analysis-services/instances/analysis-services-instance-management.md)   
 [Novità di Analysis Services](../analysis-services/what-s-new-in-analysis-services.md)     
 [Novità di PowerPivot](http://go.microsoft.com/fwlink/?LinkId=238141)   
 [Connessione BI Semantic Model di PowerPivot &#40;.bism&#41;](../analysis-services/power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)   
 [Creare e gestire origini dati condivise &#40;Reporting Services in modalità integrata SharePoint&#41;](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)  
  
  