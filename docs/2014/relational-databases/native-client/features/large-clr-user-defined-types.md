---
title: Tipi definiti dall'utente CLR di grandi dimensioni | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e34a2320c5caf05ed1ce4909422bc5b340713125
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417640"
---
# <a name="large-clr-user-defined-types"></a>Tipi CLR definiti dall'utente di grandi dimensioni
  In SQL Server 2005 i tipi definiti dall'utente in CLR (Common Language Runtime) sono limitati a dimensioni di 8.000 byte. Questa restrizione è stata eliminata in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e versioni successive. In questa versione i tipi CLR definiti dall'utente vengono considerati simili ai tipi LOB. Tipi definiti dall'utente minori o uguali a 8.000 byte, pertanto, hanno lo stesso comportamento che in SQL Server 2005, ma sono supportati dati definiti dall'utente di dimensioni maggiori, che vengono indicate come illimitate ("unlimited").  
  
 Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;OLE DB&#41; ](../ole-db/large-clr-user-defined-types-ole-db.md) e [Large CLR User-Defined tipi &#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="use-cases"></a>Modalità di utilizzo comuni  
 Per ODBC, il supporto per i tipi definiti dall'utente di grandi dimensioni include la possibilità di inviare i valori di tali tipi in parti come parametri data-at-execution. Questa operazione viene eseguita dall'uso di SQLPutData.  
  
 Per OLE DB, il supporto per i tipi UDT di grandi dimensioni include la capacità di valori UDT di flusso da e verso il server usando l'associazione di ISequentialStream.  
  
 Tipi definiti dall'utente minori o uguali a 8.000 byte hanno lo stesso comportamento che in SQL Server 2005. Per OLE DB, si può comunque trasmettere piccole tipi definiti dall'utente tramite il binding di ISequentialStream.  
  
 Il codice nativo dovrà talvolta riconoscere il contenuto dei tipi CLR definiti dall'utente, ma non dovrà creare istanze di oggetti gestiti. In tal caso, è possibile utilizzare serializzazione personalizzata per convertire i valori dei tipi definiti dall'utente nel server in un formato noto per i client.  
  
 Per le applicazioni che dispongono di codice di accesso ai dati, è possibile sfruttare il comportamento dei tipi CLR definiti dall'utente nel client recuperando tali tipi tramite API native e creandone istanze tramite l'interoperabilità C++ CLI in applicazioni in modalità mista.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](sql-server-native-client-features.md)  
  
  
