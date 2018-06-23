---
title: Supporto dell'API OLE DB per data e ora miglioramenti | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2bf7eee4dd2517d4ff9c9f871160ba0515b18ce8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170554"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Supporto dell'API OLE DB per data e ora miglioramenti
  Le caratteristiche avanzate di data e ora sono supportate dalle seguenti API OLE DB.  
  
|Funzione|Description|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Un flag viene aggiunto nella struttura DBBINDING per consentire alle applicazioni di distinguere tra i valori `datetime`, `datetime2` e `smalldatetime`. Per altre informazioni, vedere [Metadata per parametri e Rowset](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Per altre informazioni, vedere [modifiche di copia Bulk per avanzate di data e ora tipi &#40;OLE DB e ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Per altre informazioni, vedere[Metadata per parametri e Rowset](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Per altre informazioni, vedere[Metadata per parametri e Rowset](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Per altre informazioni, vedere[Metadata per parametri e Rowset](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Per altre informazioni, vedere[Metadata per parametri e Rowset](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Per informazioni dettagliate sui set di righe dello schema interessati, vedere[data e ora e i set di righe dello Schema](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Questa interfaccia supporta i nuovi tipi di data/ora, ma non è stata apportata alcuna modifica all'interfaccia.|  
|ITableDefinition::CreateTable|Per altre informazioni, vedere [tipi di dati supportati per data OLE DB e i miglioramenti tempo](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Data e ora miglioramenti &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  