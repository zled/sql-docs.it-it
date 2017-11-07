---
title: Set di righe MDSCHEMA_MEASUREGROUPS | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_MEASUREGROUPS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d39a7ce85ec5c4781d69d5a0bcd2fb468dd701bc
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemameasuregroups-rowset"></a>Set di righe MDSCHEMA_MEASUREGROUPS
  Descrive i gruppi di misure all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe **MDSCHEMA_MEASUREGROUPS** contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Nome del catalogo a cui appartiene questo gruppo di misure. **NULL** se il provider non supporta i cataloghi.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Non supportato.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Nome del cubo a cui appartiene questo gruppo di misure.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Nome del gruppo di misure.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione discorsiva del membro.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**||Valore booleano che indica se il gruppo di misure è abilitato per la scrittura.<br /><br /> Restituisce **true** se il gruppo di misure è abilitato per la scrittura.|  
|**MEASUREGROUP_CAPTION**|**DBTYPE_WSTR**||Didascalia di visualizzazione per il gruppo di misure.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe **MDSCHEMA_MEASUREGROUPS** può essere limitato nelle colonne della tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

