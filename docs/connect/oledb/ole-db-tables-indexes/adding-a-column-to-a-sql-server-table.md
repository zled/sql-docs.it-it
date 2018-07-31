---
title: Aggiunta di una colonna in una tabella SQL Server | Microsoft Docs
description: Aggiunta di una colonna a una tabella di SQL Server usando il Driver OLE DB per SQL Server
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
- AddColumn function
- OLE DB Driver for SQL Server, columns
- adding columns
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 9c5aeac8ff4ddd8a445e0487caf894b34b539302
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107273"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Aggiunta di una colonna a una tabella di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server espone il **itabledefinition:: AddColumn** (funzione). Questo consente ai consumer di aggiungere una colonna a una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Quando si aggiunge una colonna da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella, il Driver OLE DB consumer di SQL Server è limitato come segue:  
  
-   Se DBPROP_COL_AUTOINCREMENT è VARIANT_TRUE, DBPROP_COL_NULLABLE deve essere VARIANT_FALSE.  
  
-   Se la colonna viene definita tramite il tipo di dati **timestamp** di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], DBPROP_COL_NULLABLE deve essere VARIANT_FALSE.  
  
-   Per qualsiasi altra definizione di colonna, DBPROP_COL_NULLABLE deve essere VARIANT_TRUE.  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel membro *pwszName* dell'unione *uName* nel parametro *pTableID*. Il membro *eKind* di *pTableID* deve essere DBKIND_NAME.  
  
 Il nome della nuova colonna viene specificato come stringa di caratteri Unicode nel membro *pwszName* dell'unione *uName* nel membro *dbcid* del parametro DBCOLUMNDESC *pColumnDesc*. Il membro *eKind* deve essere DBKIND_NAME.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)  
  
  
