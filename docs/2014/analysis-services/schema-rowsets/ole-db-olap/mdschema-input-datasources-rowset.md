---
title: Set di righe MDSCHEMA_INPUT_DATASOURCES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_INPUT_DATASOURCES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa2f372c4facb1b2e51561bbd82a8e35fe8ed134
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210031"
---
# <a name="mdschemainputdatasources-rowset"></a>Set di righe MDSCHEMA_INPUT_DATASOURCES
  Descrive le origini dati definite all'interno del database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_INPUT_DATASOURCES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del catalogo a cui appartiene questa origine dati.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`DATASOURCE_NAME`|`DBTYPE_WSTR`||Nome dell'oggetto origine dati.|  
|`DATASOURCE_TYPE`|`DBTYPE_WSTR`||Tipo dell'origine dati. I valori validi includono:<br /><br /> -   `Relational`<br />-   `Olap`|  
|`CREATED_ON`|`DBTYPE_DBTIMESTAMP`||Data di creazione dell'origine dati.|  
|`LAST_SCHEMA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Data e ora dell'ultima modifica apportata all'origine dati.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione semplice dell'azione.|  
|`TIMEOUT`|`DBTYPE_UI4`||Timeout dell'origine dati.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_INPUT_DATASOURCES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DATASOURCE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DATASOURCE_TYPE`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
