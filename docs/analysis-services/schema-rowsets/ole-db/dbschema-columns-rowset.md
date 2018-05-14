---
title: Set di righe DBSCHEMA_COLUMNS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2bb1fec6a1633f545f0c65feda93c7e19c649a6e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="dbschemacolumns-rowset"></a>Set di righe DBSCHEMA_COLUMNS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fornisce informazioni di colonna per tutte le colonne che soddisfano i criteri di restrizione specificati.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DBSCHEMA_COLUMNS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**||Nome del database.|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**||Non supportato.|  
|**TABLE_NAME**|**DBTYPE_WSTR**||Nome del cubo.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**||Nome della gerarchia dell'attributo o della misura.|  
|**CON**|**DBTYPE_GUID**||Non supportato.|  
|**COLUMN_PROPID**|**DBTYPE_UI4**||Non supportato.|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**||Posizione della colonna a partire da 1.|  
|**COLUMN_HAS_DEFAULT**|**DBTYPE_BOOL**||Non supportato.|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**||Non supportato.|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**||Oggetto **DBCOLUMNFLAGS** maschera di bit che indica le proprietà delle colonne. Vedere la sezione 'Tipo enumerato DBCOLUMNFLAGS' in [IColumnsInfo:: GetColumnInfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|**IS_NULLABLE**|**DBTYPE_BOOL**||Restituisce sempre **false**.|  
|**DATA_TYPE**|**DBTYPE_WSTR**<br /><br /> **DBTYPE_VARIANT**||Tipo di dati della colonna. Viene restituita una stringa per le colonne della dimensione e un tipo di dati Variant per le misure.|  
|**TYPE_GUID**|**DBTYPE_GUID**||Non supportato.|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**||Lunghezza massima possibile di un valore all'interno della colonna.<br /><br /> Viene recuperata dal **DataSize** proprietà il **DataItem**.|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**||Lunghezza massima possibile di un valore all'interno della colonna, in byte, per colonne di tipo character o binary.<br /><br /> Un valore pari a zero (0) indica che la colonna non dispone di una lunghezza massima.<br /><br /> **NULL** verranno restituite per le colonne che non restituiscono i tipi di dati binary o character.|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||La precisione massima della colonna per i dati numerici tipi diversi da **DBTYPE_VARNUMERIC**.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||Il numero di cifre a destra del separatore decimale per **DBTYPE_DECIMAL**, **DBTYPE_NUMERIC**, **DBTYPE_VARNUMERIC**. In caso contrario, si tratta **NULL**.|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**||Non supportato.|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**||Non supportato.|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**||Non supportato.|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**||Non supportato.|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**||Non supportato.|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**||Non supportato.|  
|**COLLATION_NAME**|**DBTYPE_WSTR**||Non supportato.|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**||Non supportato.|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**||Non supportato.|  
|**NOME_DOMINIO**|**DBTYPE_WSTR**||Non supportato.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Non supportato.|  
|**COLUMN_OLAP_TYPE**|**DBTYPE_WSTR**||Tipo OLAP dell'oggetto.<br /><br /> **MISURA** indica l'oggetto è una misura.<br /><br /> **ATTRIBUTO** indica l'oggetto è un attributo della dimensione.<br /><br /> **SCHEMA** indica l'oggetto è una colonna in uno schema.|  
  
 Il set di righe viene ordinato in base **TABLE_CATALOG**, **TABLE_SCHEMA**, **TABLE_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DBSCHEMA_COLUMNS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_NAME**|**DBTYPE_WSTR**|Facoltativo|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|Facoltativo|  
|**COLUMN_OLAP_TYPE**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
