---
title: Rimuovere una colonna da una tabella di SQL Server | Documenti Microsoft
description: Rimozione di una colonna da una tabella di SQL Server utilizzando il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 962e36bf135c6f01594652f4549b7e0216cd063f
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689084"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Rimozione di una colonna da una tabella di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server espone il **itabledefinition:: Dropcolumn** (funzione). Ciò consente ai consumer di rimuovere una colonna da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella.  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel *pwszName*appartenente il *uName* unione nel *pTableID* parametro. Il *eKind*appartenente *pTableID* deve essere DBKIND_NAME.  
  
 Il consumer indica un nome di colonna nel *pwszName*appartenente il *uName* unione nel *pColumnID* parametro. Il nome di colonna è una stringa di caratteri Unicode. Il *eKind* appartenente *pColumnID* deve essere DBKIND_NAME.  
  
## <a name="example"></a>Esempio  
  
### <a name="code"></a>codice  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
