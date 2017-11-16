---
title: Set di righe DBSCHEMA_TABLES | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
apiname:
- DBSCHEMA_TABLES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1bc193f33395521c62e1b5e998c2098721313d9b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbschematables-rowset"></a>Set di righe DBSCHEMA_TABLES
  Identifica i gruppi di misure e le dimensioni esposte come tabelle all'interno di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DBSCHEMA_TABLES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|255|Nome del catalogo a cui appartiene l'oggetto.|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|255|Nome del cubo a cui appartiene l'oggetto.|  
|**TABLE_NAME**|**DBTYPE_WSTR**|255|Il nome dell'oggetto, se **TABLE_TYPE** è **tabella**.|  
|**TABLE_TYPE**|**DBTYPE_WSTR**||Tipo della tabella.<br /><br /> **TABELLA** indica l'oggetto è un gruppo di misure.<br /><br /> **TABELLA di sistema** indica l'oggetto è una dimensione.|  
|**TABLE_GUID**|**DBTYPE_GUID**||Non supportato.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione leggibile dell'oggetto.|  
|**TABLE_PROPID**|**DBTYPE_UI4**||Non supportato.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||Non supportato.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Data dell'ultima modifica apportata all'oggetto.|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**||Tipo OLAP dell'oggetto.<br /><br /> **MEASURE_GROUP** indica l'oggetto è un gruppo di misure.<br /><br /> **CUBE_DIMENSION** indicato l'oggetto è una dimensione.|  
  
 Il set di righe viene ordinato in base **TABLE_TYPE**, **TABLE_CATALOG**, **TABLE_SCHEMA**, e **TABLE_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DBSCHEMA_TABLES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_NAME**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_TYPE**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

