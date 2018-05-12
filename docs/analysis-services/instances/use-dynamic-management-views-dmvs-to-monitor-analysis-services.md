---
title: Utilizzare viste a gestione dinamica (DMV) per monitorare Analysis Services | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 412923d24b4d48a0ebdfa11bcf60dc19d5b85368
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="use-dynamic-management-views-dmvs-to-monitor-analysis-services"></a>Utilizzare DMV per monitorare Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Le DMV (viste a gestione dinamica) di Analysis Services sono strutture di query che consentono di esporre informazioni sulle operazioni del server locali e sull'integrità del server. La struttura di query è un'interfaccia dei set di righe dello schema tramite cui vengono restituiti i metadati e le informazioni di monitoraggio per un'istanza di Analysis Services.  
  
 Per la maggior parte delle query DMV, vengono usati un'istruzione **SELECT** e lo schema **$System** con un set di righe dello schema XML/A.set.  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 Le query DMV restituiscono informazioni sullo stato del server corrente al momento dell'esecuzione della query. Per monitorare le operazioni in tempo reale, utilizzare invece la traccia. Per altre informazioni, vedere [Utilizzare SQL Server Profiler per il monitoraggio di Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
##  <a name="bkmk_ben"></a> Vantaggi delle query utilizzando DMV  
 Le query DMV restituiscono informazioni sulle operazioni e sull'utilizzo delle risorse, che non sono disponibili in altro modo.  
  
 Le query DMV rappresentano un'alternativa all'esecuzione di comandi di individuazione XML/A. Per la maggior parte degli amministratori, la scrittura di una query DMV risulta più semplice in quanto la sintassi di query è basata su SQL. Il set di risultati viene inoltre restituito in un formato tabulare, che offre maggiore semplicità per le operazioni di lettura e copia.  
  
##  <a name="bkmk_ex"></a> Esempi e scenari  
 Una query DMV può essere utile per rispondere a domande sulle connessioni e sulle sessioni attive, nonché per verificare quali oggetti stanno utilizzando la maggior parte di memoria o CPU in un momento specifico. In questa sezione vengono forniti esempi per scenari in cui le query DMV sono più comunemente utilizzate. È possibile vedere anche la [Guida operativa di SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409) per informazioni aggiuntive sull'uso di query DMV per monitorare un'istanza del server.  
  
 `Select * from $System.discover_object_activity` /** Questa query fornisce informazioni sull'attività dell'oggetto dal momento dell'ultimo avvio del servizio. Per query di esempio basate su questa DMV, vedere [Nuova DMV System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322).  
  
 `Select * from $System.discover_object_memory_usage` /** Questa query fornisce informazioni sull'utilizzo di memoria per oggetto.  
  
 `Select * from $System.discover_sessions` /** Questa query fornisce informazioni sulle sessioni attive, incluse informazioni su durata e utente della sessione.  
  
 `Select * from $System.discover_locks` /** Questa query restituisce uno snapshot dei blocchi usati in un momento specifico.  
  
##  <a name="bkmk_syn"></a> Sintassi di query  
 Il motore di query per le DMV è il parser di data mining. La sintassi di query DMV è basata sull'istruzione [SELECT &#40;DMX&#41;](../../dmx/select-dmx.md).  
  
 Sebbene la sintassi di query DMV sia basata su un'istruzione SQL SELECT, non è supportata la sintassi completa di un'istruzione SELECT. In particolare, non sono supportate le clausole JOIN, GROUP BY, LIKE, CAST e CONVERT.  
  
```  
SELECT [DISTINCT] [TOP <n>] <select list>  
FROM $System.<schemaRowset>  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
 Nell'esempio seguente per DISCOVER_CALC_DEPENDENCY viene illustrato l'utilizzo della clausola WHERE per fornire un parametro alla query:  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
WHERE OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
 In alternativa, per i set di righe dello schema che prevedono restrizioni, la query deve includere la funzione SYSTEMRESTRICTSCHEMA. Nell'esempio seguente vengono restituiti i metadati CSDL relativi ai modelli tabulari in esecuzione in un server in modalità tabulare. Notare che CATALOG_NAME distingue tra maiuscole e minuscole:  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  
  
##  <a name="bkmk_tools"></a> Strumenti e le autorizzazioni  
 Per eseguire una query su una DMV, è necessario disporre delle autorizzazioni di amministratore di sistema nell'istanza di Analysis Services.  
  
 È possibile utilizzare qualsiasi applicazione client che supporta le query MDX o DMX, inclusi SQL Server Management Studio, un report di Reporting Services o un dashboard di PerformancePoint.  
  
 Per eseguire una query DMV da Management Studio, connettersi all'istanza su cui si vuole eseguire la query e fare clic su **Nuova query**. È possibile eseguire una query da una finestra Query DMX o MDX.  
  
##  <a name="bkmk_ref"></a> Riferimento DMV  
 Non tutti i set di righe dello schema dispongono di un'interfaccia DMV. Per restituire un elenco di tutti i set di righe dello schema su cui è possibile eseguire una query utilizzando DMV, eseguire la query seguente.  
  
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
> [!NOTE]  
>  Se una DMV non è disponibile per un determinato set di righe, il server restituirà l'errore seguente: "il \<schemarowset > tipo di richiesta non è stato riconosciuto dal server". Tutti gli altri errori indicano problemi con la sintassi.  
  
|Set di righe|Description|  
|------------|-----------------|  
|[Set di righe DBSCHEMA_CATALOGS](../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md)|Restituisce un elenco dei database di Analysis Services nella connessione corrente.|  
|[Set di righe DBSCHEMA_COLUMNS](../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md)|Restituisce un elenco di tutte le colonne nel database corrente. È possibile utilizzare questo elenco per creare una query DMV.|  
|[Set di righe DBSCHEMA_PROVIDER_TYPES](../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md)|Restituisce le proprietà relative ai tipi di dati di base supportati dal provider di dati OLE DB.|  
|[Set di righe DBSCHEMA_TABLES](../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md)|Restituisce un elenco di tutte le tabelle nel database corrente. È possibile utilizzare questo elenco per creare una query DMV.|  
|[Set di righe DISCOVER_CALC_DEPENDENCY](../../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md)|Restituisce un elenco delle colonne e delle tabelle utilizzate in un modello che presentano dipendenze da altre colonne e tabelle.|  
|[Set di righe DISCOVER_COMMAND_OBJECTS](../../analysis-services/schema-rowsets/xml/discover-command-objects-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative agli oggetti utilizzati dal comando a cui si fa riferimento.|  
|[Set di righe DISCOVER_COMMANDS](../../analysis-services/schema-rowsets/xml/discover-commands-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative al comando attualmente in esecuzione.|  
|[Set di righe DISCOVER_CONNECTIONS](../../analysis-services/schema-rowsets/xml/discover-connections-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle connessioni aperte ad Analysis Services.|  
|[Set di righe DISCOVER_CSDL_METADATA](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)|Restituisce informazioni su un modello tabulare.<br /><br /> Richiede l'aggiunta di SYSTEMRESTRICTSCHEMA e di parametri aggiuntivi.|  
|[Set di righe DISCOVER_DB_CONNECTIONS](../../analysis-services/schema-rowsets/xml/discover-db-connections-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle connessioni aperte da Analysis Services a origini dati esterne, ad esempio durante l'elaborazione o l'importazione.|  
|[Set di righe DISCOVER_DIMENSION_STAT](../../analysis-services/schema-rowsets/xml/discover-dimension-stat-rowset.md)|Restituisce gli attributi di una dimensione o le colonne di una tabella, a seconda del tipo di modello.|  
|[Set di righe DISCOVER_ENUMERATORS](../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)|Restituisce i metadati sugli enumeratori supportati per un'origine dati specifica.|  
|[Set di righe DISCOVER_INSTANCES](../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)|Restituisce informazioni sull'istanza specificata.<br /><br /> Richiede l'aggiunta di SYSTEMRESTRICTSCHEMA e di parametri aggiuntivi.|  
|[Set di righe DISCOVER_JOBS](../../analysis-services/schema-rowsets/xml/discover-jobs-rowset.md)|Restituisce informazioni sui processi correnti.|  
|[Set di righe DISCOVER_KEYWORDS & #40; XMLA & #41;](../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)|Restituisce l'elenco di parole chiave riservate.|  
|[Set di righe DISCOVER_LITERALS](../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)|Restituisce l'elenco di valori letterali, inclusi valori e tipi di dati, supportati da XMLA.|  
|[Set di righe DISCOVER_LOCKS](../../analysis-services/schema-rowsets/xml/discover-locks-rowset.md)|Restituisce uno snapshot dei blocchi utilizzati in un momento specifico.|  
|[Set di righe DISCOVER_MEMORYGRANT](../../analysis-services/schema-rowsets/xml/discover-memorygrant-rowset.md)|Restituisce informazioni sulla memoria allocata da Analysis Services all'avvio.|  
|[Set di righe DISCOVER_MEMORYUSAGE](../../analysis-services/schema-rowsets/xml/discover-memoryusage-rowset.md)|Mostra l'utilizzo della memoria per oggetti specifici.|  
|[Set di righe DISCOVER_OBJECT_ACTIVITY](../../analysis-services/schema-rowsets/xml/discover-object-activity-rowset.md)|Fornisce informazioni sull'attività dell'oggetto dal momento dell'ultimo avvio del servizio.|  
|[Set di righe DISCOVER_OBJECT_MEMORY_USAGE](../../analysis-services/schema-rowsets/xml/discover-object-memory-usage-rowset.md)|Fornisce informazioni sull'utilizzo di memoria per oggetto.|  
|[Set di righe DISCOVER_PARTITION_DIMENSION_STAT](../../analysis-services/schema-rowsets/xml/discover-partition-dimension-stat-rowset.md)|Fornisce informazioni sugli attributi di una dimensione.<br /><br /> Richiede l'aggiunta di SYSTEMRESTRICTSCHEMA e di parametri aggiuntivi.|  
|[Set di righe DISCOVER_PARTITION_STAT](../../analysis-services/schema-rowsets/xml/discover-partition-stat-rowset.md)|Fornisce informazioni sulle partizioni di una dimensione, una tabella o un gruppo di misure.<br /><br /> Richiede l'aggiunta di SYSTEMRESTRICTSCHEMA e di parametri aggiuntivi.|  
|[Set di righe DISCOVER_PERFORMANCE_COUNTERS](../../analysis-services/schema-rowsets/xml/discover-performance-counters-rowset.md)|Elenca le colonne utilizzate in un contatore delle prestazioni.<br /><br /> Richiede l'aggiunta di SYSTEMRESTRICTSCHEMA e di parametri aggiuntivi.|  
|[Set di righe DISCOVER_PROPERTIES](../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)|Restituisce informazioni sulle proprietà supportate da XMLA per l'origine dati specificata.|  
|[Set di righe DISCOVER_SCHEMA_ROWSETS](../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)|Restituisce nomi, restrizioni, descrizione e altre informazioni per tutti i valori di enumerazione supportati da XMLA.|  
|[Set di righe DISCOVER_SESSIONS](../../analysis-services/schema-rowsets/xml/discover-sessions-rowset.md)|Fornisce informazioni sulle sessioni attive, incluse informazioni su durata e utente della sessione.|  
|[Set di righe DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](../../analysis-services/schema-rowsets/xml/discover-storage-table-column-segments-rowset.md)|Fornisce informazioni a livello di colonna e di segmento sulle tabelle di archiviazione utilizzate da un database di Analysis Services in esecuzione in modalità tabulare o SharePoint.|  
|[Set di righe DISCOVER_STORAGE_TABLE_COLUMNS](../../analysis-services/schema-rowsets/xml/discover-storage-table-columns-rowset.md)|Consente al client di determinare l'assegnazione delle colonne alle tabelle di archiviazione utilizzate da un database di Analysis Services in esecuzione in modalità tabulare o SharePoint.|  
|[Set di righe DISCOVER_STORAGE_TABLES](../../analysis-services/schema-rowsets/xml/discover-storage-tables-rowset.md)|Restituisce informazioni sulle tabelle utilizzate per l'archiviazione dei modelli in un database modello tabulare.|  
|[Set di righe DISCOVER_TRACE_COLUMNS](../../analysis-services/schema-rowsets/xml/discover-trace-columns-rowset.md)|Restituisce una descrizione XML delle colonne disponibili in una traccia.|  
|[Set di righe DISCOVER_TRACE_DEFINITION_PROVIDERINFO](../../analysis-services/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset.md)|Restituisce informazioni su nome e versione del provider.|  
|[Set di righe DISCOVER_TRACE_EVENT_CATEGORIES](../../analysis-services/schema-rowsets/xml/discover-trace-event-categories-rowset.md)|Restituisce un elenco di tutte le categorie disponibili.|  
|[Set di righe DISCOVER_TRACES](../../analysis-services/schema-rowsets/xml/discover-traces-rowset.md)|Restituisce un elenco delle tracce in esecuzione attiva nella connessione corrente.|  
|[Set di righe DISCOVER_TRANSACTIONS](../../analysis-services/schema-rowsets/xml/discover-transactions-rowset.md)|Restituisce un elenco delle transazioni in esecuzione attiva nella connessione corrente.|  
|[Set di righe DISCOVER_XEVENT_TRACE_DEFINITION](http://msdn.microsoft.com/library/e1ce2d2d-f994-4318-801a-ee0385aecd84)|Restituisce un elenco delle tracce XEvent in esecuzione attiva nella connessione corrente.|  
|[Set di righe DMSCHEMA_MINING_COLUMNS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|Elenca le singole colonne di tutti i modelli di data mining disponibili nella connessione corrente.|  
|[Set di righe DMSCHEMA_MINING_FUNCTIONS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)|Restituisce un elenco di funzioni supportate dagli algoritmi di data mining nel server.|  
|[Set di righe DMSCHEMA_MINING_MODEL_CONTENT](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|Restituisce un set di righe composto da colonne che descrivono il modello corrente.|  
|[Set di righe DMSCHEMA_MINING_MODEL_CONTENT_PMML](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|Restituisce un set di righe composto da colonne che descrivono il modello corrente in formato PMML.|  
|[Set di righe DMSCHEMA_MINING_MODEL_XML](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)|Restituisce un set di righe composto da colonne che descrivono il modello corrente in formato PMML.|  
|[Set di righe DMSCHEMA_MINING_MODELS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|Restituisce un elenco dei modelli di data mining nel database corrente.|  
|[Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|Restituisce un elenco dei parametri per gli algoritmi nel server.|  
|[Set di righe DMSCHEMA_MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|Fornisce un elenco degli algoritmi di data mining disponibili nel server.|  
|[Set di righe DMSCHEMA_MINING_STRUCTURE_COLUMNS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|Restituisce un elenco di tutte le colonne di tutti i modelli di data mining disponibili nella connessione corrente.|  
|[Set di righe DMSCHEMA_MINING_STRUCTURES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|Elenca le strutture di data mining disponibili nella connessione corrente.|  
|[Set di righe MDSCHEMA_CUBES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|Restituisce informazioni sui cubi definiti nel database corrente.|  
|[Set di righe MDSCHEMA_DIMENSIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|Restituisce informazioni sulle dimensioni definite nel database corrente.|  
|[Set di righe MDSCHEMA_FUNCTIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)|Restituisce un elenco di funzioni disponibili per le applicazioni client connesse al database.|  
|[Set di righe MDSCHEMA_HIERARCHIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|Restituisce informazioni sulle gerarchie definite nel database corrente.|  
|[Set di righe MDSCHEMA_INPUT_DATASOURCES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)|Restituisce informazioni sugli oggetti origine dati definiti nel database corrente.|  
|[Set di righe MDSCHEMA_KPIS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|Restituisce informazioni sugli indicatori KPI definiti nel database corrente.|  
|[Set di righe MDSCHEMA_LEVELS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|Restituisce informazioni sui livelli nelle gerarchie definite nel database corrente.|  
|[Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)|Elenca la dimensione dei gruppi di misure.|  
|[Set di righe MDSCHEMA_MEASUREGROUPS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)|Restituisce un elenco dei gruppi di misure nella connessione corrente.|  
|[Set di righe MDSCHEMA_MEASURES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|Restituisce un elenco delle misure nella connessione corrente.|  
|[Set di righe mdschema_members](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|Restituisce un elenco di tutti i membri nella connessione corrente elencati per database, cubo e dimensione.|  
|[Set di righe MDSCHEMA_PROPERTIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|Restituisce un nome completo di ogni proprietà, insieme a tipo di proprietà, tipo di dati e altri metadati.|  
|[Set di righe MDSCHEMA_SETS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|Restituisce un elenco di set definiti nella connessione corrente.|  
  
## <a name="see-also"></a>Vedere anche   
 [Nuova DMV System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322)   
 [Nuova funzione SYSTEMRESTRICTEDSCHEMA per DMV e set di righe con restrizioni](http://go.microsoft.com/fwlink/?LinkId=231885)  
  
  
