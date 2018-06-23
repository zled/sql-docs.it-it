---
title: Set di righe MDSCHEMA_MEASUREGROUPS | Documenti Microsoft
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
- MDSCHEMA_MEASUREGROUPS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 046674dc7c579a99e3d9fd90a86c466001c270c0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068347"
---
# <a name="mdschemameasuregroups-rowset"></a>Set di righe MDSCHEMA_MEASUREGROUPS
  Descrive i gruppi di misure all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_MEASUREGROUPS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del catalogo a cui appartiene questo gruppo di misure. `NULL` se il provider non supporta i cataloghi.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo a cui appartiene questo gruppo di misure.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Nome del gruppo di misure.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione discorsiva del membro.|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||Valore booleano che indica se il gruppo di misure è abilitato per la scrittura.<br /><br /> Restituisce `true` se il gruppo di misure è abilitato per la scrittura.|  
|`MEASUREGROUP_CAPTION`|`DBTYPE_WSTR`||Didascalia di visualizzazione per il gruppo di misure.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_MEASUREGROUPS` può essere limitato nelle colonne della tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  