---
title: Set di righe DMSCHEMA_MINING_SERVICES | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_SERVICES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICES rowset
ms.assetid: 4a672f2f-d637-4def-a572-c18556f83d34
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7e7a9f2cd1d082bd2c33a15c66ce9b3fb170eb9e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingservices-rowset"></a>Set di righe DMSCHEMA_MINING_SERVICES
  Fornisce una descrizione di ogni algoritmo di data mining supportato dal provider.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_SERVICES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Nome dell'algoritmo. Questa colonna è specifica del provider.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Questa colonna contiene una bitmap che descrive il servizio di data mining. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] popola questa colonna con uno dei valori seguenti:<br /><br /> **DM_SERVICETYPE_CLASSIFICATION** (**1**)<br /><br /> **DM_SERVICETYPE_CLUSTERING** (**2**)|  
|**SERVICE_DISPLAY_NAME**|**DBTYPE_WSTR**|Nome visualizzato localizzabile per l'algoritmo.|  
|**SERVICE_GUID**|**DBTYPE_GUID**|GUID dell'algoritmo.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descrizione intuitiva dell'algoritmo.|  
|**PREDICTION_LIMIT**|**DBTYPE_UI4**|Numero massimo di stime che possono fornire il modello e l'algoritmo.|  
|**SUPPORTED_DISTRIBUTION_FLAGS**|**DBTYPE_WSTR**|Elenco delimitato da virgole di flag che descrivono le distribuzioni statistiche supportate dall'algoritmo. Questa colonna contiene uno o più dei valori seguenti:<br /><br /> "**NORMALE**"<br /><br /> "**LOG NORMALE**"<br /><br /> "**UNIFORM**"|  
|**SUPPORTED_INPUT_CONTENT_TYPES**|**DBTYPE_WSTR**|Elenco delimitato da virgole di flag che descrivono i tipi di contenuto di input supportati dall'algoritmo. Questa colonna contiene uno o più dei valori seguenti:<br /><br /> "**CHIAVE**"<br /><br /> "**DISCRETE**"<br /><br /> "**CONTINUO**"<br /><br /> "**DISCRETIZED**"<br /><br /> "**ORDERED**"<br /><br /> "CHIAVE **SEQUENZA**"<br /><br /> "**CYCLICAL**"<br /><br /> "**PROBABILITÀ**"<br /><br /> "**VARIANZA**"<br /><br /> "**STDEV**"<br /><br /> "**SUPPORTO**"<br /><br /> "**VARIANZA DELLA PROBABILITÀ**"<br /><br /> "**STDEV PROBABILITÀ**"<br /><br /> "**CHIAVE TEMPORALE**"|  
|**SUPPORTED_PREDICTION_CONTENT_TYPES**|**DBTYPE_WSTR**|Elenco delimitato da virgole di flag che descrivono i tipi di contenuto di stima supportati dall'algoritmo. Questa colonna contiene uno o più dei valori seguenti:<br /><br /> "**CHIAVE**"<br /><br /> "**DISCRETE**"<br /><br /> "**CONTINUO**"<br /><br /> "**DISCRETIZED**"<br /><br /> "**ORDERED**"<br /><br /> "CHIAVE **SEQUENZA** "<br /><br /> "**CYCLICAL**"<br /><br /> "**PROBABILITÀ**"<br /><br /> "**VARIANZA**"<br /><br /> "**STDEV**"<br /><br /> "**SUPPORTO**"<br /><br /> "**VARIANZA DELLA PROBABILITÀ**"<br /><br /> "**STDEV PROBABILITÀ**"<br /><br /> "KEY TIME"|  
|**SUPPORTED_MODELING_FLAGS**|**DBTYPE_WSTR**|Elenco delimitato da virgole dei flag di modellazione supportati dall'algoritmo. Questa colonna contiene uno o più dei valori seguenti:<br /><br /> "**MODEL_EXISTENCE_ONLY**"<br /><br /> "**REGRESSORE**"<br /><br /> <br /><br /> Si noti che è anche possibile definire flag specifici del provider.|  
|**SUPPORTED_SOURCE_QUERY**|**DBTYPE_WSTR**|Questa colonna è supportata per garantire la compatibilità con le versioni precedenti.|  
|**TRAINING_COMPLEXITY**|**DBTYPE_I4**|La durata di tempo prevista per l'esecuzione del training:<br /><br /> **DM_TRAINING_COMPLEXITY_LOW** indica che il tempo di esecuzione è relativamente breve ed è proporzionale all'input.<br /><br /> **DM_TRAINING_COMPLEXITY_MEDIUM** indica che il tempo di esecuzione potrebbe essere lungo, ma è in genere è proporzionale all'input.<br /><br /> **DM_TRAINING_COMPLEXITY_HIGH** indica che il tempo di esecuzione è lungo e può aumentare in modo esponenziale in relazione al numero di case di training.|  
|**PREDICTION_COMPLEXITY**|**DBTYPE_I4**|La durata di tempo prevista per la stima:<br /><br /> **DM_PREDICTION_COMPLEXITY_LOW** indica che il tempo di esecuzione è relativamente breve ed è proporzionale all'input.<br /><br /> **DM_PREDICTION_COMPLEXITY_MEDIUM** indica che il tempo di esecuzione potrebbe essere lungo, ma è in genere è proporzionale all'input.<br /><br /> **DM_PREDICTION_COMPLEXITY_HIGH** indica che il tempo di esecuzione è lungo e può aumentare in modo esponenziale in relazione al numero di case di training.|  
|**EXPECTED_QUALITY**|**DBTYPE_I4**|Qualità prevista del modello prodotto con questo algoritmo:<br /><br /> **DM_EXPECTED_QUALITY_LOW**<br /><br /> **DM_EXPECTED_QUALITY_MEDIUM**<br /><br /> **DM_EXPECTED_QUALITY_HIGH**|  
|**LA SCALABILITÀ**|**DBTYPE_I4**|Scalabilità dell'algoritmo.<br /><br /> **DM_SCALING_LOW**<br /><br /> **DM_SCALING_MEDIUM**<br /><br /> **DM_SCALING_HIGH**|  
|**ALLOW_INCREMENTAL_INSERT**|**DBTYPE_BOOL**|Valore booleano che indica se l'algoritmo supporta il training incrementale, ovvero l'aggiornamento dei modelli individuati in base a nuovi dati effettivi anziché mediante una nuova individuazione dei modelli.|  
|**ALLOW_PMML_INITIALIZATION**|**DBTYPE_BOOL**|Valore booleano che indica se è possibile creare modelli di data mining in base a una stringa PMML 2.1.<br /><br /> Se **TRUE**, l'algoritmo di data mining supporta inizializzazione da contenuto PMML 2.1.|  
|**CONTROLLO**|**DBTYPE_I4**|Supporto fornito dal servizio se il training viene interrotto:<br /><br /> **DM_CONTROL_NONE** indica che l'algoritmo non può essere annullato dopo l'avvio per il training del modello.<br /><br /> **DM_CONTROL_CANCEL** indica che l'algoritmo può essere annullato dopo l'avvio del training del modello, ma deve essere riavviato per riprendere il training.<br /><br /> **DM_CONTROL_SUSPENDRESUME** indica che l'algoritmo può essere annullato e ripreso in qualsiasi momento, ma risultati non sono disponibili fino al completamento del training.<br /><br /> **DM_CONTROL_SUSPENDWITHRESULT** indica che l'algoritmo può essere annullato e ripreso in qualsiasi momento e che è possono ottenere eventuali risultati incrementali.|  
|**ALLOW_DUPLICATE_KEY**|**DBTYPE_BOOL**|Valore booleano che indica se i case possono contenere chiavi duplicate.<br /><br /> Se **VARIANT_TRUE**, case possono contenere chiavi duplicate.|  
|**VIEWER_TYPE**|**DBTYPE_WSTR**|Visualizzatore consigliato per questo modello.|  
|**HELP_FILE**|**DBTYPE_WSTR**|(Facoltativo) Nome del file che contiene la documentazione per questo servizio.|  
|**HELP_CONTEXT**|**DBTYPE_I4**|(Facoltativo) ID di contesto della Guida per questo servizio.|  
|**MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL**|**DBTYPE_WSTR**|Versione DDL supportata. 0 indica nessun supporto DDL.|  
|**MSOLAP_SUPPORTS_OLAP_MINING_MODELS**|**DBTYPE_BOOL**|Valore booleano che indica se è possibile creare modelli di data mining OLAP.<br /><br /> Se **TRUE**, è possibile creare modelli di data mining OLAP. Richiede **MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL** sia diverso da zero.|  
|**MSOLAP_SUPPORTS_DATA_MINING_DIMENSIONS**|**DBTYPE_BOOL**|Valore booleano che indica se è possibile creare dimensioni di data mining.<br /><br /> Se **TRUE**, dimensioni di data mining possono essere create.|  
|**MSOLAP_SUPPORTS_DRILLTHROUGH**|**DBTYPE_BOOL**|Valore booleano che indica se il servizio supporta funzionalità drill-through.<br /><br /> Se **TRUE**, il servizio supporta funzionalità drill-through.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_SERVICES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Data Mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

