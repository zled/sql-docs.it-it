---
title: Set di righe DMSCHEMA_MINING_STRUCTURE_COLUMNS | Microsoft Docs
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
- DMSCHEMA_MINING_STRUCTURE_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURE_COLUMNS rowset
ms.assetid: 81f25502-ac90-42f1-8ddf-7b0f9752ebfd
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c98da6f1e843b08fac4b91baabec79ab0d9c341
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171582"
---
# <a name="dmschemaminingstructurecolumns-rowset"></a>Set di righe DMSCHEMA_MINING_STRUCTURE_COLUMNS
  Descrive le singole colonne di tutte le strutture di data mining distribuite in un server che esegue [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_STRUCTURE_COLUMNS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non supporta schemi, pertanto questa colonna è sempre `NULL`.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`||Nome della struttura. Questa colonna non può contenere un valore `NULL`.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Nome della colonna. L'univocità è garantita solo nelle colonne che condividono lo stesso modello. Ad esempio, due colonne nidificate possono avere lo stesso nome se appartengono a due tabelle nidificate diverse all'interno della stessa struttura.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||GUID della colonna. I provider che non utilizzano GUID per identificare le colonne restituiscono un valore `NULL` in questa colonna.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||ID di proprietà della colonna. I provider che non associano ID di proprietà alle colonne restituiscono un valore `NULL` in questa colonna. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Restituisce `NULL` per questa colonna.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Numero ordinale della colonna. Le colonne vengono numerate a partire da 1. `NULL` se non è presente alcun valore ordinale stabile per la colonna.|  
|`COLUMN_HASDEFAULT`|`DBTYPE_BOOL`||Valore booleano che indica se questa colonna dispone di un valore predefinito.<br /><br /> È `TRUE` se la colonna dispone di un valore predefinito.<br /><br /> È `FALSE` se la colonna non dispone di un valore predefinito o se non è possibile determinare se la colonna dispone di un valore predefinito.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Valore predefinito della colonna. Un provider può esporre `DBCOLUMN_DEFAULTVALUE` ma non `DBCOLUMN_HASDEFAULT` (per le tabelle ISO) nel set di righe restituito da `IColumnsRowset::GetColumnsRowset`.<br /><br /> Se il valore predefinito è `NULL`, `COLUMN_HASDEFAULT` è `TRUE` e il valore della colonna `COLUMN_DEFAULT` è `NULL`.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||-Una maschera di bit che descrive le caratteristiche della colonna. Il tipo enumerato `DBCOLUMNFLAGS` specifica i bit nella maschera di bit. Questa colonna non può contenere un valore `NULL`. I valori validi includono:<br />-   **DBCOLUMNFLAGS_ISNULLABLE** (`0x20`)<br />-   **DBCOLUMNFLAGS_MAYBENULL** (`0x40`)<br />-   **DBCOLUMNFLAGS_ISLONG** (`0x80`)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Valore booleano che indica se questa colonna dispone di un valore predefinito.<br /><br /> È `TRUE` se la colonna può contenere `NULL`. In caso contrario è `FALSE`.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Indicatore del tipo di dati della colonna. Esempio:<br /><br /> -   "`TABLE`" = `DBTYPE_HCHAPTER`<br />-   "`TEXT`" = `DBTYPE_WCHAR`<br />-   "`LONG`" = `DBTYPE_I8`<br />-   "`DOUBLE`" = `DBTYPE_R8`<br />-   "`DATE`" = `DBTYPE_DATE`|  
|`TYPE_GUID`|`DBTYPE_GUID`||GUID del tipo di dati della colonna. I provider che non utilizzano GUID per identificare i tipi di dati restituiscono un valore `NULL` in questa colonna.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Lunghezza massima possibile di un valore nella colonna. Per le colonne di tipo carattere, binario o bit, i valori possibili sono i seguenti:<br /><br /> -La lunghezza massima della colonna in caratteri, byte o bit, rispettivamente, se la lunghezza è definita. Ad esempio, una colonna `CHAR(5)` in una tabella SQL dispone di una lunghezza massima di 5.<br />-La lunghezza massima dei dati digitare caratteri, byte o bit, rispettivamente, se la colonna non ha una lunghezza definita.<br />-Zero (0) se la colonna né il tipo di dati ha una lunghezza massima definita.<br />-   `NULL` per tutti gli altri tipi di colonne.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Lunghezza massima in ottetti (byte) della colonna, se la colonna è di tipo carattere o binario. Un valore pari a zero (0) indica che la colonna non dispone di una lunghezza massima. È `NULL` per tutti gli altri tipi di colonne.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||La precisione massima della colonna se il tipo di dati della colonna è un tipo di dati numerico diverso da `VARNUMERIC`. È `NULL` se il tipo di dati della colonna non è numerico oppure è `VARNUMERIC`.<br /><br /> La precisione delle colonne con un tipo di dati `DBTYPE_DECIMAL` o `DBTYPE_NUM`ERIC dipende dalla definizione della colonna.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Numero di cifre a destra del separatore decimale se l'indicatore del tipo di colonna è `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC` o `DBTYPE_VARNUMERIC`. In caso contrario è `NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Precisione di Datetime, ovvero numero di cifre nella parte relativa ai secondi frazionari, della colonna se la colonna e di tipo datetime o intervallo. È `NULL` se il tipo di dati della colonna non è datetime.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo in cui è definito il set di caratteri. `NULL` se il provider non supporta i cataloghi o diversi set di caratteri.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato in cui è definito il set di caratteri. `NULL` se il provider non supporta schemi o set di caratteri diversi.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Nome del set di caratteri. `NULL` se il provider non supporta set di caratteri diversi.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo in cui sono definite le regole di confronto. `NULL` se il provider non supporta cataloghi o regole di confronto diverse.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato in cui sono definite le regole di confronto. `NULL` se il provider non supporta schemi o regole di confronto diverse.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Nome delle regole di confronto. `NULL` se il provider non supporta regole di confronto diverse.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo in cui è definito il dominio. `NULL` se il provider non supporta cataloghi o domini.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato in cui è definito il dominio. `NULL` se il provider non supporta schemi o domini.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Nome del dominio. `NULL` se il provider non supporta domini.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione leggibile della colonna. `NULL` se non esiste alcuna descrizione associata alla colonna.|  
|`DISTRIBUTION_FLAG`|`DBTYPE_WSTR`||Distribuzione della colonna della struttura di data mining:<br /><br /> -   "`NORMAL`"<br />-"`LOG_NORM`AL"<br />-   "`UNIFORM`"|  
|`CONTENT_TYPE`|`DBTYPE_WSTR`||Tipo di contenuto della colonna della struttura di data mining:<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-"`DISCRETIZED(`[argomenti]`)`"<br />-   "`ORDERED`"<br />-   "`SEQUENCE_TIME`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY_VARIANCE`"<br />-   "`PROBABILITY_STDEV`"|  
|`MODELING_FLAG`|`DBTYPE_WSTR`||Elenco delimitato da virgole di flag di modellazione. L'unico flag di modellazione per una colonna struttura è "`NOT NULL`".|  
|`IS_RELATED_TO_KEY`|`DBTYPE_BOOL`||Valore booleano che indica se questa colonna è correlata alla chiave.<br /><br /> È `VARIANT_TRUE` se la colonna è correlata alla chiave. In caso contrario è `VARIANT_FALSE`. Se la chiave è costituita da un'unica colonna, il campo `RELATED_ATTRIBUTE` può contenere il nome della colonna corrispondente.|  
|`RELATED_ATTRIBUTE`|`DBTYPE_WSTR`||Nome della colonna di destinazione a cui è correlata la colonna corrente o che corrisponde a una proprietà speciale.|  
|`CONTAINING_COLUMN`|`DBTYPE_WSTR`||Il nome della colonna `TABLE` che contiene tale colonna. `NULL` se nessuna tabella contiene la colonna.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Valore booleano che indica se questa colonna ha appreso un set di valori possibili.<br /><br /> È `TRUE` se la colonna ha appreso un set di valori possibili. In caso contrario è `FALSE`.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DMSCHEMA_MINING_STRUCTURE_COLUMNS` può essere limitato nelle colonne della tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`|Facoltativo.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`|Facoltativo.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
