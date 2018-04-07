---
title: Livelli di isolamento (OLE DB) | Documenti Microsoft
description: Livelli di isolamento (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f40f3936fbf4ace09ff1df6a18ef86bc00747fd4
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="isolation-levels-ole-db"></a>Livelli di isolamento (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  I client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] possono controllare i livelli di isolamento delle transazioni per una connessione. Per controllare il livello di isolamento delle transazioni, viene utilizzato il Driver OLE DB per il consumer di SQL Server:  
  
-   Proprietà DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS per il Driver OLE DB per la modalità autocommit predefinita di SQL Server.  
  
     Il Driver OLE DB per impostazione predefinita di SQL Server per il livello è DBPROPVAL_TI_READCOMMITTED.  
  
-   Il *isoLevel* parametro il **ITransactionLocal:: StartTransaction** metodo per le transazioni locali di commit manuale.  
  
-   Il *isoLevel* parametro del **ITransactionDispenser:: BeginTransaction** metodo per la coordinata MS DTC transazioni distribuite.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente accesso di sola lettura nel livello di isolamento di lettura dirty. Tutti gli altri livelli limitano la concorrenza applicando blocchi agli oggetti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Poiché il client richiede livelli di concorrenza maggiori, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applica restrizioni superiori all'accesso simultaneo ai dati. Per mantenere il massimo livello di accesso simultaneo ai dati, il Driver OLE DB per il consumer di SQL Server deve controllare in modo intelligenze le richieste per livelli di concorrenza specifici.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] è stato introdotto il livello di isolamento dello snapshot. Per ulteriori informazioni, vedere [utilizzo dell'isolamento dello Snapshot](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Transazioni](../../oledb/ole-db-transactions/transactions.md)  
  
  
