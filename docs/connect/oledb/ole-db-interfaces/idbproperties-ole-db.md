---
title: IDBProperties (OLE DB) | Documenti Microsoft
description: Interfaccia IDBProperties (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea67dba9a2a0f884a297ef0c1fffee053b1cbe8b
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  La specifica dello standard OLE DB consente ai provider di specificare VT_EMPTY per **DBPROPINFO::vValues**. Tuttavia, il Driver OLE DB per SQL Server OLE DB restituisce sempre VT_EMPTY quando si chiama **IDBProperties:: GetPropertyInfo** con **DBPROPSET_ROWSETALL** per recuperare le proprietà set di righe.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce &#40; OLE DB &#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
