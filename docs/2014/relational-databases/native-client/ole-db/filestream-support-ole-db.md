---
title: Supporto FILESTREAM (OLE DB) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba270b26a5a290f5b5c6fdd2830f10b9bf695037
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063576"
---
# <a name="filestream-support-ole-db"></a>Supporto FILESTREAM (OLE DB)
  A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, OLE DB supporta la caratteristica FILESTREAM avanzata. Per ulteriori informazioni su questa funzionalità, vedere [supporto FILESTREAM](../features/filestream-support.md). Per esempi, vedere [Filestream e OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Per inviare e ricevere valori `varbinary(max)` maggiori di 2 GB, un'applicazione utilizza `DBTYPE_IUNKNOWN` in associazioni di parametri e di risultati. Per i parametri il provider deve chiamare IUnknown:: QueryInterface per ISequentialStream e per ottenere risultati che restituiscono ISequentialStream.  
  
 Per OLE DB, il controllo correlato ai valori ISequentialStream non è assoluto. Quando si *wType* viene `DBTYPE_IUNKNOWN` nel `DBBINDING` struct, controllo della lunghezza può essere disabilitata omettendo `DBPART_LENGTH` da *dwPart* o impostando la lunghezza dei dati (in corrispondenza dell'offset *obLength* nel buffer di dati) a ~ 0. In questo caso, il provider non controllerà la lunghezza del valore e richiederà e restituirà tutti i dati disponibili tramite il flusso. Questa modifica verrà applicata a tutti i tipi LOB (Large Object) e XML, ma solo in caso di connessione a server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. In questo modo, gli sviluppatori disporranno di maggiore flessibilità, mantenendo la coerenza e la compatibilità con le versioni precedenti per applicazioni esistenti e server legacy.  
  
 Questa modifica interessa tutte le interfacce che trasferiscono i dati, principalmente a IRowset:: GetData ICommand:: Execute e IRowsetFastLoad:: InsertRow.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione in SQL Server Native Client](../sql-server-native-client-programming.md)  
  
  