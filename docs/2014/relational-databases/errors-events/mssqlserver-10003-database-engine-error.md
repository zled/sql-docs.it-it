---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3f93a6fcdb5b5d5ac98d834f96e6d2689a5765f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156712"
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
 [Modelli e autorizzazioni di SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  