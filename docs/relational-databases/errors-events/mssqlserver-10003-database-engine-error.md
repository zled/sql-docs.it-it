---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 49fd4f9e0573ecd2230ee5573a0166c17189a0ac
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver10003"></a>MSSQLSERVER_10003
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10003|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HR_E_OUTOFMEMORY|  
|Testo del messaggio|Memoria insufficiente per il provider.|  
  
## <a name="explanation"></a>Spiegazione  
La condizione di memoria di sistema insufficiente ha causato l'esaurimento della memoria del provider OLE DB.  
  
## <a name="user-action"></a>Azione dell'utente  
Riavviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se l'operazione non è risolutiva, riavviare il computer. Se il problema persiste, raccogliere gli eventi di traccia OLE DB mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e fornire questi dati al Servizio Supporto Tecnico Clienti Microsoft per il provider OLE DB.  
  
## <a name="see-also"></a>Vedere anche  
[Modelli e autorizzazioni di SQL Server Profiler](~/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
[SQL Server Native Client &#40;OLE DB&#41;](~/relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  

