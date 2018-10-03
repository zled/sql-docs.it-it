---
title: Set di righe MDSCHEMA_MEASURES | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_MEASURES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASURES rowset
ms.assetid: 6ff5bd1a-aad0-49b8-9f8d-7df2637caacf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f421e3ebd93af0eb5fe175c0d94d28ab8509289
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094271"
---
# <a name="mdschemameasures-rowset"></a>Set di righe MDSCHEMA_MEASURES
  Descrive ogni misura all'interno di un cubo.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_MEASURES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del catalogo a cui appartiene questa misura. `NULL` se il provider non supporta i cataloghi.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nome dello schema a cui appartiene questa misura. `NULL` se il provider non supporta gli schemi.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo a cui appartiene questa misura.|  
|`MEASURE_NAME`|`DBTYPE_WSTR`||Nome della misura.|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della misura. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|`MEASURE_CAPTION`|`DBTYPE_WSTR`||Etichetta o didascalia associata alla misura. Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, viene restituito `MEASURE_NAME`.|  
|`MEASURE_GUID`|`DBTYPE_GUID`||Non supportato.|  
|`MEASURE_AGGREGATOR`|`DBTYPE_I4`||Enumerazione tramite cui viene identificata la modalità di derivazione di una misura. I possibili valori sono i seguenti:<br /><br /> -   `MDMEASURE_AGGR_SUM` (`1`) indicato che la misura viene aggregata da `SUM`.<br />-   `MDMEASURE_AGGR_COUNT` (`2`) indicato che la misura viene aggregata da `COUNT`.<br />-   **MDMEASURE_AGGR_MIN** (`3`) indicato che la misura viene aggregata da `MIN`.<br />-   **MDMEASURE_AGGR_MAX** (`4`) indicato che la misura viene aggregata da `MAX`.<br />-   `MDMEASURE_AGGR_AVG` (`5`) indicato che la misura viene aggregata da `AVG`.<br />-   `MDMEASURE_AGGR_VAR` (`6`) indicato che la misura viene aggregata da `VAR`.<br />-   `MDMEASURE_AGGR_STD` (`7`) indicato che la misura viene aggregata da `STDEV`.<br />-   `MDMEASURE_AGGR_DST` (`8`) indicato che la misura viene aggregata da `DISTINCT COUNT`.<br />-   `MDMEASURE_AGGR_NONE` (`9`) indicato che la misura viene aggregata da `NONE`.<br />-   `MDMEASURE_AGGR_AVGCHILDREN` (`10`) indicato che la misura viene aggregata da `AVERAGEOFCHILDREN`.<br />-   `MDMEASURE_AGGR_FIRSTCHILD` (`11`) indicato che la misura viene aggregata da `FIRSTCHILD`.<br />-   `MDMEASURE_AGGR_LASTCHILD` (`12`) indicato che la misura viene aggregata da `LASTCHILD`.<br />-   `MDMEASURE_AGGR_FIRSTNONEMPTY` (`13`) indicato che la misura viene aggregata da `FIRSTNONEMPTY`,<br />-   `MDMEASURE_AGGR_LASTNONEMPTY` (`14`) indicato che la misura viene aggregata da `LASTNONEMPTY`.<br />-   `MDMEASURE_AGGR_BYACCOUNT` (`15`) indicato che la misura viene aggregata da `BYACCOUNT`.<br />-   `MDMEASURE_AGGR_CALCULATED` (`127`) indica che la misura è stata derivata da una formula che non era parte delle funzioni precedenti.<br />-   `MDMEASURE_AGGR_UNKNOWN` (`0`) indica che la misura è stata derivata da una funzione di aggregazione sconosciuto o una formula.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Tipo di dati della misura.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Precisione massima della proprietà se il tipo di dati dell'oggetto misura è un valore numerico esatto. `NULL` per tutti gli altri tipi di proprietà.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Numero di cifre a destra del separatore decimale se l'indicatore del tipo di oggetto misura è `DBTYPE_NUMERIC` o `DBTYPE_DECIMAL`. In caso contrario il valore è `NULL`.|  
|`MEASURE_UNITS`|`DBTYPE_WSTR`||Non supportato|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione leggibile della misura. `NULL` se non sono presenti descrizioni.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Espressione per il membro.|  
|`MEASURE_IS_VISIBLE`|`DBTYPE_BOOL`||Valore booleano che restituisce sempre True. Se la misura non è visibile, non verrà inclusa nel set di righe dello schema.|  
|`LEVELS_LIST`|`DBTYPE_WSTR`||Stringa che restituisce sempre `NULL`.|  
|`MEASURE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Nome della colonna nella query SQL che corrisponde al nome della misura.|  
|`MEASURE_UNQUALIFIED_CAPTION`|`DBTYPE_WSTR`||Nome della misura, non qualificato con il nome del gruppo di misure.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Nome del gruppo di misure a cui appartiene la misura.|  
|`MEASURE_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Il percorso da utilizzare durante la visualizzazione della misura nell'interfaccia utente. I nomi delle cartelle saranno separati da un punto e virgola. Le cartelle nidificate sono indicate da una barra rovesciata (\\).|  
|`DEFAULT_FORMAT_STRING`|`DBTYPE_WSTR`||La stringa di formato predefinita per la misura.|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME` e `MEASURE_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_MEASURES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEASURE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -1 CUBO<br />-DIMENSIONE DI 2<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
|`MEASURE_VISIBILITY`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -Visible 1<br />-2 non visibile<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
