---
title: XML for Analysis Schema Rowsets | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- rowsets [Analysis Services], XML for Analysis
- XML for Analysis, schema rowsets
- schema rowsets [Analysis Services], XML for Analysis
- schema rowsets [XML for Analysis]
ms.assetid: 36e3ecfd-fcc3-415a-9c43-f59921d2468a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f0c44abd2ba4be59a86b46a9b0ff74196c570e5e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xml-for-analysis-schema-rowsets"></a>XML for Analysis Schema Rowsets
  Il provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) include set di righe dello schema che restituiscono metadati su stato del server, attività e oggetti. Il recupero dei metadati è necessario se si sviluppa un'applicazione client che si connette a un modello di Analysis Services con struttura e caratteristiche variabili.  
  
 I set di righe dello schema forniscono inoltre l'analisi dei processi e delle operazioni interne che possono facilitare il monitoraggio del server e la risoluzione dei problemi. Per supportare meglio le attività amministrative ad hoc, è possibile eseguire una query Dynamic Management View (DMV) sulla maggior parte dei set di righe dello schema. Le query DMV restituiscono risultati in un formato tabulare leggibile che è possibile visualizzare in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].  
  
 Nella tabella seguente viene elencato e descritto ogni set di righe dello schema XMLA e viene specificato se restituisce informazioni specifiche dei modelli di dati tabulari.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Set di righe<sup>1</sup>|Description|  
|------------------------|-----------------|  
|[Set di righe DISCOVER_CALC_DEPENDENCY](../../../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md)|Restituisce informazioni sulle dipendenze fra tabelle, colonne, misure e formule delle colonne calcolate.<br /><br /> Si applica ai modelli tabulari distribuiti in un'istanza di Analysis Services e [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modelli nelle cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_CONNECTIONS](../../../analysis-services/schema-rowsets/xml/discover-connections-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle connessioni attualmente aperte nel server.|  
|[Set di righe DISCOVER_COMMAND_OBJECTS](../../../analysis-services/schema-rowsets/xml/discover-command-objects-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative agli oggetti utilizzati dal comando a cui si fa riferimento.|  
|[Set di righe DISCOVER_COMMANDS](../../../analysis-services/schema-rowsets/xml/discover-commands-rowset.md)|Vengono fornite informazioni sull'utilizzo delle risorse e sulle attività relative all'ultimo comando eseguito o attualmente in esecuzione nelle connessioni aperte nel server.|  
|[Set di righe DISCOVER_CSDL_METADATA](../../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)|Restituisce una definizione XML di un'origine dati a un client in grado di utilizzare una tabella o [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] del modello e presentare i dati di origine come parte di un report.<br /><br /> Si applica ai modelli tabulari distribuiti in un'istanza di Analysis Services e [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modelli nelle cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_DATASOURCES](../../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md)|Restituisce un elenco delle origini dati del provider XMLA disponibili nel server o nel servizio Web.|  
|[Set di righe DISCOVER_DB_CONNECTIONS](../../../analysis-services/schema-rowsets/xml/discover-db-connections-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle connessioni attualmente aperte dal server a un database.|  
|[Set di righe DISCOVER_DIMENSION_STAT](../../../analysis-services/schema-rowsets/xml/discover-dimension-stat-rowset.md)|Restituisce statistiche sulla dimensione specificata.|  
|[Set di righe DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)|Restituisce un elenco di nomi, tipi di dati e valori di enumerazione di enumeratori supportati dal provider XMLA per un'origine dati specifica.|  
|[Set di righe DISCOVER_JOBS](../../../analysis-services/schema-rowsets/xml/discover-jobs-rowset.md)|Fornisce informazioni sui processi attivi in esecuzione nel server.|  
|[Set di righe DISCOVER_KEYWORDS &#40; XMLA &#41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)|Vengono restituite informazioni su parole chiave riservate dal provider XMLA.|  
|[Set di righe DISCOVER_LITERALS](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)|Restituisce informazioni sui valori letterali, inclusi tipi e valori di dati, supportati dal provider XMLA.|  
|[Set di righe DISCOVER_LOCATIONS](../../../analysis-services/schema-rowsets/xml/discover-locations-rowset.md)|Restituisce informazioni sul contenuto di un file di backup.|  
|[Set di righe DISCOVER_LOCKS](../../../analysis-services/schema-rowsets/xml/discover-locks-rowset.md)|Fornisce informazioni sui blocchi correnti presenti nel server.|  
|[Set di righe DISCOVER_MEMORYGRANT](../../../analysis-services/schema-rowsets/xml/discover-memorygrant-rowset.md)|Restituisce un elenco di concessioni di quote di memoria interna recuperate da processi attualmente in esecuzione nel server.|  
|[Set di righe DISCOVER_MEMORYUSAGE](../../../analysis-services/schema-rowsets/xml/discover-memoryusage-rowset.md)|Restituisce le statistiche di utilizzo della memoria per vari oggetti allocati dal server.|  
|[Set di righe DISCOVER_OBJECT_ACTIVITY](../../../analysis-services/schema-rowsets/xml/discover-object-activity-rowset.md)|Fornisce l'utilizzo delle risorse per oggetto dopo l'avvio del servizio.|  
|[Set di righe DISCOVER_OBJECT_MEMORY_USAGE](../../../analysis-services/schema-rowsets/xml/discover-object-memory-usage-rowset.md)|Fornisce informazioni sulle risorse di memoria utilizzate dagli oggetti.|  
|[Set di righe DISCOVER_PARTITION_DIMENSION_STAT](../../../analysis-services/schema-rowsets/xml/discover-partition-dimension-stat-rowset.md)|Restituisce statistiche sulla dimensione associata a una partizione.|  
|[Set di righe DISCOVER_PARTITION_STAT](../../../analysis-services/schema-rowsets/xml/discover-partition-stat-rowset.md)|Restituisce statistiche sulle aggregazioni in una partizione specifica.|  
|[Set di righe DISCOVER_PERFORMANCE_COUNTERS](../../../analysis-services/schema-rowsets/xml/discover-performance-counters-rowset.md)|Restituisce il valore di uno o più specifici contatori di prestazioni.|  
|[Set di righe DISCOVER_PROPERTIES](../../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)|Restituisce un elenco di informazioni e valori sulle proprietà standard e specifiche del provider supportate dal provider XMLA per l'origine dati specificata.|  
|[Set di righe DISCOVER_SCHEMA_ROWSETS](../../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)|Vengono restituiti nomi, restrizioni, descrizione e altre informazioni per tutti i valori di enumerazione e gli eventuali valori di enumerazione specifici del provider supportati dal provider XMLA.|  
|[Set di righe DISCOVER_SESSIONS](../../../analysis-services/schema-rowsets/xml/discover-sessions-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle sessioni attualmente aperte nel server.|  
|[Set di righe DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](../../../analysis-services/schema-rowsets/xml/discover-storage-table-column-segments-rowset.md)|Vengono fornite informazioni a livello di colonna e segmento sulle tabelle di archiviazione utilizzate da una tabella o [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] database.<br /><br /> Si applica ai modelli tabulari distribuiti in un'istanza di Analysis Services e [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modelli nelle cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_STORAGE_TABLE_COLUMNS](../../../analysis-services/schema-rowsets/xml/discover-storage-table-columns-rowset.md)|Consente al client di determinare l'assegnazione di colonne alle tabelle di archiviazione utilizzate da una tabella o [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] database.<br /><br /> Si applica ai modelli tabulari distribuiti in un'istanza di Analysis Services e [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modelli nelle cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_STORAGE_TABLES](../../../analysis-services/schema-rowsets/xml/discover-storage-tables-rowset.md)|Restituisce informazioni sulle tabelle utilizzate in un modello.<br /><br /> Si applica ai modelli tabulari distribuiti in un'istanza di Analysis Services e [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modelli nelle cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_TRACE_COLUMNS](../../../analysis-services/schema-rowsets/xml/discover-trace-columns-rowset.md)|Descrive le colonne di traccia fornite dal provider di traccia.|  
|[Set di righe DISCOVER_TRACE_DEFINITION_PROVIDERINFO](../../../analysis-services/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset.md)|Restituisce informazioni di base sul provider di traccia, quali il nome e descrizione.|  
|[Set di righe DISCOVER_TRACE_EVENT_CATEGORIES](../../../analysis-services/schema-rowsets/xml/discover-trace-event-categories-rowset.md)|Descrive le categorie di eventi fornite dal provider di traccia.|  
|[Set di righe DISCOVER_TRACES](../../../analysis-services/schema-rowsets/xml/discover-traces-rowset.md)|Restituisce informazioni sulle tracce in esecuzione in un server.|  
|[Set di righe DISCOVER_TRANSACTIONS](../../../analysis-services/schema-rowsets/xml/discover-transactions-rowset.md)|Restituisce il set corrente di transazioni in sospeso nel sistema.|  
|[Set di righe DISCOVER_XML_METADATA](../../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md)|Restituisce un documento XML in cui viene descritto un oggetto richiesto.|  
  
 <sup>1</sup> tutte le righe dello schema elencate di seguito sono supportate dal provider dell'origine dati MSOLAP per il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Provider XMLA.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Usare dinamica viste a Gestione &#40; viste a gestione dinamica &#41; per monitorare Analysis Services](../../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)   
 [Il recupero dei metadati da un'origine dati analitici](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  

