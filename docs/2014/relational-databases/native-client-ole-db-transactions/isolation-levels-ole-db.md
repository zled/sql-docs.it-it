---
title: I livelli di isolamento (OLE DB) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6a83ec8d81a3c9e07c36c3973735c3a62746bd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168989"
---
# <a name="isolation-levels-ole-db"></a>Livelli di isolamento (OLE DB)
  I client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono controllare i livelli di isolamento delle transazioni per una connessione. Per controllare il livello di isolamento delle transazioni, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer di provider OLE DB Native Client utilizza:  
  
-   Proprietà DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modalità autocommit predefinita del provider OLE DB Native Client.  
  
     Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impostazione predefinita del provider OLE DB Native Client per il livello è DBPROPVAL_TI_READCOMMITTED.  
  
-   Il *isoLevel* parametro del **ITransactionLocal:: StartTransaction** metodo per le transazioni locali di commit manuale.  
  
-   Il *isoLevel* parametro del **ITransactionDispenser:: BeginTransaction** metodo per la coordinata MS DTC transazioni distribuite.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente accesso di sola lettura nel livello di isolamento di lettura dirty. Tutti gli altri livelli limitano la concorrenza applicando blocchi agli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché il client richiede livelli di concorrenza maggiori, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applica restrizioni superiori all'accesso simultaneo ai dati. Per mantenere il massimo livello di accesso simultaneo ai dati, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client deve controllare in modo intelligenze le richieste per livelli di concorrenza specifici.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] è stato introdotto il livello di isolamento dello snapshot. Per altre informazioni, vedere [utilizzo dell'isolamento dello Snapshot](../native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Transazioni](transactions.md)  
  
  