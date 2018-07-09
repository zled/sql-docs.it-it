---
title: Set di righe DMSCHEMA_MINING_SERVICES | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_SERVICES
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICES rowset
ms.assetid: 4a672f2f-d637-4def-a572-c18556f83d34
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e6ccfdba24d7bc23b97eb15e61321f82e5ab1d9b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278229"
---
# <a name="dmschemaminingservices-rowset"></a>Set di righe DMSCHEMA_MINING_SERVICES
  Fornisce una descrizione di ogni algoritmo di data mining supportato dal provider.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_SERVICES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Nome dell'algoritmo. Questa colonna è specifica del provider.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`||Questa colonna contiene una bitmap che descrive il servizio di data mining. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Popola questa colonna con uno dei valori seguenti:<br /><br /> -   `DM_SERVICETYPE_CLASSIFICATION` (`1`)<br />-   `DM_SERVICETYPE_CLUSTERING` (`2`)|  
|`SERVICE_DISPLAY_NAME`|`DBTYPE_WSTR`||Nome visualizzato localizzabile per l'algoritmo.|  
|`SERVICE_GUID`|`DBTYPE_GUID`||GUID dell'algoritmo.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione intuitiva dell'algoritmo.|  
|`PREDICTION_LIMIT`|`DBTYPE_UI4`||Numero massimo di stime che possono fornire il modello e l'algoritmo.|  
|`SUPPORTED_DISTRIBUTION_FLAGS`|`DBTYPE_WSTR`||Elenco delimitato da virgole di flag che descrivono le distribuzioni statistiche supportate dall'algoritmo. Questa colonna contiene uno o più dei valori seguenti:<br /><br /> -   "`NORMAL`"<br />-   "`LOG NORMAL`"<br />-   "`UNIFORM`"|  
|`SUPPORTED_INPUT_CONTENT_TYPES`|`DBTYPE_WSTR`||Elenco delimitato da virgole di flag che descrivono i tipi di contenuto di input supportati dall'algoritmo. Questa colonna contiene uno o più dei valori seguenti:<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-   "`DISCRETIZED`"<br />-   "`ORDERED`"<br />-"CHIAVE `SEQUENCE`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY VARIANCE`"<br />-   "`PROBABILITY STDEV`"<br />-   "`KEY TIME`"|  
|`SUPPORTED_PREDICTION_CONTENT_TYPES`|`DBTYPE_WSTR`||Elenco delimitato da virgole di flag che descrivono i tipi di contenuto di stima supportati dall'algoritmo. Questa colonna contiene uno o più dei valori seguenti:<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-   "`DISCRETIZED`"<br />-   "`ORDERED`"<br />-"CHIAVE `SEQUENCE` "<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY VARIANCE`"<br />-   "`PROBABILITY STDEV`"<br />-"LA CHIAVE TEMPORALE"|  
|`SUPPORTED_MODELING_FLAGS`|`DBTYPE_WSTR`||Elenco delimitato da virgole dei flag di modellazione supportati dall'algoritmo. Questa colonna contiene uno o più dei valori seguenti:<br /><br /> -   "`MODEL_EXISTENCE_ONLY`"<br />-   "`REGRESSOR`"<br /><br /> È inoltre possibile definire flag specifici del provider.|  
|`SUPPORTED_SOURCE_QUERY`|`DBTYPE_WSTR`||-Questa colonna è supportata per la compatibilità con le versioni precedenti.|  
|`TRAINING_COMPLEXITY`|`DBTYPE_I4`||La durata di tempo prevista per l'esecuzione del training:<br /><br /> -   `DM_TRAINING_COMPLEXITY_LOW` indica che il tempo di esecuzione è relativamente breve ed è proporzionale all'input.<br />-   **DM_TRAINING_COMPLEXITY_MEDIUM** indica che il tempo di esecuzione potrebbe essere lungo, ma è in genere proporzionale all'input.<br />-   **DM_TRAINING_COMPLEXITY_HIGH** indica che il tempo di esecuzione è lungo e può aumentare in misura esponenziale in relazione al numero di case di training.|  
|`PREDICTION_COMPLEXITY`|`DBTYPE_I4`||La durata di tempo prevista per la stima:<br /><br /> -   **DM_PREDICTION_COMPLEXITY_LOW** indica che il tempo di esecuzione è relativamente breve ed è proporzionale all'input.<br />-   **DM_PREDICTION_COMPLEXITY_MEDIUM** indica che il tempo di esecuzione potrebbe essere lungo, ma è in genere proporzionale all'input.<br />-   **DM_PREDICTION_COMPLEXITY_HIGH** indica che il tempo di esecuzione è lungo e può aumentare in misura esponenziale in relazione al numero di case di training.|  
|`EXPECTED_QUALITY`|`DBTYPE_I4`||Qualità prevista del modello prodotto con questo algoritmo:<br /><br /> -   `DM_EXPECTED_QUALITY_LOW`<br />-   `DM_EXPECTED_QUALITY_MEDIUM`<br />-   **DM_EXPECTED_QUALITY_HIGH**|  
|`SCALING`|`DBTYPE_I4`||Scalabilità dell'algoritmo.<br /><br /> -   **DM_SCALING_LOW**<br />-   `DM_SCALING_MEDIUM`<br />-   **DM_SCALING_HIGH**|  
|`ALLOW_INCREMENTAL_INSERT`|`DBTYPE_BOOL`||Valore booleano che indica se l'algoritmo supporta il training incrementale, ovvero l'aggiornamento dei modelli individuati in base a nuovi dati effettivi anziché mediante una nuova individuazione dei modelli.|  
|`ALLOW_PMML_INITIALIZATION`|`DBTYPE_BOOL`||Valore booleano che indica se è possibile creare modelli di data mining in base a una stringa PMML 2.1.<br /><br /> Se è `TRUE`, l'algoritmo di data mining supporta inizializzazione da contenuto PMML 2.1.|  
|`CONTROL`|`DBTYPE_I4`||Supporto fornito dal servizio se il training viene interrotto:<br /><br /> -   `DM_CONTROL_NONE` indica che l'algoritmo non può essere annullato dopo l'avvio per il training del modello.<br />-   `DM_CONTROL_CANCEL` indica che l'algoritmo può essere annullato dopo che viene avviato per il training del modello, ma deve essere riavviato per riprendere il training.<br />-   `DM_CONTROL_SUSPENDRESUME` indica che l'algoritmo può essere annullato e ripreso in qualsiasi momento, ma i risultati non sono disponibili fino al completamento del training.<br />-   `DM_CONTROL_SUSPENDWITHRESULT` indica che l'algoritmo può essere annullato e ripreso in qualsiasi momento e possono essere ottenuti eventuali risultati incrementali.|  
|`ALLOW_DUPLICATE_KEY`|`DBTYPE_BOOL`||Valore booleano che indica se i case possono contenere chiavi duplicate.<br /><br /> Se è `VARIANT_TRUE`, i case possono contenere chiavi duplicate.|  
|`VIEWER_TYPE`|`DBTYPE_WSTR`||Visualizzatore consigliato per questo modello.|  
|`HELP_FILE`|`DBTYPE_WSTR`||(Facoltativo) Nome del file che contiene la documentazione per questo servizio.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||(Facoltativo) ID di contesto della Guida per questo servizio.|  
|`MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL`|`DBTYPE_WSTR`||Versione DDL supportata. 0 indica nessun supporto DDL.|  
|`MSOLAP_SUPPORTS_OLAP_MINING_MODELS`|`DBTYPE_BOOL`||Valore booleano che indica se è possibile creare modelli di data mining OLAP.<br /><br /> Se è `TRUE`, è possibile creare modelli di data mining OLAP. Richiede che `MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL` sia diverso da zero.|  
|`MSOLAP_SUPPORTS_DATA_MINING_DIMENSIONS`|`DBTYPE_BOOL`||Valore booleano che indica se è possibile creare dimensioni di data mining.<br /><br /> Se è `TRUE`, è possibile creare dimensioni di data mining.|  
|`MSOLAP_SUPPORTS_DRILLTHROUGH`|`DBTYPE_BOOL`||Valore booleano che indica se il servizio supporta funzionalità drill-through.<br /><br /> Se è `TRUE`, il servizio supporta funzionalità drill-through.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DMSCHEMA_MINING_SERVICES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
