---
title: Set di righe MDSCHEMA_PROPERTIES | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_PROPERTIES rowset
ms.assetid: 95c480f7-c525-44ba-a59b-cd36f5855a4f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17395bb081006e46b052bdaf8da2166b0366d686
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100131"
---
# <a name="mdschemaproperties-rowset"></a>Set di righe MDSCHEMA_PROPERTIES
  Descrive le proprietà dei membri all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_PROPERTIES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del database.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nome dello schema a cui appartiene la proprietà. `NULL` se il provider non supporta gli schemi.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della dimensione. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della gerarchia. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco del livello a cui appartiene questa proprietà. Se il provider non supporta i livelli denominati, deve restituire il valore `DIMENSION_UNIQUE_NAME` per questo campo. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco del membro a cui appartiene la proprietà. Utilizzato per archivi dati che non supportano i livelli denominati o le cui proprietà sono impostate membro per membro. Se la proprietà viene applicata a tutti i membri in un livello, questa colonna è `NULL`. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|`PROPERTY_TYPE`|`DBTYPE_I2`||Bitmap che specifica il tipo della proprietà:<br /><br /> -   `MDPROP_MEMBER` (`1`) identifica una proprietà di un membro. Questa proprietà può essere utilizzata nella clausola DIMENSION PROPERTIES dell'istruzione SELECT.<br />-   `MDPROP_CELL` (`2`) identifica una proprietà di una cella. Questa proprietà può essere utilizzata nella clausola CELL PROPERTIES alla fine dell'istruzione SELECT.<br />-   `MDPROP_SYSTEM` (`4`) identifica una proprietà interna.<br />-   `MDPROP_BLOB` (`8`) identifica una proprietà che contiene un oggetto binario di grandi dimensioni (blob).|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`||Nome della proprietà. Se la chiave della proprietà è uguale al nome della proprietà, `PROPERTY_NAME` sarà vuoto.|  
|`PROPERTY_CAPTION`|`DBTYPE_WSTR`||Etichetta o didascalia associata alla proprietà, utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, verrà restituito `PROPERTY_NAME`.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Tipo di dati della proprietà.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Lunghezza massima possibile della proprietà, se è di tipo carattere, binario o bit.<br /><br /> Il valore zero indica l'assenza di una lunghezza massima definita.<br /><br /> Per tutti gli altri tipi di dati verrà restituito `NULL`.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Lunghezza massima possibile (in byte) della proprietà, se è di tipo carattere o binario.<br /><br /> Il valore zero indica l'assenza di una lunghezza massima definita.<br /><br /> Per tutti gli altri tipi di dati verrà restituito `NULL`.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Precisione massima della proprietà, se si tratta di un tipo di dati numerico.<br /><br /> Per tutti gli altri tipi di dati verrà restituito `NULL`.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Il numero di cifre a destra del separatore decimale, se è di tipo `DBTYPE_NUMERIC` o `DBTYPE_DECIMAL`.<br /><br /> Per tutti gli altri tipi di dati verrà restituito `NULL`.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Una descrizione leggibile della proprietà. `NULL` se non sono presenti descrizioni.|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`||Tipo della proprietà. Può essere una delle enumerazioni seguenti:<br /><br /> -   **MD_PROPTYPE_REGULAR** (`0x00`)<br />-   **MD_PROPTYPE_ID** (`0x01`)<br />-   **MD_PROPTYPE_RELATION_TO_PARENT** (`0x02`)<br />-   **MD_PROPTYPE_ROLLUP_OPERATOR** (`0x03`)<br />-   **MD_PROPTYPE_ORG_TITLE** (`0x11`)<br />-   **MD_PROPTYPE_CAPTION** (`0x21`)<br />-   **MD_PROPTYPE_CAPTION_SHORT** (`0x22`)<br />-   **MD_PROPTYPE_CAPTION_DESCRIPTION** (`0x23`)<br />-   **MD_PROPTYPE_CAPTION_ABREVIATION** (`0x24`)<br />-   **MD_PROPTYPE_WEB_URL** (`0x31`)<br />-   **MD_PROPTYPE_WEB_HTML** (`0x32`)<br />-   **MD_PROPTYPE_WEB_XML_OR_XSL** (`0x33`)<br />-   **MD_PROPTYPE_WEB_MAIL_ALIAS** (`0x34`)<br />-   **MD_PROPTYPE_ADDRESS** (`0x41`)<br />-   **MD_PROPTYPE_ADDRESS_STREET** (`0x42`)<br />-   **MD_PROPTYPE_ADDRESS_HOUSE** (`0x43`)<br />-   **MD_PROPTYPE_ADDRESS_CITY** (`0x44`)<br />-   **MD_PROPTYPE_ADDRESS_STATE_OR_PROVINCE** (`0x45`)<br />-   **MD_PROPTYPE_ADDRESS_ZIP** (`0x46`)<br />-   **MD_PROPTYPE_ADDRESS_QUARTER** (`0x47`)<br />-   **MD_PROPTYPE_ADDRESS_COUNTRY** (`0x48`)<br />-   **MD_PROPTYPE_ADDRESS_BUILDING** (`0x49`)<br />-   **MD_PROPTYPE_ADDRESS_ROOM** (`0x4A`)<br />-   **MD_PROPTYPE_ADDRESS_FLOOR** (`0x4B`)<br />-   **MD_PROPTYPE_ADDRESS_FAX** (`0x4C`)<br />-   **MD_PROPTYPE_ADDRESS_PHONE** (`0x4D`)<br />-   **MD_PROPTYPE_GEO_CENTROID_X** (`0x61`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Y** (`0x62`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Z** (`0x63`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_TOP** (`0x64`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_LEFT** (`0x65`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_BOTTOM** (`0x66`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_RIGHT** (`0x67`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_FRONT** (`0x68`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_REAR** (`0x69`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_POLYGON** (`0x6A`)<br />-   **MD_PROPTYPE_PHYSICAL_SIZE** (`0x71`)<br />-   **MD_PROPTYPE_PHYSICAL_COLOR** (`0x72`)<br />-   **MD_PROPTYPE_PHYSICAL_WEIGHT** (`0x73`)<br />-   **MD_PROPTYPE_PHYSICAL_HEIGHT** (`0x74`)<br />-   **MD_PROPTYPE_PHYSICAL_WIDTH** (`0x75`)<br />-   **MD_PROPTYPE_PHYSICAL_DEPTH** (`0x76`)<br />-   **MD_PROPTYPE_PHYSICAL_VOLUME** (`0x77`)<br />-   **MD_PROPTYPE_PHYSICAL_DENSITY** (`0x78`)<br />-   **MD_PROPTYPE_PERSON_FULL_NAME** (`0x82`)<br />-   **MD_PROPTYPE_PERSON_FIRST_NAME** (`0x83`)<br />-   **MD_PROPTYPE_PERSON_LAST_NAME** (`0x84`)<br />-   **MD_PROPTYPE_PERSON_MIDDLE_NAME** (`0x85`)<br />-   **MD_PROPTYPE_PERSON_DEMOGRAPHIC** (`0x86`)<br />-   **MD_PROPTYPE_PERSON_CONTACT** (`0x87`)<br />-   **MD_PROPTYPE_QTY_RANGE_LOW** (`0x91`)<br />-   **MD_PROPTYPE_QTY_RANGE_HIGH** (`0x92`)<br />-   **MD_PROPTYPE_FORMATTING_COLOR** (`0xA1`)<br />-   **MD_PROPTYPE_FORMATTING_ORDER** (`0xA2`)<br />-   **MD_PROPTYPE_FORMATTING_FONT** (`0xA3`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_EFFECTS** (`0xA4`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_SIZE** (`0xA5`)<br />-   **MD_PROPTYPE_FORMATTING_SUB_TOTAL** (`0xA6`)<br />-   **MD_PROPTYPE_DATE** (`0xB1`)<br />-   **MD_PROPTYPE_DATE_START** (`0xB2`)<br />-   **MD_PROPTYPE_DATE_ENDED** (`0xB3`)<br />-   **MD_PROPTYPE_DATE_CANCELED** (`0xB4`)<br />-   **MD_PROPTYPE_DATE_MODIFIED** (`0xB5`)<br />-   **MD_PROPTYPE_DATE_DURATION** (`0xB6`)<br />-   **MD_PROPTYPE_VERSION** (`0xC1`)|  
|`SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Nome della proprietà utilizzato nelle query SQL dalla dimensione del cubo o del database.|  
|`LANGUAGE`|`DBTYPE_UI2`||Traduzione espressa come `LCID`. Valida solo per le traduzioni delle proprietà.|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`||Identifica il tipo di gerarchia a cui viene applicata la proprietà:<br /><br /> -   `MD_USER_DEFINED` (`1`) indica la proprietà si trova in una gerarchia definita dall'utente<br />-   `MD_SYSTEM_ENABLED` (`2`) indica la proprietà si trova in una gerarchia dell'attributo<br />-   `MD_SYSTEM_DISABLED` (`4`) indica la proprietà si trova in una gerarchia dell'attributo che non è abilitata.|  
|`PROPERTY_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||Nome della gerarchia dell'attributo di origine di questa proprietà.|  
|`PROPERTY_CARDINALITY`|`DBTYPE_WSTR`||Cardinalità della proprietà. I valori possibili includono le seguenti stringhe:<br /><br /> -   `ONE`<br />-   `MANY`|  
|`MIME_TYPE`|`DBTYPE_WSTR`||Tipo MIME per i BLOB (Binary Large Object).|  
|`PROPERTY_IS_VISIBLE`|`DBTYPE_BOOL`||Valore booleano che indica se la proprietà è visibile.<br /><br /> `TRUE` se la proprietà è visibile; in caso contrario, `FALSE`.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_PROPERTIES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Obbligatorio|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`PROPERTY_TYPE`|`DBTYPE_I2`|Facoltativo|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`|(Facoltativo) Una restrizione predefinita è attiva su `MDPROP_MEMBER` O `MDPROP_CELL`.|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`|(Facoltativo) Una restrizione predefinita è attiva su `MD_USER_DEFINED` O `MD_SYSTEM_ENABLED`.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -1 CUBO<br />-DIMENSIONE DI 2<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
|`PROPERTY_VISIBILITY`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -Visible 1<br />-2 non visibile<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
