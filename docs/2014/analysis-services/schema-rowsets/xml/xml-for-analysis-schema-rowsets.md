---
title: XML for Analysis Schema Rowsets | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- rowsets [Analysis Services], XML for Analysis
- XML for Analysis, schema rowsets
- schema rowsets [Analysis Services], XML for Analysis
- schema rowsets [XML for Analysis]
ms.assetid: 36e3ecfd-fcc3-415a-9c43-f59921d2468a
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c8125b3543e6f3c088ad8b7ae7dd5952d52df26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159272"
---
# <a name="xml-for-analysis-schema-rowsets"></a>XML for Analysis Schema Rowsets
  Il provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) include set di righe dello schema che restituiscono metadati su stato del server, attività e oggetti. Il recupero dei metadati è necessario se si sviluppa un'applicazione client che si connette a un modello di Analysis Services con struttura e caratteristiche variabili.  
  
 I set di righe dello schema forniscono inoltre l'analisi dei processi e delle operazioni interne che possono facilitare il monitoraggio del server e la risoluzione dei problemi. Per supportare meglio le attività amministrative ad hoc, è possibile eseguire una query Dynamic Management View (DMV) sulla maggior parte dei set di righe dello schema. Le query DMV restituiscono risultati in un formato tabulare leggibile che è possibile visualizzare in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].  
  
 Nella tabella seguente viene elencato e descritto ogni set di righe dello schema XMLA e viene specificato se restituisce informazioni specifiche dei modelli di dati tabulari.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Set di righe<sup>1</sup>|Description|  
|------------------------|-----------------|  
|[Set di righe DISCOVER_CALC_DEPENDENCY](discover-calc-dependency-rowset.md)|Restituisce informazioni sulle dipendenze fra tabelle, colonne, misure e formule delle colonne calcolate.<br /><br /> Si applica a modelli tabulari distribuiti in un'istanza di Analysis Services e a modelli di PowerPivot in cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_CONNECTIONS](discover-connections-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle connessioni attualmente aperte nel server.|  
|[Set di righe DISCOVER_COMMAND_OBJECTS](discover-command-objects-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative agli oggetti utilizzati dal comando a cui si fa riferimento.|  
|[Set di righe DISCOVER_COMMANDS](discover-commands-rowset.md)|Vengono fornite informazioni sull'utilizzo delle risorse e sulle attività relative all'ultimo comando eseguito o attualmente in esecuzione nelle connessioni aperte nel server.|  
|[Set di righe DISCOVER_CSDL_METADATA](discover-csdl-metadata-rowset.md)|Restituisce una definizione XML di un'origine dati a un client tramite cui è possibile utilizzare un modello tabulare o PowerPivot e presentare i dati dell'origine come parte di un report.<br /><br /> Si applica a modelli tabulari distribuiti in un'istanza di Analysis Services e a modelli di PowerPivot in cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_DATASOURCES](discover-datasources-rowset.md)|Restituisce un elenco delle origini dati del provider XMLA disponibili nel server o nel servizio Web.|  
|[Set di righe DISCOVER_DB_CONNECTIONS](discover-db-connections-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle connessioni attualmente aperte dal server a un database.|  
|[Set di righe DISCOVER_DIMENSION_STAT](discover-dimension-stat-rowset.md)|Restituisce statistiche sulla dimensione specificata.|  
|[Set di righe DISCOVER_ENUMERATORS](discover-enumerators-rowset.md)|Restituisce un elenco di nomi, tipi di dati e valori di enumerazione di enumeratori supportati dal provider XMLA per un'origine dati specifica.|  
|[Set di righe DISCOVER_JOBS](discover-jobs-rowset.md)|Fornisce informazioni sui processi attivi in esecuzione nel server.|  
|[Set di righe DISCOVER_KEYWORDS &#40;XMLA&#41;](discover-keywords-rowset-xmla.md)|Vengono restituite informazioni su parole chiave riservate dal provider XMLA.|  
|[Set di righe DISCOVER_LITERALS](discover-literals-rowset.md)|Restituisce informazioni sui valori letterali, inclusi tipi e valori di dati, supportati dal provider XMLA.|  
|[Set di righe DISCOVER_LOCATIONS](discover-locations-rowset.md)|Restituisce informazioni sul contenuto di un file di backup.|  
|[Set di righe DISCOVER_LOCKS](discover-locks-rowset.md)|Fornisce informazioni sui blocchi correnti presenti nel server.|  
|[Set di righe DISCOVER_MEMORYGRANT](discover-memorygrant-rowset.md)|Restituisce un elenco di concessioni di quote di memoria interna recuperate da processi attualmente in esecuzione nel server.|  
|[Set di righe DISCOVER_MEMORYUSAGE](discover-memoryusage-rowset.md)|Restituisce le statistiche di utilizzo della memoria per vari oggetti allocati dal server.|  
|[Set di righe DISCOVER_OBJECT_ACTIVITY](discover-object-activity-rowset.md)|Fornisce l'utilizzo delle risorse per oggetto dopo l'avvio del servizio.|  
|[Set di righe DISCOVER_OBJECT_MEMORY_USAGE](discover-object-memory-usage-rowset.md)|Fornisce informazioni sulle risorse di memoria utilizzate dagli oggetti.|  
|[Set di righe DISCOVER_PARTITION_DIMENSION_STAT](discover-partition-dimension-stat-rowset.md)|Restituisce statistiche sulla dimensione associata a una partizione.|  
|[Set di righe DISCOVER_PARTITION_STAT](discover-partition-stat-rowset.md)|Restituisce statistiche sulle aggregazioni in una partizione specifica.|  
|[Set di righe DISCOVER_PERFORMANCE_COUNTERS](discover-performance-counters-rowset.md)|Restituisce il valore di uno o più specifici contatori di prestazioni.|  
|[Set di righe DISCOVER_PROPERTIES](discover-properties-rowset.md)|Restituisce un elenco di informazioni e valori sulle proprietà standard e specifiche del provider supportate dal provider XMLA per l'origine dati specificata.|  
|[Set di righe DISCOVER_SCHEMA_ROWSETS](discover-schema-rowsets-rowset.md)|Vengono restituiti nomi, restrizioni, descrizione e altre informazioni per tutti i valori di enumerazione e gli eventuali valori di enumerazione specifici del provider supportati dal provider XMLA.|  
|[Set di righe DISCOVER_SESSIONS](discover-sessions-rowset.md)|Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle sessioni attualmente aperte nel server.|  
|[Set di righe DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](discover-storage-table-column-segments-rowset.md)|Fornisce informazioni a livello di colonna e segmento sulle tabelle di archiviazione utilizzate da un database tabulare o PowerPivot.<br /><br /> Si applica a modelli tabulari distribuiti in un'istanza di Analysis Services e a modelli di PowerPivot in cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_STORAGE_TABLE_COLUMNS](discover-storage-table-columns-rowset.md)|Consente al client di determinare l'assegnazione di colonne alle tabelle di archiviazione utilizzate da un database tabulare o PowerPivot.<br /><br /> Si applica a modelli tabulari distribuiti in un'istanza di Analysis Services e a modelli di PowerPivot in cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_STORAGE_TABLES](discover-storage-tables-rowset.md)|Restituisce informazioni sulle tabelle utilizzate in un modello.<br /><br /> Si applica a modelli tabulari distribuiti in un'istanza di Analysis Services e a modelli di PowerPivot in cartelle di lavoro di Excel in esecuzione in un ambiente SharePoint.|  
|[Set di righe DISCOVER_TRACE_COLUMNS](discover-trace-columns-rowset.md)|Descrive le colonne di traccia fornite dal provider di traccia.|  
|[Set di righe DISCOVER_TRACE_DEFINITION_PROVIDERINFO](discover-trace-definition-providerinfo-rowset.md)|Restituisce informazioni di base sul provider di traccia, quali il nome e descrizione.|  
|[Set di righe DISCOVER_TRACE_EVENT_CATEGORIES](discover-trace-event-categories-rowset.md)|Descrive le categorie di eventi fornite dal provider di traccia.|  
|[Set di righe DISCOVER_TRACES](discover-traces-rowset.md)|Restituisce informazioni sulle tracce in esecuzione in un server.|  
|[Set di righe DISCOVER_TRANSACTIONS](discover-transactions-rowset.md)|Restituisce il set corrente di transazioni in sospeso nel sistema.|  
|[Set di righe DISCOVER_XML_METADATA](discover-xml-metadata-rowset.md)|Restituisce un documento XML in cui viene descritto un oggetto richiesto.|  
  
 <sup>1</sup> tutte le righe dello schema elencati di seguito sono supportate dal provider dell'origine dati MSOLAP per il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Provider XMLA.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Usare le viste a gestione dinamica &#40;viste a gestione dinamica&#41; per monitorare Analysis Services](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)   
 [Recupero di metadati da un'origine dati analitici](../../multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
