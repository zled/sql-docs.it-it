---
title: 'Utilizzo di IRow:: GetColumns | Documenti Microsoft'
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7f4f66d36796de8c4dbb0c39b169314be9bdc473
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="using-irowgetcolumns"></a>Utilizzo di IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il **IRow** implementazione consente l'accesso sequenza forward-only alle colonne. È possibile accedere a tutte le colonne nella riga con una singola chiamata a **IRow:: GetColumns** o chiamare **IRow:: GetColumns** più volte ogni volta che si accede più colonne nella riga.  
  
 Le diverse chiamate a **IRow:: GetColumns** non devono sovrapporsi. Ad esempio, se la prima chiamata a **IRow:: GetColumns** recupera colonne 1, 2 e 3, la seconda chiamata a **IRow:: GetColumns** deve chiamare per le colonne 4, 5 e 6. Se le chiamate successive a **IRow:: GetColumns** si sovrappongono, il flag di stato (campo dwstatus in DBCOLUMNACCESS) viene impostato su DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di una sola riga con IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
