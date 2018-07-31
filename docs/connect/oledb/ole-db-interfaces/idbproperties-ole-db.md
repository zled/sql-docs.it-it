---
title: IDBProperties (OLE DB) | Microsoft Docs
description: Interfaccia IDBProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d4f514c391b51326ced8df9e45082af54ee1c8c2
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106037"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  La specifica dello standard OLE DB consente ai provider di specificare VT_EMPTY per **DBPROPINFO::vValues**. Tuttavia, il driver OLE DB per SQL Server restituisce sempre VT_EMPTY quando si chiama **IDBProperties::GetPropertyInfo** con **DBPROPSET_ROWSETALL** per recuperare le proprietà dei set di righe.  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
