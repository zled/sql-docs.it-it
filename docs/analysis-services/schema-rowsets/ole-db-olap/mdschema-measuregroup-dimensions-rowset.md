---
title: Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_MEASUREGROUP_DIMENSIONS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEASUREGROUP_DIMENSIONS rowset
ms.assetid: c731c06a-7382-4e50-ba0e-d8cee3ab4f28
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d94779b19769a5ee5ac9d5d10f2804114911cde
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS
  Enumera le dimensioni dei gruppi di misure.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_MEASUREGROUP_DIMENSIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Nome del catalogo a cui appartiene questo gruppo di misure. **NULL** se il provider non supporta i cataloghi.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Non supportato.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Nome del cubo a cui appartiene questo gruppo di misure.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Nome del gruppo di misure.|  
|**MEASUREGROUP_CARDINALITY**|**DBTYPE_WSTR**||Numero di istanze di cui una misura nel gruppo di misure può disporre per un singolo membro di dimensione. I valori possibili includono:<br /><br /> **UNO**<br /><br /> **MOLTI**|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco per la dimensione.|  
|**DIMENSION_CARDINALITY**|**DBTYPE_WSTR**||Numero di istanze di cui un membro di dimensione può disporre per una singola istanza di una misura del gruppo di misure. I valori possibili includono:<br /><br /> **UNO**<br /><br /> **MOLTI**|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**||Valore booleano che indica se le gerarchie nella dimensione sono visibili.<br /><br /> Restituisce **TRUE** se uno o più gerarchie nella dimensione è visibile; in caso contrario, **FALSE**.|  
|**DIMENSION_IS_FACT_DIMENSION**|**DBTYPE_BOOL**||Valore booleano che indica se la dimensione è una dimensione dei fatti.<br /><br /> Restituisce **TRUE** se la dimensione è una dimensione dei fatti; in caso contrario, **FALSE**.|  
|**DIMENSION_PATH**|**DBTYPE_HCHAPTER**||Elenco di dimensioni per la dimensione di riferimento.|  
|**DIMENSION_GRANULARITY**|**DBTYPE_WSTR**||Nome univoco della gerarchia di granularità.|  
  
 Il set di righe supporta l'ordinamento in **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**, **MEASUREGROUP_NAME**,  **DIMENSION_UNIQUE_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_MEASUREGROUP_DIMENSIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> 1 Visibile<br /><br /> 2 Non visibile<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
