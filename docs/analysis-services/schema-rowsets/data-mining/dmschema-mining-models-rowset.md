---
title: Set di righe DMSCHEMA_MINING_MODELS | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_MODELS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_MODELS rowset
ms.assetid: 1636f4cf-b342-4e2e-93b4-04136e2d41ef
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae35f0d1de25ed1551b4368009c4be28e2ea3ea5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="dmschemaminingmodels-rowset"></a>Set di righe DMSCHEMA_MINING_MODELS
  Enumera i modelli di data mining nel catalogo corrente. Il **DMSCHEMA_MINING_MODELS** set di righe include informazioni quali i nomi di modello, data di elaborazione e l'algoritmo di data mining associato a ogni modello di data mining.  
  
 . Il **DMSCHEMA_MINING_MODELS** è molto simile a set di righe dello schema di [DBSCHEMA_TABLES](../../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md) set di righe dello schema e può essere usato nello stesso modo.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_MODELS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Nome del catalogo. Popolato con il nome del database di cui il modello è membro.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Nome del modello di data mining. Questa colonna contiene il nome del modello di data mining e non è mai vuota.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Tipo di modello.|  
|**MODEL_GUID**|**DBTYPE_GUID**|GUID del modello.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descrizione intuitiva del modello.|  
|**MODEL_PROPID**|**DBTYPE_UI4**|ID di proprietà del modello. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**|Data di creazione del modello.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**|Data dell'ultima modifica della definizione del modello.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Enumerazione che identifica il tipo di algoritmo di data mining utilizzato dal modello. Il tipo può corrispondere a uno dei valori seguenti:<br /><br /> **DM_SERVICETYPE_CLASSIFICATION** (1)<br /><br /> **DM_SERVICETYPE_SEGMENTATION**(2)<br /><br /> **ASSOCIAZIONE DM_SERVICETYPE_**(4)<br /><br /> **DM_SERVICETYPE_ DENSITY_ESTIMATE**(8)<br /><br /> **DM_SERVICETYPE_SEQUENCE**(16)|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Nome specifico del provider per l'algoritmo di data mining utilizzato dal modello.|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**|Istruzione utilizzata per creare il modello di data mining.|  
|**PREDICTION_ENTITY**|**DBTYPE_WSTR**|Elenco delimitato da virgole che indica quali colonne di data mining possono essere stimate.|  
|**IS_POPULATED**|**DBTYPE_BOOL**|Flag booleano che indica se il modello è popolato.<br /><br /> **TRUE** se il modello è popolato; in caso contrario, **FALSE**.|  
|**MINING_PARAMETERS**|**DBTYPE_WSTR**|Elenco con valori separati da virgole dei parametri utilizzati durante la creazione del modello.|  
|**MINING_STRUCTURE**|**DBTYPE_WSTR**|ID della struttura di data mining su cui è basato il modello.|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**|Data dell'ultima elaborazione del modello.|  
|**MSOLAP_IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|Flag booleano che indica se il modello supporta il drill-through.|  
|**FILTRO**|**DBTYPE_WSTR**|Espressione di filtro associata al modello di data mining.<br /><br /> Un valore NULL o una stringa vuota indica che non è applicato alcun filtro.|  
|**TRAINING_SET_SIZE**|**DBTYPE_UIS**|Numero di case contenuti nel set di training del modello di data mining dopo l'elaborazione della struttura e dopo l'applicazione di eventuali filtri al modello.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_MODELS** set di righe può essere limitato sulle colonne nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Facoltativa.|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Facoltativa.|  
|**MINING_STRUCTURE**|**DBTYPE_WSTR**|Facoltativa.|  
  
 Per esempi di come eseguire una query di questo set di righe, vedere [parametri utilizzati per creare un modello di Data Mining di Query](../../../analysis-services/data-mining/query-the-parameters-used-to-create-a-mining-model.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
