---
title: 'Utilizzo di IRow:: GetColumns | Documenti Microsoft'
description: 'Utilizzo di IRow:: GetColumns per accedere a tutte le colonne in una riga'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b18b256d859c85b846d81ae239003fec2aafc010
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="using-irowgetcolumns"></a>Utilizzo di IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il **IRow** implementazione consente l'accesso sequenza forward-only alle colonne. È possibile accedere a tutte le colonne nella riga con una singola chiamata a **IRow:: GetColumns** o chiamare **IRow:: GetColumns** più volte ogni volta che si accede più colonne nella riga.  
  
 Le diverse chiamate a **IRow:: GetColumns** non devono sovrapporsi. Ad esempio, se la prima chiamata a **IRow:: GetColumns** recupera colonne 1, 2 e 3, la seconda chiamata a **IRow:: GetColumns** deve chiamare per le colonne 4, 5 e 6. Se le chiamate successive a **IRow:: GetColumns** si sovrappongono, il flag di stato (campo dwstatus in DBCOLUMNACCESS) viene impostato su DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di una sola riga utilizzando IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
