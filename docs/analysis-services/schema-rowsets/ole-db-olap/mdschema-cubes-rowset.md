---
title: Set di righe MDSCHEMA_CUBES | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MDSCHEMA_CUBES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_CUBES rowset
ms.assetid: 5f1b63d4-aa3f-48c6-b866-7ffd91675044
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4b23f8bda8cc2aa410ddc04225420ff6372be3e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemacubes-rowset"></a>Set di righe MDSCHEMA_CUBES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descrive la struttura dei cubi all'interno di un database.  
  
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
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno di questi valori validi:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIONE|  
|**Base Cube_Name**|**DBTYPE_WSTR**|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
