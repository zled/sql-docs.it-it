---
title: Set di righe DMSCHEMA_MINING_MODELS | Documenti Microsoft
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
- DMSCHEMA_MINING_MODELS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODELS rowset
ms.assetid: 1636f4cf-b342-4e2e-93b4-04136e2d41ef
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d8296ddb800b7691936236aa0cdb6550c89c34c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156570"
---
# <a name="dmschemaminingmodels-rowset"></a>Set di righe DMSCHEMA_MINING_MODELS
  Enumera i modelli di data mining nel catalogo corrente. Il set di righe `DMSCHEMA_MINING_MODELS` include informazioni, ad esempio i nomi di modello, la data di elaborazione e l'algoritmo di data mining associato a ogni modello di data mining.  
  
 , Il `DMSCHEMA_MINING_MODELS` set di righe dello schema è molto simile al [DBSCHEMA_TABLES](../ole-db/dbschema-tables-rowset.md) set di righe dello schema e può essere usato nello stesso modo.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_MODELS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo. Popolato con il nome del database di cui il modello è membro.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Nome del modello di data mining. Questa colonna contiene il nome del modello di data mining e non è mai vuota.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Tipo di modello.|  
|`MODEL_GUID`|`DBTYPE_GUID`||GUID del modello.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione intuitiva del modello.|  
|`MODEL_PROPID`|`DBTYPE_UI4`||ID di proprietà del modello. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Data di creazione del modello.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Data dell'ultima modifica della definizione del modello.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`||Enumerazione che identifica il tipo di algoritmo di data mining utilizzato dal modello. Il tipo può corrispondere a uno dei valori seguenti:<br /><br /> -   `DM_SERVICETYPE_CLASSIFICATION` (1)<br />-   `DM_SERVICETYPE_SEGMENTATION`(2)<br />-   `DM_SERVICETYPE_ ASSOCIATION`(4)<br />-   `DM_SERVICETYPE_ DENSITY_ESTIMATE`(8)<br />-   `DM_SERVICETYPE_SEQUENCE`(16)|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Nome specifico del provider per l'algoritmo di data mining utilizzato dal modello.|  
|`CREATION_STATEMENT`|`DBTYPE_WSTR`||Istruzione utilizzata per creare il modello di data mining.|  
|`PREDICTION_ENTITY`|`DBTYPE_WSTR`||Elenco delimitato da virgole che indica quali colonne di data mining possono essere stimate.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Flag booleano che indica se il modello è popolato.<br /><br /> `TRUE` se il modello è popolato; in caso contrario, `FALSE`.|  
|`MINING_PARAMETERS`|`DBTYPE_WSTR`||Elenco con valori separati da virgole dei parametri utilizzati durante la creazione del modello.|  
|`MINING_STRUCTURE`|`DBTYPE_WSTR`||ID della struttura di data mining su cui è basato il modello.|  
|`LAST_PROCESSED`|`DBTYPE_DBTIMESTAMP`||Data dell'ultima elaborazione del modello.|  
|`MSOLAP_IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||Flag booleano che indica se il modello supporta il drill-through.|  
|`FILTER`|`DBTYPE_WSTR`||Espressione di filtro associata al modello di data mining.<br /><br /> Un valore NULL o una stringa vuota indica che non è applicato alcun filtro.|  
|`TRAINING_SET_SIZE`|`DBTYPE_UIS`||Numero di case contenuti nel set di training del modello di data mining dopo l'elaborazione della struttura e dopo l'applicazione di eventuali filtri al modello.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DMSCHEMA_MINING_MODELS` può essere limitato nelle colonne della tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Facoltativo.|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`|Facoltativo.|  
|`MINING_STRUCTURE`|`DBTYPE_WSTR`|Facoltativo.|  
  
 Per esempi di come eseguire una query di questo set di righe, vedere [i parametri utilizzati per creare un modello di Data Mining di Query](../../data-mining/query-the-parameters-used-to-create-a-mining-model.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  