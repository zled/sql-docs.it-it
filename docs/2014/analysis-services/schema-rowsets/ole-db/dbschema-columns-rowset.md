---
title: Set di righe DBSCHEMA_COLUMNS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DBSCHEMA_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_COLUMNS rowset
ms.assetid: 653bdd07-a533-4a99-8b6a-6e5c7322e1f3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6354f098140ff7775967fad89b1198e18619395b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173192"
---
# <a name="dbschemacolumns-rowset"></a>Set di righe DBSCHEMA_COLUMNS
  Fornisce informazioni di colonna per tutte le colonne che soddisfano i criteri di restrizione specificati.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DBSCHEMA_COLUMNS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`||Nome del database.|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`||Non supportato.|  
|`TABLE_NAME`|`DBTYPE_WSTR`||Nome del cubo.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Nome della gerarchia dell'attributo o della misura.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||Non supportato.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||Non supportato.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Posizione della colonna a partire da 1.|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||Non supportato.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Non supportato.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||Maschera di bit `DBCOLUMNFLAGS` tramite cui vengono indicate le proprietà della colonna. Vedere 'Tipo enumerato DBCOLUMNFLAGS' in [IColumnsInfo:: GetColumnInfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Restituisce sempre `false`.|  
|`DATA_TYPE`|`DBTYPE_WSTR`<br /><br /> `DBTYPE_VARIANT`||Tipo di dati della colonna. Viene restituita una stringa per le colonne della dimensione e un tipo di dati Variant per le misure.|  
|`TYPE_GUID`|`DBTYPE_GUID`||Non supportato.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Lunghezza massima possibile di un valore all'interno della colonna.<br /><br /> Viene recuperata dalla proprietà `DataSize` in `DataItem`.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Lunghezza massima possibile di un valore all'interno della colonna, in byte, per colonne di tipo character o binary.<br /><br /> Un valore pari a zero (0) indica che la colonna non dispone di una lunghezza massima.<br /><br /> Per le colonne che non restituiscono dati di tipo binary o character, verrà restituito `NULL`.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Precisione massima della colonna per tipi di dati numerici diversi da `DBTYPE_VARNUMERIC`.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Numero di cifre a destra del separatore decimale per `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC`, `DBTYPE_VARNUMERIC`. In caso contrario è `NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Non supportato.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Non supportato.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Non supportato.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Non supportato.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Non supportato.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Non supportato.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Non supportato.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Non supportato.|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`||Tipo OLAP dell'oggetto.<br /><br /> Tramite `MEASURE` viene indicato che l'oggetto è una misura.<br /><br /> Tramite `ATTRIBUTE` viene indicato che l'oggetto è un attributo della dimensione.<br /><br /> Tramite `SCHEMA` viene indicato che l'oggetto è una colonna di uno schema.|  
  
 Il set di righe viene ordinato in base a `TABLE_CATALOG`, `TABLE_SCHEMA`, `TABLE_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DBSCHEMA_COLUMNS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|Facoltativo|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|Facoltativo|  
|`TABLE_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB](ole-db-schema-rowsets.md)  
  
  
