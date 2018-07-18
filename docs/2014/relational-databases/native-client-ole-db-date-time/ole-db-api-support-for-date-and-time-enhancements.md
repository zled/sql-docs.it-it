---
title: Supporto dell'API OLE DB per data e ora miglioramenti | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b94ba91b68daf5415b4c9ae753f4d9e32c6949bc
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408387"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Supporto dell'API OLE DB per data e ora miglioramenti
  Le caratteristiche avanzate di data e ora sono supportate dalle seguenti API OLE DB.  
  
|Funzione|Description|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Un flag viene aggiunto nella struttura DBBINDING per consentire alle applicazioni di distinguere tra i valori `datetime`, `datetime2` e `smalldatetime`. Per altre informazioni, vedere [Rowset Metadata e parametro](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Per altre informazioni, vedere [modifiche apportate alla copia Bulk per avanzate di data e ora i tipi &#40;OLE DB e ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Per altre informazioni, vedere[Rowset Metadata e parametro](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Per altre informazioni, vedere[Rowset Metadata e parametro](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Per altre informazioni, vedere[Rowset Metadata e parametro](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Per altre informazioni, vedere[Rowset Metadata e parametro](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Per informazioni dettagliate di righe dello schema interessati, vedere[data e ora e i set di righe dello Schema](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Questa interfaccia supporta i nuovi tipi di data/ora, ma non è stata apportata alcuna modifica all'interfaccia.|  
|ITableDefinition::CreateTable|Per altre informazioni, vedere [supporto dei tipi di dati per data OLE DB e miglioramenti per la fase](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Data e miglioramenti per la fase &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  
