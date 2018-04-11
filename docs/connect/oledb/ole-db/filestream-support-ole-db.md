---
title: Supporto FILESTREAM (OLE DB) | Documenti Microsoft
description: Supporto FILESTREAM (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: efbe3ce15444b0c6556cf3cef0267e99bb55657f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="filestream-support-ole-db"></a>Supporto FILESTREAM (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e il Driver OLE DB per SQL Server, OLE DB supporta la caratteristica FILESTREAM avanzata. Per ulteriori informazioni su questa funzionalità, vedere [supporto FILESTREAM](../../oledb/features/filestream-support.md). Per esempi, vedere [Filestream e OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Per inviare e ricevere **varbinary (max)** valori maggiori di 2 GB, un'applicazione utilizza **DBTYPE_IUNKNOWN** nelle associazioni di parametro e il risultato. Per i parametri il provider deve chiamare IUnknown:: QueryInterface per ISequentialStream e per ottenere risultati che restituiscono ISequentialStream.  
  
 Per OLE DB, il controllo correlato ai valori ISequentialStream è assoluto. Quando *wType* è **DBTYPE_IUNKNOWN** nel **DBBINDING** struct, controllo della lunghezza può essere disabilitata omettendo **DBPART_LENGTH** da *dwPart* o impostando la lunghezza dei dati (offset *obLength* nel buffer di dati) a ~ 0. In questo caso, il provider non controllerà la lunghezza del valore e richiederà e restituirà tutti i dati disponibili tramite il flusso. Questa modifica verrà applicata a tutti i tipi LOB (Large Object) e XML, ma solo in caso di connessione a server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. In questo modo, gli sviluppatori disporranno di maggiore flessibilità, mantenendo la coerenza e la compatibilità con le versioni precedenti per applicazioni esistenti e server legacy.  
  
 Questa modifica interessa tutte le interfacce che trasferiscono i dati, principalmente IRowset:: GetData ICommand:: Execute e IRowsetFastLoad:: InsertRow.  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/oledb-driver-for-sql-server-programming.md)  
  
  
