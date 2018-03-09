---
title: MSSQLSERVER_3431 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8b5fad28f6df88f0c245d50d65c78596e64e31c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3431"></a>MSSQLSERVER_3431
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3431|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|UNRESOLVED_XACT|  
|Testo del messaggio|Impossibile recuperare il database '%.*ls' (ID di database %d) perché i risultati di una transazione non sono stati risolti. Le transazioni di Microsoft Distributed Transaction Coordinator (MS DTC) sono state preparate, ma l'applicazione non è stata in grado di determinarne la risoluzione. Per risolvere il problema, correggere MS DTC, eseguire un ripristino da un backup completo oppure correggere il database.|  
  
## <a name="explanation"></a>Spiegazione  
Una o più transazioni distribuite in cui viene utilizzato [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) sono risultate incomplete alla chiusura del database. Non è stato possibile recuperare il database perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di completare le transazioni o di eseguirne il rollback senza disporre di ulteriori informazioni restituite da MS DTC.  
  
## <a name="user-action"></a>Azione dell'utente  
Per recuperare il database, è necessario risolvere dapprima il problema relativo a MS DTC. Per analizzare il problema relativo a MS DTC, esaminare i registri eventi di Windows. Se non è possibile risolvere il problema e recuperare il database, ripristinare un backup del database.  
  
