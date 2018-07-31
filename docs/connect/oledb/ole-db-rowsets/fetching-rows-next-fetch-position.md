---
title: Posizione del recupero successivo | Microsoft Docs
description: Recupero di righe - Posizione del recupero successivo
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
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ec1149b615c64f2113afc007c0ea04e4c4665698
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106107"
---
# <a name="fetching-rows---next-fetch-position"></a>Recupero di righe - Posizione del recupero successivo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il driver OLE DB per SQL Server tiene traccia della posizione del recupero successivo in modo che una sequenza di chiamate al metodo **GetNextRows** (senza elementi ignorati, cambiamenti di direzione o nuove chiamate ai metodi **FindNextRow**, **Seek** o **RestartPosition**) legga l'intero set di righe senza ignorare o ripetere alcuna riga. La posizione del recupero successiva viene modificata chiamando **IRowset::GetNextRows**, **IRowset::RestartPosition** o **IRowsetIndex::Seek** oppure chiamando **FindNextRow** con un valore *pBookmark* Null. La chiamata a **FindNextRow** con un valore *pBookmark* non Null non influisce sulla posizione del recupero successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di righe](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
