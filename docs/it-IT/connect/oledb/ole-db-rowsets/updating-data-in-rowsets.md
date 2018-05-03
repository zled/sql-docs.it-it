---
title: L'aggiornamento dei dati nei set di righe | Documenti Microsoft
description: L'aggiornamento dei dati nei set di righe usando il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 50acb90ed3adcdcb6fb30c00e0f1e25f4f574cd0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data-in-rowsets"></a>Aggiornamento dei dati dei set di righe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per gli aggiornamenti di SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dati quando un consumer aggiorna un set di righe modificabile che contiene i dati. Viene creato un set di righe modificabile quando il consumer richiede il supporto per uno di **IRowsetChange** o **IRowsetUpdate** interfaccia.  
  
 Tutti i Driver OLE DB per l'utilizzo di set di righe modificabile con SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursori per supportare il set di righe. La proprietà del set di righe DBPROP_LOCKMODE modifica il comportamento di controllo della concorrenza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nei cursori e determina il comportamento di recupero delle righe del set di righe e di generazione degli errori di integrità dei dati nei set di righe aggiornabili.  
  
 Il Driver OLE DB per SQL Server supporta la sincronizzazione di riga prima o dopo un aggiornamento.  
  
> [!NOTE]  
>  IRowChange::SetColumns è disponibile per l'impostazione dei valori di una o più colonne denominate di un oggetto riga.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Aggiornamento dei dati nei cursori SQL Server](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Risincronizzazione delle righe](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
