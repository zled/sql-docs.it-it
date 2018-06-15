---
title: Set di righe MDSCHEMA_INPUT_DATASOURCES | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 329f3081e3e16b3603c5ddd299ccafc0a98f6a9a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028302"
---
# <a name="mdschemainputdatasources-rowset"></a>Set di righe MDSCHEMA_INPUT_DATASOURCES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive le origini dati definite all'interno del database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_INPUT_DATASOURCES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Nome del catalogo a cui appartiene questa origine dati.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Non supportato.|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**||Nome dell'oggetto origine dati.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**||Tipo dell'origine dati. I valori validi includono:<br /><br /> **Relazionale**<br /><br /> **OLAP**|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**||Data di creazione dell'origine dati.|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**||Data e ora dell'ultima modifica apportata all'origine dati.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione semplice dell'azione.|  
|**TIMEOUT**|**DBTYPE_UI4**||Timeout dell'origine dati.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_INPUT_DATASOURCES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
