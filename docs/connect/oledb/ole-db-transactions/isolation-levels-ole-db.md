---
title: Livelli di isolamento (OLE DB) | Documenti Microsoft
description: Livelli di isolamento (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 0774a7743cc9993b05f1470be31faf482147d282
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306770"
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
  
  
