---
title: Confronto per IRowsetFind | Microsoft Docs
description: Possibilità di confronto per IRowsetFind
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 33ddde806c456b59391e06b75d5ab11446b038f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731839"
---
# <a name="comparability-for-irowsetfind"></a>Possibilità di confronto per IRowsetFind
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Solo per i tipi data/ora, IRowsetFind supporta i confronti seguenti:  
  
-   LT  
  
-   LE  
  
-   EQ  
  
-   GE  
  
-   GT  
  
-   NE  
  
-   IGNORE  
  
 Se viene tentato qualsiasi altro confronto, viene restituito DB_E_BADCOMPAREOP, in conformità con la specifica OLE DB.  
  
## <a name="see-also"></a>Vedere anche  
 [Miglioramenti relativi a data e ora &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
