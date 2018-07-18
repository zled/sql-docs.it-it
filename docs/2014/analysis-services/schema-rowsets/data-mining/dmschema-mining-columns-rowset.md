---
title: Set di righe DMSCHEMA_MINING_COLUMNS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_COLUMNS rowset
ms.assetid: ae35ccde-4438-46f4-8611-40b2b1a42fce
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 60dc2e773b93f27fe96489bcb55fdfe22c3168d4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232061"
---
# <a name="dmschemaminingcolumns-rowset"></a>Set di righe DMSCHEMA_MINING_COLUMNS
  Vengono descritte le singole colonne di tutti i modelli di data mining in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Questo set di righe è limitato al catalogo corrente.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_COLUMNS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo. Popolato con il nome del database di cui il modello è membro.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Nome del modello di data mining. Questa colonna contiene il nome del modello di data mining a cui è associata una colonna e non è mai vuota.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Nome della colonna.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||GUID della colonna. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||ID di proprietà della colonna. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Posizione ordinale della colonna. Le colonne vengono numerate a partire da 1. Questa colonna contiene `NULL` se non è presente alcun valore ordinale stabile per la colonna.|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||Valore booleano che indica se la colonna dispone di un valore predefinito.<br /><br /> È `TRUE` se la colonna dispone di un valore predefinito. In caso contrario è `FALSE`.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Valore predefinito della colonna.<br /><br /> Se il valore predefinito corrisponde al valore `NULL`, `COLUMN_HASDEFAULT` contiene `TRUE` e questa colonna contiene `NULL`.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||Maschera di bit che descrive le caratteristiche della colonna. Il tipo enumerato `DBCOLUMNFLAGS` specifica i bit nella maschera di bit. Questa colonna non è mai vuota.|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Valore booleano che indica se la colonna ammette valori Null.<br /><br /> È `FALSE` se la colonna non ammette valori Null. In caso contrario è `TRUE`.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Indicatore del tipo di dati della colonna. Nell'elenco seguente vengono illustrati alcuni esempi di tipi di marcatori restituiti.<br /><br /> "`TABLE`" restituisce `DBTYPE_HCHAPTER`.<br /><br /> "`TEXT`" restituisce `DBTYPE_WCHAR`.<br /><br /> "`LONG`" restituisce `DBTYPE_I8`.<br /><br /> "`DOUBLE`" restituisce `DBTYPE_R8`.<br /><br /> "`DATE`" restituisce `DBTYPE_DATE`.|  
|`TYPE_GUID`|`DBTYPE_GUID`||GUID del tipo di dati della colonna. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `VT_NULL`.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Lunghezza massima possibile di un valore nella colonna. Per le colonne di tipo carattere, binario o bit, i valori possibili sono i seguenti:<br /><br /> -La lunghezza massima della colonna in caratteri, byte o bit, rispetto al tipo di colonna, se è definita una lunghezza. Ad esempio, una colonna `CHAR(5)` in una tabella SQL dispone di una lunghezza massima di 5.<br />-La lunghezza massima del tipo di dati in caratteri, byte o bit, rispetto al tipo di colonna, se la colonna non ha una lunghezza definita.<br />-Zero (0) se la colonna né il tipo di dati ha una lunghezza massima definita.<br />-   `NULL` per tutti gli altri tipi di colonne|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Lunghezza massima in ottetti (byte) della colonna, se la colonna è di tipo carattere o binario. Un valore pari a zero (0) indica che la colonna non dispone di una lunghezza massima. Questa colonna contiene il valore `NULL` per tutti gli altri tipi di colonne.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Precisione massima della colonna se il tipo di dati della colonna è un tipo di dati numerico diverso da `VARNUMERIC`.<br /><br /> È `NULL` se il tipo di dati della colonna non è numerico oppure è `VARNUMERIC`.<br /><br /> La precisione delle colonne con un tipo di dati `DBTYPE_DECIMAL` o `DBTYPE_NUMERIC` dipende dalla definizione della colonna.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Numero di cifre a destra del separatore decimale se l'indicatore del tipo di colonna è `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC` o `DBTYPE_VARNUMERIC`. In caso contrario, questa colonna contiene un valore `VT_NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Precisione di data/ora, ovvero numero di cifre nella parte relativa ai secondi frazionari, della colonna se la colonna e di tipo datetime o intervallo. In caso contrario è `NULL`.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo in cui è definito il set di caratteri. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato in cui è definito il set di caratteri. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Nome del set di caratteri. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo in cui sono definite le regole di confronto. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato in cui sono definite le regole di confronto. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Nome delle regole di confronto. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo in cui è definito il dominio. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato in cui è definito il dominio. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Nome del dominio. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione intuitiva della colonna. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e contiene sempre `NULL`.|  
|`DISTRIBUTION_FLAG`|`DBTYPE_WSTR`||Descrizione della distribuzione statistica della colonna. Questa colonna contiene uno dei valori seguenti:<br /><br /> -   "`NORMAL`"<br />-   "`LOG_NORMAL`"<br />-   "`UNIFORM`"|  
|`CONTENT_TYPE`|`DBTYPE_WSTR`||Descrizione del contenuto della colonna. Questa colonna contiene uno dei valori seguenti:<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-"`DISCRETIZED(`[argomenti]`)`"<br />-   "`ORDERED`"<br />-   "`KEY TIME`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY_VARIANCE`"<br />-   "`PROBABILITY_STDEV`"<br />-   `"KEY SEQUENCE`"|  
|`MODELING_FLAG`|`DBTYPE_WSTR`||Elenco delimitato da virgole di flag. I flag definiti sono:<br /><br /> -   "`MODEL_EXISTENCE_ONLY`"<br />-   "`REGRESSOR`"<br /><br /> Questa colonna può inoltre contenere flag di modellazione specifici dell'algoritmo.|  
|`IS_RELATED_TO_KEY`|`DBTYPE_BOOL`||Valore booleano che indica se la colonna è correlata alla chiave.<br /><br /> È `TRUE` se questa colonna è correlata alla chiave. Se la chiave è costituita da un'unica colonna, il campo `RELATED_ATTRIBUTE` può contenere il nome della colonna corrispondente.|  
|`RELATED_ATTRIBUTE`|`DBTYPE_WSTR`||Nome della colonna di destinazione a cui è correlata la colonna corrente o che corrisponde a una proprietà speciale.|  
|`IS_INPUT`|`DBTYPE_BOOL`||Valore booleano che indica se la colonna è una colonna di input.<br /><br /> È `VARIANT_TRUE` se questa è una colonna di input.|  
|`IS_PREDICTABLE`|`DBTYPE_BOOL`||Valore booleano che indica se la colonna è stimabile.<br /><br /> È `TRUE` se la colonna è stimabile.|  
|`CONTAINING_COLUMN`|`DBTYPE_WSTR`||Nome della colonna `TABLE` che contiene questa colonna. Questa colonna contiene `NULL` se la colonna non è contenuta in un'altra colonna.|  
|`PREDICTION_SCALAR_FUNCTIONS`|`DBTYPE_WSTR`||Elenco delimitato da virgole di funzioni scalari che possono essere eseguite sulla colonna.|  
|`PREDICTION_TABLE_FUNCTIONS`|`DBTYPE_WSTR`||Elenco delimitato da virgole di funzioni che possono essere applicate alla colonna. Le funzioni devono restituire una tabella. Il formato dell'elenco è il seguente:<br /><br /> `<function name>(<column1> [, <column2>], ...)`<br /><br /> Il formato consente all'applicazione client di determinare la firma (elenco di parametri) per la rispettiva funzione.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Valore booleano che indica se è stato eseguito il training della colonna con un set di valori possibili.<br /><br /> È `TRUE` se è stato eseguito il training della colonna con un set di valori possibili.<br /><br /> Contiene `FALSE` se la colonna non è popolata.|  
|`PREDICTION_SCORE`|`DBTYPE_R8`||Punteggio del modello per la stima della colonna. Il punteggio viene utilizzato per misurare l'accuratezza di un modello.|  
|`SOURCE_COLUMN`|`DBTYPE_WSTR`||Nome della colonna della struttura di data mining di origine per la colonna di data mining corrente.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DMSCHEMA_MINING_COLUMNS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
