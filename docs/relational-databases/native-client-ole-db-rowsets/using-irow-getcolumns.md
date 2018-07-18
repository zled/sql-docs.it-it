---
title: 'Utilizzo di IRow:: GetColumns | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 131c677a67fdb28d1d37f3e6b7f11c4cd4e5deb1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432490"
---
# <a name="using-irowgetcolumns"></a>Utilizzo di IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il **IRow** implementazione consente l'accesso sequenza forward-only alle colonne. È possibile accedere a tutte le colonne nella riga con una singola chiamata a **IRow:: GetColumns** o chiamare **IRow:: GetColumns** più volte ogni volta che si accede di diverse colonne nella riga.  
  
 Le diverse chiamate a **IRow:: GetColumns** non devono sovrapporsi. Ad esempio, se la prima chiamata a **IRow:: GetColumns** recupera colonne 1, 2 e 3, la seconda chiamata a **IRow:: GetColumns** deve chiamare per le colonne 4, 5 e 6. Se le chiamate successive a **IRow:: GetColumns** si sovrappongono, il flag di stato (il campo dwstatus in DBCOLUMNACCESS) viene impostato su DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di una sola riga con IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
