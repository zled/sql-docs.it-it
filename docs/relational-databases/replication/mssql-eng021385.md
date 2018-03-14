---
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c99c72b377f10999f55ad48a23e2b522308d0a2a
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng021385"></a>MSSQL_ENG021385
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21385|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Lo snapshot non è in grado di elaborare la pubblicazione '%s', probabilmente perché sono in corso attività di modifica dello schema o di aggiunta di nuovi articoli.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore viene generato se l'agente snapshot viene eseguito quando il database di pubblicazione è sottoposto a modifiche, ad esempio l'aggiunta o l'eliminazione di articoli e l'esecuzione di modifiche dello schema negli oggetti pubblicati.  
  
## <a name="user-action"></a>Azione dell'utente  
 Riavviare l'agente snapshot dopo che sono state apportate tutte le modifiche al database di pubblicazione. Per altre informazioni, vedere [Avviare e arrestare un agente di replica &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [Concetti di base relativi ai file eseguibili dell'agente di replica](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
