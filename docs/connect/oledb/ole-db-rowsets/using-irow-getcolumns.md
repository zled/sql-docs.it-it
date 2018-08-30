---
title: 'Utilizzo di IRow:: GetColumns | Microsoft Docs'
description: 'Utilizzo di IRow:: GetColumns per accedere a tutte le colonne in una riga'
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.author: pelopes
manager: craigg
ms.openlocfilehash: b92b76eca593259457727f9f870eb45b66cb477d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025759"
---
# <a name="using-irowgetcolumns"></a>Utilizzo di IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L'implementazione di IRow** consente un accesso sequenziale forward-only alle colonne. È possibile accedere a tutte le colonne nella riga con una sola chiamata a IRow::GetColumns **o chiamare IRow::GetColumns** più volte a ogni accesso a diverse colonne nella riga.  
  
 Le diverse chiamate a IRow::GetColumns** non devono sovrapporsi. Se ad esempio la prima chiamata a IRow::GetColumns recupera le colonne 1, 2 e 3, la seconda chiamata dovrebbe recuperare le colonne 4, 5 e 6. Se le chiamate successive a IRow::GetColumns** si sovrappongono, il flag di stato (il campo dwstatus in DBCOLUMNACCESS) viene impostato su DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di una sola riga con IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
