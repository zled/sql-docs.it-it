---
title: Set di righe MDSCHEMA_INPUT_DATASOURCES | Documenti Microsoft
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
- MDSCHEMA_INPUT_DATASOURCES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a810fef41d402cb35d9e6e3c62120f09b0c6bae4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemainputdatasources-rowset"></a>Set di righe MDSCHEMA_INPUT_DATASOURCES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descrive le origini dati definite all'interno del database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_INPUT_DATASOURCES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
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
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
