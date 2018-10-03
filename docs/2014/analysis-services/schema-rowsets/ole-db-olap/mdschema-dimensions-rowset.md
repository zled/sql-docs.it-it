---
title: Set di righe MDSCHEMA_DIMENSIONS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_DIMENSIONS rowset
ms.assetid: a0fd94bb-359a-4df6-93a6-d60d50223944
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 49cd8f4f01840b67cde31d9031320ac276ec6faa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152635"
---
# <a name="mdschemadimensions-rowset"></a>Set di righe MDSCHEMA_DIMENSIONS
  Descrive le dimensioni condivise e private all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe `MDSCHEMA_DIMENSIONS` contiene le colonne seguenti:  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del database.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nome della dimensione. Se una dimensione appartiene a più cubi o a più gruppi di misure, sarà presente una riga per ogni combinazione univoca di dimensione, gruppo di misure e cubo.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della dimensione.|  
|`DIMENSION_GUID`|`DBTYPE_GUID`||Non supportato.|  
|`DIMENSION_CAPTION`|`DBTYPE_WSTR`||Didascalia della dimensione. Deve essere utilizzata durante la visualizzazione del nome della dimensione, ad esempio nell'interfaccia utente o in report.|  
|`DIMENSION_ORDINAL`|`DBTYPE_UI4`||Posizione della dimensione all'interno del cubo.|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||Tipo della dimensione. I valori validi includono:<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`DIMENSION_CARDINALITY`|`DBTYPE_UI4`||Numero di membri nell'attributo chiave.|  
|`DEFAULT_HIERARCHY`|`DBTYPE_WSTR`||Gerarchia della dimensione. Mantenuta per compatibilità con le versioni precedenti.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione semplice della dimensione.|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||Sempre `FALSE`.|  
|`IS_READWRITE`|`DBTYPE_BOOL`||Valore booleano che indica se una dimensione è abilitata per la scrittura.<br /><br /> `TRUE` se la dimensione è abilitata per la scrittura.|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||Bitmap che specifica quali colonne contengono valori univoci, se la dimensione contiene solo membri con nomi univoci. Le costanti del valore bit seguenti sono definite in Msmd.h per questa bitmap:<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE`|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Sempre `NULL`.|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Sempre `TRUE`. **Nota:** una dimensione non è visibile a meno che non sono visibili una o più gerarchie nella dimensione.|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME` e `DIMENSION_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_DIMENSIONS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -1 CUBO<br />-DIMENSIONE DI 2<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -Visible 1<br />-2 non visibile<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
