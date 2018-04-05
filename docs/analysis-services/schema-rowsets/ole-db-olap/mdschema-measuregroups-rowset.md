---
title: Set di righe MDSCHEMA_MEASUREGROUPS | Documenti Microsoft
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
ms.openlocfilehash: aebac1aafd7d49e6b5b5c21343161184ba19da34
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemameasuregroups-rowset"></a>Set di righe MDSCHEMA_MEASUREGROUPS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descrive i gruppi di misure all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe **MDSCHEMA_MEASUREGROUPS** contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
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
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
