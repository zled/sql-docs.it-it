---
title: Set di righe MDSCHEMA_LEVELS | Documenti Microsoft
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
- MDSCHEMA_LEVELS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_LEVELS rowset
ms.assetid: 4313e268-33f4-4e99-96d7-2ec26775c580
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 51aced8c191943330b6df9f08fc65292b1a77d81
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067898"
---
# <a name="mdschemalevels-rowset"></a>Set di righe MDSCHEMA_LEVELS
  Descrive ogni livello all'interno di una determinata gerarchia.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_LEVELS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del catalogo a cui appartiene il livello. `NULL` se il provider non supporta i cataloghi.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nome dello schema a cui appartiene il livello. `NULL` se il provider non supporta gli schemi.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo a cui appartiene questo livello.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della dimensione a cui appartiene questo livello. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della gerarchia. Se il livello appartiene a più di una gerarchia, è presente una riga per ogni gerarchia a cui appartiene. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|`LEVEL_NAME`|`DBTYPE_WSTR`||Nome del livello.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco del livello correttamente preceduto da un carattere di escape.|  
|`LEVEL_GUID`|`DBTYPE_GUID`||Non supportato.|  
|`LEVEL_CAPTION`|`DBTYPE_WSTR`||Etichetta o didascalia associata alla gerarchia. Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, viene restituito `LEVEL_NAME`.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||Distanza del livello dalla radice della gerarchia. Il livello radice è zero (`0)`.|  
|`LEVEL_CARDINALITY`|`DBTYPE_UI4`||Numero di membri nel livello.|  
|`LEVEL_TYPE`|`DBTYPE_I4`||Tipo del livello:<br /><br /> -   `MDLEVEL_TYPE_GEO_CONTINENT` (`0x2001`)<br />-   `MDLEVEL_TYPE_GEO_REGION` (`0x2002`)<br />-   `MDLEVEL_TYPE_GEO_COUNTRY` (`0x2003`)<br />-   `MDLEVEL_TYPE_GEO_STATE_OR_PROVINCE` (`0x2004`)<br />-   `MDLEVEL_TYPE_GEO_COUNTY` (`0x2005`)<br />-   `MDLEVEL_TYPE_GEO_CITY` (`0x2006`)<br />-   `MDLEVEL_TYPE_GEO_POSTALCODE` (`0x2007`)<br />-   `MDLEVEL_TYPE_GEO_POINT` (`0x2008`)<br />-   `MDLEVEL_TYPE_ORG_UNIT` (`0x1011`)<br />-   `MDLEVEL_TYPE_BOM_RESOURCE` (`0x1012`)<br />-   **MDLEVEL_TYPE_QUANTITATIVE** (`0x1013`)<br />-   `MDLEVEL_TYPE_ACCOUNT` (`0x1014`)<br />-   `MDLEVEL_TYPE_CUSTOMER` (`0x1021`)<br />-   `MDLEVEL_TYPE_CUSTOMER_GROUP` (`0x1022`)<br />-   `MDLEVEL_TYPE_CUSTOMER_HOUSEHOLD` (`0x1023`)<br />-   `MDLEVEL_TYPE_PRODUCT` (`0x1031`)<br />-   `MDLEVEL_TYPE_PRODUCT_GROUP` (`0x1032`)<br />-   `MDLEVEL_TYPE_SCENARIO` (`0x1015`)<br />-   `MDLEVEL_TYPE_UTILITY` (`0x1016`)<br />-   `MDLEVEL_TYPE_PERSON` (`0x1041`)<br />-   `MDLEVEL_TYPE_COMPANY` (`0x1042`)<br />-   `MDLEVEL_TYPE_CURRENCY_SOURCE` (`0x1051`)<br />-   `MDLEVEL_TYPE_CURRENCY_DESTINATION` (`0x1052`)<br />-   `MDLEVEL_TYPE_CHANNEL` (`0x1061`)<br />-   `MDLEVEL_TYPE_REPRESENTATIVE` (`0x1062`)<br />-   `MDLEVEL_TYPE_PROMOTION` (`0x1071`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione leggibile del livello. NULL se non sono presenti descrizioni.|  
|`CUSTOM_ROLLUP_SETTINGS`|`DBTYPE_I4`||Bitmap che specifica le opzioni di rollup personalizzato:<br /><br /> -   `MDLEVELS_CUSTOM_ROLLUP_EXPRESSION` (`0x01`) indica la presenza di un'espressione per questo livello. (Deprecato)<br />-   `MDLEVELS_CUSTOM_ROLLUP_COLUMN` (`0x02`) indica che è presente una colonna di rollup personalizzato per questo livello.<br />-   `MDLEVELS_SKIPPED_LEVELS` (`0x04`) indica che è presente un livello ignorato associato con i membri di questo livello.<br />-   `MDLEVELS_CUSTOM_MEMBER_PROPERTIES` (`0x08`) indica che i membri del livello dispongono di proprietà personalizzate dei membri.<br />-   `MDLEVELS_UNARY_OPERATOR` (`0x10`) indica che i membri del livello dispongono di operatori unari.|  
|`LEVEL_UNIQUE_SETTINGS`|`DBTYPE_I4`||Bitmap che specifica quali colonne contengono valori univoci, se il livello dispone solo di membri con chiavi o nomi univoci. Nel file Msmd.h sono definite le seguenti costanti del valore bit per questa bitmap:<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`)<br />-   `MDDIMENSIONS_MEMBER_NAME_UNIQUE` (`2`)<br /><br /> La chiave è sempre univoca in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Il nome sarà univoco se l'impostazione dell'attributo è `UniqueInDimension` o `UniqueInAttribute`|  
|`LEVEL_IS_VISIBLE`|`DBTYPE_BOOL`||Valore booleano che indica se il livello è visibile.<br /><br /> Restituisce sempre True. Se il livello non è visibile, non verrà incluso nel set di righe dello schema.|  
|`LEVEL_ORDERING_PROPERTY`|`DBTYPE_WSTR`||ID dell'attributo in base a cui viene ordinato il livello.|  
|`LEVEL_DBTYPE`|`DBTYPE_I4`||L'enumerazione `DBTYPE` della colonna chiave del membro utilizzata per l'attributo del livello.<br /><br /> Null se le chiavi concatenate vengono utilizzate come colonna chiave del membro.|  
|`LEVEL_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Viene restituito sempre NULL.|  
|`LEVEL_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Rappresentazione SQL dei nomi del membro del livello.|  
|`LEVEL_KEY_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Rappresentazione SQL dei valori chiave del membro del livello.|  
|`LEVEL_UNIQUE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Rappresentazione SQL dei nomi univoci del membro.|  
|`LEVEL_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||Nome della gerarchia dell'attributo che fornisce l'origine del livello.|  
|`LEVEL_KEY_CARDINALITY`|`DBTYPE_UI2`||Numero di colonne nella chiave del livello.|  
|`LEVEL_ORIGIN`|`DBTYPE_UI2`||Bitmap che definisce come è stato originato il livello:<br /><br /> -   `MD_ORIGIN_USER_DEFINED` Identifica i livelli in una gerarchia definita dall'utente.<br />-   `MD_ORIGIN_ATTRIBUTE` Identifica i livelli in una gerarchia dell'attributo.<br />-   `MD_ORIGIN_KEY_ATTRIBUTE` Identifica i livelli in una gerarchia dell'attributo chiave.<br />-   `MD_ORIGIN_INTERNAL` Identifica i livelli nelle gerarchie di attributi che non sono abilitati.|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_UNIQUE_NAME`, `LEVEL_NUMBER`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_LEVELS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`LEVEL_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`LEVEL_ORIGIN`|`DBTYPE_UI2`|(Facoltativo) Una restrizione predefinita è attiva su `MD_USER_DEFINED` e `MD_SYSTEM_ENABLED`|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -1 CUBO<br />-QUOTA 2<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
|`LEVEL_VISIBILITY`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori:<br /><br /> -Visible 1<br />-2 non visibile<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  