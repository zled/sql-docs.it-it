---
title: Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS | Microsoft Docs
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
- MDSCHEMA_MEASUREGROUP_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS rowset
ms.assetid: c731c06a-7382-4e50-ba0e-d8cee3ab4f28
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ae41cad794f31443dfa2fbfc2951f0b611d5766
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308451"
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS
  Enumera le dimensioni dei gruppi di misure.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_MEASUREGROUP_DIMENSIONS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del catalogo a cui appartiene questo gruppo di misure. `NULL` se il provider non supporta i cataloghi.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo a cui appartiene questo gruppo di misure.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Nome del gruppo di misure.|  
|`MEASUREGROUP_CARDINALITY`|`DBTYPE_WSTR`||Numero di istanze di cui una misura nel gruppo di misure può disporre per un singolo membro di dimensione. I valori possibili includono:<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco per la dimensione.|  
|`DIMENSION_CARDINALITY`|`DBTYPE_WSTR`||Numero di istanze di cui un membro di dimensione può disporre per una singola istanza di una misura del gruppo di misure.<br /><br /> I valori possibili includono:<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Valore booleano che indica se le gerarchie nella dimensione sono visibili.<br /><br /> Restituisce `TRUE` se sono visibili una o più gerarchie nella dimensione; in caso contrario `FALSE`.|  
|`DIMENSION_IS_FACT_DIMENSION`|`DBTYPE_BOOL`||Valore booleano che indica se la dimensione è una dimensione dei fatti.<br /><br /> Restituisce `TRUE` se la dimensione è una dimensione dei fatti; in caso contrario `FALSE`.|  
|`DIMENSION_PATH`|`DBTYPE_HCHAPTER`||Elenco di dimensioni per la dimensione di riferimento.|  
|`DIMENSION_GRANULARITY`|`DBTYPE_WSTR`||Nome univoco della gerarchia di granularità.|  
  
 Il set di righe supporta l'ordinamento in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `MEASUREGROUP_NAME`, `DIMENSION_UNIQUE_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_MEASUREGROUP_DIMENSIONS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -Visible 1<br />-2 non visibile<br />-Restrizione predefinita è un valore pari a 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
