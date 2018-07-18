---
title: Recupero di una sola riga utilizzando IRow | Documenti Microsoft
description: Recupero di una singola riga mediante IRow interfaccia del Driver OLE DB per SQL Server
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
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 21123e4d9918216f9b23ca2c7304bdcb1be2b0c7
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690044"
---
# <a name="fetching-a-single-row-with-irow"></a>Recupero di una sola riga utilizzando IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il **IRow** interfaccia implementazione nel Driver OLE DB per SQL Server è stata semplificata per migliorare le prestazioni. **IRow** consente l'accesso diretto alle colonne di un singolo oggetto riga. Se si conosce in anticipo che il risultato di un'esecuzione del comando produca esattamente una riga, **IRow** recupererà le colonne di tale riga. Se il set di risultati include più righe, **IRow** esporrà solo la prima riga.  
  
 Il **IRow** implementazione non consente la navigazione della riga. A ogni colonna della riga è possibile accedere una sola volta, con un'eccezione. È infatti possibile accedere a una colonna una volta per trovarne le dimensioni e una seconda volta per recuperare i dati.  
  
> [!NOTE]  
>  **IRow:: Open** supporta solo i tipi DBGUID_STREAM e DBGUID_NULL di oggetti da aprire.  
  
 Per ottenere un oggetto riga utilizzando **ICommand:: Execute** metodo, è necessario passare IID_IRow. Il **IMultipleResults** interfaccia deve essere utilizzata per gestire più set di risultati. **IMultipleResults** supporta **IRow** e **IRowset**. **IRowset** viene utilizzato per le operazioni bulk.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Uso di IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
