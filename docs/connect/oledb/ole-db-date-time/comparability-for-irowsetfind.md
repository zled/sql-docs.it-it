---
title: Confronto per IRowsetFind | Documenti Microsoft
description: Possibilità di confronto per IRowsetFind
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 63f7625014822e063eb4ca8b91dd3411fc7d788c
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="comparability-for-irowsetfind"></a>Possibilità di confronto per IRowsetFind
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
 [Data e ora miglioramenti &#40; OLE DB &#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
