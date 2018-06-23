---
title: 'Utilizzo di IRow:: GetColumns | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 9924e5374909ec8ff9a6465b7e7d1b5c594faf25
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694592"
---
# <a name="using-irowgetcolumns"></a>Utilizzo di IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il **IRow** implementazione consente l'accesso sequenza forward-only alle colonne. È possibile accedere a tutte le colonne nella riga con una singola chiamata a **IRow:: GetColumns** o chiamare **IRow:: GetColumns** più volte a ogni accesso a diverse colonne nella riga.  
  
 Le diverse chiamate a **IRow:: GetColumns** non devono sovrapporsi. Se, ad esempio, la prima chiamata a **IRow:: GetColumns** recupera colonne 1, 2 e 3, la seconda chiamata a **IRow:: GetColumns** deve chiamare per le colonne 4, 5 e 6. Se le chiamate successive a **IRow:: GetColumns** periodo pianificato si sovrappongono, il flag di stato (campo dwstatus in DBCOLUMNACCESS) viene impostato su DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di una sola riga con IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
