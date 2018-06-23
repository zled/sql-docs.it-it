---
title: Recupero di una sola riga utilizzando IRow | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bf3b6bc9fa7bdb31059e631d1afd2bd2dd94eed3
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694752"
---
# <a name="fetching-a-single-row-with-irow"></a>Recupero di una sola riga utilizzando IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il **IRow** nell'implementazione dell'interfaccia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client è stato semplificato per migliorare le prestazioni. **IRow** consente l'accesso diretto alle colonne di un singolo oggetto riga. Se si conosce in anticipo che il risultato di un'esecuzione del comando produca esattamente una riga, **IRow** recupererà le colonne di tale riga. Se il set di risultati include più righe, **IRow** esporrà solo la prima riga.  
  
 Il **IRow** implementazione non consente la navigazione della riga. A ogni colonna della riga è possibile accedere una sola volta, con un'eccezione. È infatti possibile accedere a una colonna una volta per trovarne le dimensioni e una seconda volta per recuperare i dati.  
  
> [!NOTE]  
>  **IRow:: Open** supporta solo i tipi DBGUID_STREAM e DBGUID_NULL di oggetti da aprire.  
  
 Per ottenere un oggetto riga utilizzando **ICommand:: Execute** metodo, è necessario passare IID_IRow. Il **IMultipleResults** interfaccia deve essere utilizzata per gestire più set di risultati. **IMultipleResults** supporta **IRow** e **IRowset**. **IRowset** viene utilizzato per le operazioni bulk.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Uso di IRow::GetColumns](../../relational-databases/native-client-ole-db-rowsets/using-irow-getcolumns.md)  
  
-   [Recupero di dati BLOB tramite IRow](http://msdn.microsoft.com/library/badbd6ac-20aa-4891-a14f-48d38e7f30de)  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
