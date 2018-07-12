---
title: Recupero di una sola riga con IRow | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 243d57b5e42e2c4ecebec6ce1e05d3061baa0a2c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412400"
---
# <a name="fetching-a-single-row-with-irow"></a>Recupero di una sola riga utilizzando IRow
  Il **IRow** implementazione nell'interfaccia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client è semplificato per migliorare le prestazioni. **IRow** consente l'accesso diretto alle colonne di un singolo oggetto riga. Se si conosce in anticipo che il risultato di un'esecuzione del comando produca esattamente una riga, **IRow** recupererà le colonne di tale riga. Se il set di risultati include più righe **IRow** esporrà solo la prima riga.  
  
 Il **IRow** implementazione non consente la navigazione della riga. A ogni colonna della riga è possibile accedere una sola volta, con un'eccezione. È infatti possibile accedere a una colonna una volta per trovarne le dimensioni e una seconda volta per recuperare i dati.  
  
> [!NOTE]  
>  **IRow:: Open** supporta solo un tipo i tipi DBGUID_STREAM e DBGUID_NULL di oggetti da aprire.  
  
 Per ottenere un oggetto riga utilizzando **ICommand:: Execute** metodo, è necessario passare IID_IRow. Il **IMultipleResults** interfaccia deve essere utilizzata per gestire più set di risultati. **IMultipleResults** supporta **IRow** e **IRowset**. **IRowset** viene usata per operazioni bulk.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Uso di IRow::GetColumns](using-irow-getcolumns.md)  
  
-   [Recupero di dati BLOB tramite IRow](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](rowsets.md)  
  
  
