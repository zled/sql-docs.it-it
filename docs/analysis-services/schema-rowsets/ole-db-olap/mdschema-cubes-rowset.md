---
title: Set di righe MDSCHEMA_CUBES | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82a07fda14984582ae9461d861df0fa47920b527
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemacubes-rowset"></a>Set di righe MDSCHEMA_CUBES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive la struttura dei cubi all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_CUBES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Nome del database.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Non supportato.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Nome del cubo o della dimensione. I nomi delle dimensioni sono preceduti da un simbolo di dollaro ($).<br /><br /> Nota: Solo gli amministratori di database e server di dispongano delle autorizzazioni per visualizzare i cubi creati da una dimensione.|  
|**CUBE_TYPE**|**DBTYPE_WSTR**|Tipo del cubo. I valori validi sono:<br /><br /> **CUBO**<br /><br /> **DIMENSIONE**|  
|**CUBE_GUID**|**DBTYPE_GUID**|Non supportato.|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**|Non supportato.|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**|Ora dell'ultima elaborazione del cubo.|  
|**SCHEMA_UPDATED_BY**|**DBTYPE_WSTR**|Non supportato.|  
|**LAST_DATA_UPDATE**|**DBTYPE_DBTIMESTAMP**|Ora dell'ultima elaborazione del cubo.|  
|**DATA_UPDATED_BY**|**DBTYPE_WSTR**|Non supportato.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descrizione semplice del cubo.|  
|**IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|Valore booleano che restituisce sempre true.|  
|**IS_LINKABLE**|**DBTYPE_BOOL**|Valore booleano che indica se un cubo può essere utilizzato in un cubo collegato.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**|Valore booleano che indica se un cubo è abilitato per la scrittura.|  
|**IS_SQL_ENABLED**|**DBTYPE_BOOL**|Valore booleano che indica se SQL può essere utilizzato nel cubo.|  
|**CUBE_CAPTION**|**DBTYPE_WSTR**|Didascalia del cubo.|  
|**BASE_CUBE_NAME**|**DBTYPE_WSTR**|Nome del cubo di origine se si tratta di un cubo di prospettiva.|  
|**ANNOTAZIONI**|**DBTYPE_WSTR**|(Facoltativo) Set di note, in formato XML.|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_CUBES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno di questi valori validi:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIONE|  
|**Base Cube_Name**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
