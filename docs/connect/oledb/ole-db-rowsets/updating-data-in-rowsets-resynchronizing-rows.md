---
title: Risincronizzazione delle righe | Microsoft Docs
description: Risincronizzazione delle righe usando il Driver OLE DB per SQL Server
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
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: dc7d722f4d4b97cd4242195d49ff7d5290c52f24
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017462"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Aggiornamento dei dati nei set di righe - Risincronizzazione delle righe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server supporta **IRowsetResynch** su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supportato dal cursore solo set di righe. **IRowsetResynch** non è disponibile su richiesta. Il consumer deve richiedere l'interfaccia prima di aprire il set di righe.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornamento dei dati nei set di righe](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
