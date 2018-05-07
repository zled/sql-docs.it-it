---
title: Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4be854b72c773300115e49551ceaf0ddc4d7db81
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
