---
title: I livelli di isolamento (OLE DB) | Documenti Microsoft
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
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d1870c4f9f348c9d1b2ca52b94ee38a3e5d38190
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35698072"
---
# <a name="isolation-levels-ole-db"></a>Livelli di isolamento (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  I client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono controllare i livelli di isolamento delle transazioni per una connessione. Per controllare il livello di isolamento delle transazioni, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer di provider OLE DB Native Client utilizza:  
  
-   Proprietà DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modalità autocommit predefinita del provider OLE DB Native Client.  
  
     Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impostazione predefinita del provider OLE DB Native Client per il livello è DBPROPVAL_TI_READCOMMITTED.  
  
-   Il *isoLevel* parametro del **ITransactionLocal:: StartTransaction** metodo per le transazioni locali di commit manuale.  
  
-   Il *isoLevel* parametro del **ITransactionDispenser:: BeginTransaction** metodo per la coordinata MS DTC transazioni distribuite.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente accesso di sola lettura nel livello di isolamento di lettura dirty. Tutti gli altri livelli limitano la concorrenza applicando blocchi agli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché il client richiede livelli di concorrenza maggiori, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applica restrizioni superiori all'accesso simultaneo ai dati. Per mantenere il massimo livello di accesso simultaneo ai dati, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client deve controllare in modo intelligenze le richieste per livelli di concorrenza specifici.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] è stato introdotto il livello di isolamento dello snapshot. Per altre informazioni, vedere [utilizzo dell'isolamento dello Snapshot](../../relational-databases/native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Transazioni](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
