---
title: Set di righe MDSCHEMA_CUBES | Microsoft Docs
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
- MDSCHEMA_CUBES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_CUBES rowset
ms.assetid: 5f1b63d4-aa3f-48c6-b866-7ffd91675044
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 441f83b4b5bec1a2340fbf6e8a3b14da77363162
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243401"
---
# <a name="mdschemacubes-rowset"></a>Set di righe MDSCHEMA_CUBES
  Descrive la struttura dei cubi all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_CUBES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del database.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo o della dimensione. I nomi delle dimensioni sono preceduti da un simbolo di dollaro ($). **Nota:** solo server e gli amministratori del database dispongono delle autorizzazioni per visualizzare i cubi creati da una dimensione.|  
|`CUBE_TYPE`|`DBTYPE_WSTR`||Tipo del cubo. I valori validi sono:<br /><br /> -   `CUBE`<br />-   `DIMENSION`|  
|`CUBE_GUID`|`DBTYPE_GUID`||Non supportato.|  
|`CREATED_ON`|`DBTYPE_DBTIMESTAMP`||Non supportato.|  
|`LAST_SCHEMA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Ora dell'ultima elaborazione del cubo.|  
|`SCHEMA_UPDATED_BY`|`DBTYPE_WSTR`||Non supportato.|  
|`LAST_DATA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Ora dell'ultima elaborazione del cubo.|  
|`DATA_UPDATED_BY`|`DBTYPE_WSTR`||Non supportato.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione semplice del cubo.|  
|`IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||Valore booleano che restituisce sempre true.|  
|`IS_LINKABLE`|`DBTYPE_BOOL`||Valore booleano che indica se un cubo può essere utilizzato in un cubo collegato.|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||Valore booleano che indica se un cubo è abilitato per la scrittura.|  
|`IS_SQL_ENABLED`|`DBTYPE_BOOL`||Valore booleano che indica se SQL può essere utilizzato nel cubo.|  
|`CUBE_CAPTION`|`DBTYPE_WSTR`||Didascalia del cubo.|  
|`BASE_CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo di origine se si tratta di un cubo di prospettiva.|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||(Facoltativo) Set di note, in formato XML.|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_CUBES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno di questi valori validi:<br /><br /> -1 CUBO<br />-DIMENSIONE DI 2<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
|`Base Cube_Name`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
