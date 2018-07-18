---
title: Set di righe MDSCHEMA_MEASUREGROUPS | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7846fa9eb88a91a945c787cfec0fe19d0c520cf6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300981"
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
  
  
