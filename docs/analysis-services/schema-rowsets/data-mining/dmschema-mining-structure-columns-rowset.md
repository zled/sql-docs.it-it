---
title: Set di righe DMSCHEMA_MINING_STRUCTURE_COLUMNS | Documenti Microsoft
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
- DMSCHEMA_MINING_STRUCTURE_COLUMNS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURE_COLUMNS rowset
ms.assetid: 81f25502-ac90-42f1-8ddf-7b0f9752ebfd
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ff811a339635f5ff914224a060e14a52e3f94d6c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingstructurecolumns-rowset"></a>Set di righe DMSCHEMA_MINING_STRUCTURE_COLUMNS
  Vengono descritte le singole colonne di tutte le strutture di data mining distribuite in un server che esegue [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_STRUCTURE_COLUMNS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**||Nome del catalogo.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**||Nome dello schema non qualificato. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]non supporta schemi, pertanto questa colonna è sempre **NULL**.|  
|**NOME_STRUTTURA**|**DBTYPE_WSTR**||Nome della struttura. Questa colonna non può contenere un **NULL**.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**||Nome della colonna. L'univocità è garantita solo nelle colonne che condividono lo stesso modello. Ad esempio, due colonne nidificate possono avere lo stesso nome se appartengono a due tabelle nidificate diverse all'interno della stessa struttura.|  
|**CON**|**DBTYPE_GUID**||GUID della colonna. I provider che non utilizzano GUID per identificare le colonne restituiscono **NULL** in questa colonna.|  
|**COLUMN_PROPID**|**DBTYPE_UI4**||ID di proprietà della colonna. I provider che non associano ID di proprietà alle colonne restituiscono **NULL** in questa colonna. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituisce **NULL** per questa colonna.|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**||Numero ordinale della colonna. Le colonne vengono numerate a partire da 1. **NULL** se è presente alcun valore ordinale stabile per la colonna.|  
|**COLUMN_HASDEFAULT**|**DBTYPE_BOOL**||Valore booleano che indica se questa colonna dispone di un valore predefinito.<br /><br /> **TRUE** se la colonna contiene un valore predefinito.<br /><br /> **FALSE** se la colonna non ha un valore predefinito o se è noto se la colonna ha un valore predefinito.|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**||Valore predefinito della colonna. Un provider può esporre **DBCOLUMN_DEFAULTVALUE** ma non **DBCOLUMN_HASDEFAULT** (per le tabelle ISO) nel set di righe restituito da **IColumnsRowset::**.<br /><br /> Se il valore predefinito è **NULL**, **COLUMN_HASDEFAULT** è **TRUE** e **COLUMN_DEFAULT** colonna è un **NULL** valore.|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**||Maschera di bit che descrive le caratteristiche della colonna. Il **DBCOLUMNFLAGS** tipo enumerato specifica i bit nella maschera di bit. Questa colonna non può contenere un **NULL** valore. I valori validi includono:<br /><br /> **DBCOLUMNFLAGS_ISNULLABLE** (**0x20**)<br /><br /> **DBCOLUMNFLAGS_MAYBENULL** (**0x40**)<br /><br /> **DBCOLUMNFLAGS_ISLONG** (**0x80**)|  
|**IS_NULLABLE**|**DBTYPE_BOOL**||Valore booleano che indica se questa colonna dispone di un valore predefinito.<br /><br /> **TRUE** se la colonna può contenere **NULL**; **FALSE**, in caso contrario.|  
|**DATA_TYPE**|**DBTYPE_UI2**||Indicatore del tipo di dati della colonna. Esempio:<br /><br /> "**TABELLA**" = **DBTYPE_HCHAPTER**<br /><br /> "**TESTO**" = **DBTYPE_WCHAR**<br /><br /> "**LUNGO**" = **DBTYPE_I8**<br /><br /> "**DOPPIE**" = **DBTYPE_R8**<br /><br /> "**DATA**" = **DBTYPE_DATE**|  
|**TYPE_GUID**|**DBTYPE_GUID**||GUID del tipo di dati della colonna. I provider che non utilizzano GUID per identificare i tipi di dati restituiscono **NULL** in questa colonna.|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**||Lunghezza massima possibile di un valore nella colonna. Per le colonne di tipo carattere, binario o bit, i valori possibili sono i seguenti:<br /><br /> Lunghezza massima della colonna in caratteri, byte o bit, rispettivamente, se la lunghezza è definita. Ad esempio, una colonna `CHAR(5)` in una tabella SQL dispone di una lunghezza massima di 5.<br /><br /> Lunghezza massima del tipo di dati in caratteri, byte o bit, rispettivamente, se la colonna non dispone di una lunghezza definita.<br /><br /> È zero (0) se né la colonna né il tipo di dati dispongono di una lunghezza massima definita.<br /><br /> **NULL** per tutti gli altri tipi di colonne.|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**||Lunghezza massima in ottetti (byte) della colonna, se la colonna è di tipo carattere o binario. Un valore pari a zero (0) indica che la colonna non dispone di una lunghezza massima. **NULL** per tutti gli altri tipi di colonne.|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||La precisione massima della colonna se il tipo di dati della colonna è diverso da un tipo di dati numerici **VARNUMERIC**; **NULL** se il tipo di dati della colonna non è numerico oppure è **VARNUMERIC**.<br /><br /> La precisione delle colonne con tipo di dati **DBTYPE_DECIMAL** o **DBTYPE_NUM**ERIC dipende dalla definizione della colonna.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||Il numero di cifre a destra del separatore decimale se l'indicatore del tipo della colonna è **DBTYPE_DECIMAL**, **DBTYPE_NUMERIC**, o **DBTYPE_VARNUMERIC**. In caso contrario, si tratta **NULL**.|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**||Precisione di Datetime, ovvero numero di cifre nella parte relativa ai secondi frazionari, della colonna se la colonna e di tipo datetime o intervallo. Se il tipo di dati della colonna non è di tipo datetime, si tratta **NULL**.|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**||Nome del catalogo in cui è definito il set di caratteri. **NULL** se il provider non supporta cataloghi o set di caratteri diversi.|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**||Nome dello schema non qualificato in cui è definito il set di caratteri. **NULL** se il provider non supporta schemi o set di caratteri diversi.|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**||Nome del set di caratteri. **NULL** se il provider non supporta set di caratteri diversi.|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**||Nome del catalogo in cui sono definite le regole di confronto. **NULL** se il provider non supporta cataloghi o regole di confronto diverse.|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**||Nome dello schema non qualificato in cui sono definite le regole di confronto. **NULL** se il provider non supporta schemi o regole di confronto diverse.|  
|**COLLATION_NAME**|**DBTYPE_WSTR**||Nome delle regole di confronto. **NULL** se il provider non supporta regole di confronto diverse.|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**||Nome del catalogo in cui è definito il dominio. **NULL** se il provider non supporta cataloghi o domini.|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**||Nome dello schema non qualificato in cui è definito il dominio. **NULL** se il provider non supporta schemi o domini.|  
|**NOME_DOMINIO**|**DBTYPE_WSTR**||Nome del dominio. **NULL** se il provider non supporta i domini.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione leggibile della colonna. **NULL** se non vi è alcuna descrizione associata alla colonna.|  
|**DISTRIBUTION_FLAG**|**DBTYPE_WSTR**||Distribuzione della colonna della struttura di data mining:<br /><br /> "**NORMALE**"<br /><br /> "**LOG_NORM**AL"<br /><br /> "**UNIFORM**"|  
|**CONTENT_TYPE**|**DBTYPE_WSTR**||Tipo di contenuto della colonna della struttura di data mining:<br /><br /> "**CHIAVE**"<br /><br /> "**DISCRETE**"<br /><br /> "**CONTINUO**"<br /><br /> "**DISCRETIZED (**[argomenti]**)**"<br /><br /> "**ORDERED**"<br /><br /> "**SEQUENCE_TIME**"<br /><br /> "**CYCLICAL**"<br /><br /> "**PROBABILITÀ**"<br /><br /> "**VARIANZA**"<br /><br /> "**STDEV**"<br /><br /> "**SUPPORTO**"<br /><br /> "**PROBABILITY_VARIANCE**"<br /><br /> "**PROBABILITY_STDEV**"|  
|**MODELING_FLAG**|**DBTYPE_WSTR**||Elenco delimitato da virgole di flag di modellazione. L'unico flag di modellazione per una colonna della struttura è "**non NULL**".|  
|**IS_RELATED_TO_KEY**|**DBTYPE_BOOL**||Valore booleano che indica se questa colonna è correlata alla chiave.<br /><br /> **VARIANT_TRUE** se questa colonna è correlata alla chiave; **VARIANT_FALSE** in caso contrario. Se la chiave è una singola colonna, il **RELATED_ATTRIBUTE** campo può contenere facoltativamente il nome della colonna.|  
|**RELATED_ATTRIBUTE**|**DBTYPE_WSTR**||Nome della colonna di destinazione a cui è correlata la colonna corrente o che corrisponde a una proprietà speciale.|  
|**CONTAINING_COLUMN**|**DBTYPE_WSTR**||Il nome del **tabella** colonna contenente questa colonna. **NULL** se nessuna tabella contiene la colonna.|  
|**IS_POPULATED**|**DBTYPE_BOOL**||Valore booleano che indica se questa colonna ha appreso un set di valori possibili.<br /><br /> **TRUE** se la colonna ha appreso un set di valori possibili. **FALSE**, in caso contrario.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_STRUCTURE_COLUMNS** set di righe può essere limitato sulle colonne nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**|Facoltativa.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**|Facoltativa.|  
|**NOME_STRUTTURA**|**DBTYPE_WSTR**|Facoltativa.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Data Mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

