---
title: Supporto dell'API OLE DB per i miglioramenti relativi a data e ora | Microsoft Docs
description: Supporto dell'API OLE DB per i miglioramenti relativi a data e ora
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 022f7814263067eaa3030ae6c376f99666ad0dd3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695829"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Supporto dell'API OLE DB per i miglioramenti relativi a data e ora
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le caratteristiche avanzate di data e ora sono supportate dalle seguenti API OLE DB.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|IAccessor:: CreateAccessor|Viene aggiunto un contrassegno nella struttura DBBINDING per consentire alle applicazioni per la discriminazione tra **data/ora**, **datetime2**, e **smalldatetime** valori. Per altre informazioni, vedere [Rowset Metadata e parametro](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Per altre informazioni, vedere [modifiche apportate alla copia Bulk per avanzate di data e ora i tipi &#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md).|  
|ICommandWithParameters::GetParameterInfo|Per altre informazioni, vedere[Rowset Metadata e parametro](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Per altre informazioni, vedere[Rowset Metadata e parametro](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Per altre informazioni, vedere[Rowset Metadata e parametro](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Per altre informazioni, vedere[Rowset Metadata e parametro](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset:: GetRowset|Per informazioni dettagliate di righe dello schema interessati, vedere[data e ora e i set di righe dello Schema](../../oledb/ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md).|  
|IRowsetFastLoad|Questa interfaccia supporta i nuovi tipi di data/ora, ma non è stata apportata alcuna modifica all'interfaccia.|  
|Itabledefinition:: CreateTable|Per altre informazioni, vedere [supporto dei tipi di dati per data OLE DB e miglioramenti per la fase](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Miglioramenti relativi a data e ora &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
