---
title: Set di righe DMSCHEMA_MINING_COLUMNS | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DMSCHEMA_MINING_COLUMNS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_COLUMNS rowset
ms.assetid: ae35ccde-4438-46f4-8611-40b2b1a42fce
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e37841617289eaa71af4d7c2c091459f32a745b6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="dmschemaminingcolumns-rowset"></a>Set di righe DMSCHEMA_MINING_COLUMNS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Vengono descritte le singole colonne di tutti i modelli di data mining in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Questo set di righe è limitato al catalogo corrente.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_COLUMNS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Nome del catalogo. Popolato con il nome del database di cui il modello è membro.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Nome del modello di data mining. Questa colonna contiene il nome del modello di data mining a cui è associata una colonna e non è mai vuota.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|Nome della colonna.|  
|**CON**|**DBTYPE_GUID**|GUID della colonna. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**COLUMN_PROPID**|**DBTYPE_UI4**|ID di proprietà della colonna. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**|Posizione ordinale della colonna. Le colonne vengono numerate a partire da 1. Questa colonna contiene **NULL** se è presente alcun valore ordinale stabile per la colonna.|  
|**COLUMN_HAS_DEFAULT**|**DBTYPE_BOOL**|Valore booleano che indica se la colonna dispone di un valore predefinito.<br /><br /> **TRUE** se la colonna contiene un valore predefinito, in caso contrario **FALSE**.|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**|Valore predefinito della colonna.<br /><br /> Se il valore predefinito è il **NULL** valore **COLUMN_HASDEFAULT** contiene **TRUE**, e questa colonna contiene **NULL**.|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**|Maschera di bit che descrive le caratteristiche della colonna. Il **DBCOLUMNFLAGS** tipo enumerato specifica i bit nella maschera di bit. Questa colonna non è mai vuota.|  
|**IS_NULLABLE**|**DBTYPE_BOOL**|Valore booleano che indica se la colonna ammette valori Null.<br /><br /> **FALSE** se la colonna è notoriamente non ammette valori null; in caso contrario, **TRUE**.|  
|**DATA_TYPE**|**DBTYPE_UI2**|Indicatore del tipo di dati della colonna. Nell'elenco seguente vengono illustrati alcuni esempi di tipi di marcatori restituiti.<br /><br /> "**Tabella**" restituirebbe **DBTYPE_HCHAPTER**.<br /><br /> "**Testo**" restituirebbe **DBTYPE_WCHAR**.<br /><br /> "**Lungo**" restituirebbe **DBTYPE_I8**.<br /><br /> "**DOPPIE**" restituirebbe **DBTYPE_R8**.<br /><br /> "**Data**" restituirebbe **DBTYPE_DATE**.|  
|**TYPE_GUID**|**DBTYPE_GUID**|GUID del tipo di dati della colonna. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **VT_NULL**.|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**|Lunghezza massima possibile di un valore nella colonna. Per le colonne di tipo carattere, binario o bit, i valori possibili sono i seguenti:<br /><br /> Lunghezza massima della colonna in caratteri, byte o bit, rispetto al tipo di colonna, se è definita una lunghezza. Ad esempio, un **char (5)** colonna in una tabella SQL ha una lunghezza massima di 5.<br /><br /> Lunghezza massima del tipo di dati in caratteri, byte o bit, rispetto al tipo di colonna, se la colonna non dispone di una lunghezza definita.<br /><br /> È zero (0) se né la colonna né il tipo di dati dispongono di una lunghezza massima definita.<br /><br /> **NULL** per tutti gli altri tipi di colonne|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**|Lunghezza massima in ottetti (byte) della colonna, se la colonna è di tipo carattere o binario. Un valore pari a zero (0) indica che la colonna non dispone di una lunghezza massima. Questa colonna contiene **NULL** per tutti gli altri tipi di colonne.|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**|La precisione massima della colonna se il tipo di dati della colonna è diverso da un tipo di dati numerici **VARNUMERIC**.<br /><br /> **NULL** se il tipo di dati della colonna non è numerico oppure è **VARNUMERIC**.<br /><br /> La precisione delle colonne con tipo di dati **DBTYPE_DECIMAL** o **DBTYPE_NUMERIC** dipende dalla definizione della colonna.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**|Il numero di cifre a destra del separatore decimale se l'indicatore del tipo della colonna è **DBTYPE_DECIMAL**, **DBTYPE_NUMERIC**, o **DBTYPE_VARNUMERIC**. In caso contrario, questa colonna contiene **VT_NULL**.|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**|La precisione di data/ora (numero di cifre nella parte relativa ai secondi frazionari) della colonna se il tipo di dati della colonna è un tipo DateTime o intervallo. in caso contrario, **NULL**.|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**|Nome del catalogo in cui è definito il set di caratteri. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**|Nome dello schema non qualificato in cui è definito il set di caratteri. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**|Nome del set di caratteri. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**|Nome del catalogo in cui sono definite le regole di confronto. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**|Nome dello schema non qualificato in cui sono definite le regole di confronto. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**COLLATION_NAME**|**DBTYPE_WSTR**|Nome delle regole di confronto. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**|Nome del catalogo in cui è definito il dominio. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**|Nome dello schema non qualificato in cui è definito il dominio. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**NOME_DOMINIO**|**DBTYPE_WSTR**|Nome del dominio. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descrizione intuitiva della colonna di questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**DISTRIBUTION_FLAG**|**DBTYPE_WSTR**|Descrizione della distribuzione statistica della colonna. Questa colonna contiene uno dei valori seguenti:<br /><br /> "**NORMALE**"<br /><br /> "**LOG_NORMAL**"<br /><br /> "**UNIFORM**"|  
|**CONTENT_TYPE**|**DBTYPE_WSTR**|Descrizione del contenuto della colonna. Questa colonna contiene uno dei valori seguenti:<br /><br /> "**CHIAVE**"<br /><br /> "**DISCRETE**"<br /><br /> "**CONTINUO**"<br /><br /> "**DISCRETIZED (**[argomenti]**)**"<br /><br /> "**ORDERED**"<br /><br /> "**CHIAVE TEMPORALE**"<br /><br /> "**CYCLICAL**"<br /><br /> "**PROBABILITÀ**"<br /><br /> "**VARIANZA**"<br /><br /> "**STDEV**"<br /><br /> "**SUPPORTO**"<br /><br /> "**PROBABILITY_VARIANCE**"<br /><br /> "**PROBABILITY_STDEV**"<br /><br /> **"SEQUENZA DI TASTI**"|  
|**MODELING_FLAG**|**DBTYPE_WSTR**|Elenco delimitato da virgole di flag. I flag definiti sono:<br /><br /> "**MODEL_EXISTENCE_ONLY**"<br /><br /> "**REGRESSORE**"<br /><br /> Questa colonna può inoltre contenere flag di modellazione specifici dell'algoritmo.|  
|**IS_RELATED_TO_KEY**|**DBTYPE_BOOL**|Valore booleano che indica se la colonna è correlata alla chiave.<br /><br /> **TRUE** se questa colonna è correlata alla chiave. Se la chiave è una singola colonna, il **RELATED_ATTRIBUTE** campo può contenere facoltativamente il nome della colonna.|  
|**RELATED_ATTRIBUTE**|**DBTYPE_WSTR**|Nome della colonna di destinazione a cui è correlata la colonna corrente o che corrisponde a una proprietà speciale.|  
|**IS_INPUT**|**DBTYPE_BOOL**|Valore booleano che indica se la colonna è una colonna di input.<br /><br /> **VARIANT_TRUE** se si tratta di una colonna di input.|  
|**IS_PREDICTABLE**|**DBTYPE_BOOL**|Valore booleano che indica se la colonna è stimabile.<br /><br /> **TRUE** se la colonna è stimabile.|  
|**CONTAINING_COLUMN**|**DBTYPE_WSTR**|Il nome del **tabella** colonna che contiene questa colonna. Questa colonna contiene **NULL** se la colonna non è contenuta in un'altra colonna.|  
|**PREDICTION_SCALAR_FUNCTIONS**|**DBTYPE_WSTR**|Elenco delimitato da virgole di funzioni scalari che possono essere eseguite sulla colonna.|  
|**PREDICTION_TABLE_FUNCTIONS**|**DBTYPE_WSTR**|Elenco delimitato da virgole di funzioni che possono essere applicate alla colonna. Le funzioni devono restituire una tabella. Il formato dell'elenco è il seguente:<br /><br /> `<function name>(<column1> [, <column2>], ...)`<br /><br /> Il formato consente all'applicazione client di determinare la firma (elenco di parametri) per la rispettiva funzione.|  
|**IS_POPULATED**|**DBTYPE_BOOL**|Valore booleano che indica se è stato eseguito il training della colonna con un set di valori possibili.<br /><br /> **TRUE** se la colonna è stata eseguita con un set di valori possibili.<br /><br /> Contiene **FALSE** se la colonna non viene popolata.|  
|**PREDICTION_SCORE**|**DBTYPE_R8**|Punteggio del modello per la stima della colonna. Il punteggio viene utilizzato per misurare l'accuratezza di un modello.|  
|**SOURCE_COLUMN**|**DBTYPE_WSTR**|Nome della colonna della struttura di data mining di origine per la colonna di data mining corrente.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_COLUMNS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Facoltativo.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Facoltativo.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
