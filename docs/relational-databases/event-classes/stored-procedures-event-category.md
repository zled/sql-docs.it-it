---
title: Categoria di eventi Stored procedure | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e155df20d6345e8b3bbc34566ba702f464cd196e
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34328952"
---
# <a name="stored-procedures-event-category"></a>Categoria di eventi Stored procedure
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La categoria di eventi **Stored Procedure** contiene eventi stored procedure generali.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Classe di evento RPC:Completed](../../relational-databases/event-classes/rpc-completed-event-class.md)|Indica il completamento di una chiamata di procedura remota (RPC).|  
|[Classe di evento PreConnect:Completed](../../relational-databases/event-classes/preconnect-completed-event-class.md)|Indica la fine dell'esecuzione di una funzione di classificazione di Resource Governor.|  
|[Classe di evento PreConnect:Starting](../../relational-databases/event-classes/preconnect-starting-event-class.md)|Indica l'avvio dell'esecuzione di una funzione di classificazione di Resource Governor.|  
|[Classe di evento RPC Output Parameter](../../relational-databases/event-classes/rpc-output-parameter-event-class.md)|Traccia i valori di output dei parametri delle chiamate di procedura remota dopo l'esecuzione.|  
|[Classe di evento RPC:Starting](../../relational-databases/event-classes/rpc-starting-event-class.md)|Indica l'avvio di una chiamata di procedura remota.|  
|[Classe di evento SP:CacheHit](../../relational-databases/event-classes/sp-cachehit-event-class.md)|Indica la presenza della stored procedure nella cache.|  
|[Classe di evento SP:CacheInsert](../../relational-databases/event-classes/sp-cacheinsert-event-class.md)|Indica l'inserimento della stored procedure nella cache.|  
|[Classe di evento SP:CacheMiss](../../relational-databases/event-classes/sp-cachemiss-event-class.md)|Indica l'assenza della stored procedure nella cache.|  
|[Classe di evento SP:CacheRemove](../../relational-databases/event-classes/sp-cacheremove-event-class.md)|Indica l'eliminazione della stored procedure dalla cache.|  
|[Classe di evento SP:Completed](../../relational-databases/event-classes/sp-completed-event-class.md)|Indica il completamento dell'esecuzione della stored procedure.|  
|[Classe di evento SP:Recompile](../../relational-databases/event-classes/sp-recompile-event-class.md)|Indica la ricompilazione della stored procedure.|  
|[Classe di evento SP:Starting](../../relational-databases/event-classes/sp-starting-event-class.md)|Indica l'avvio dell'esecuzione della stored procedure.|  
|[Classe di evento SP:StmtCompleted](../../relational-databases/event-classes/sp-stmtcompleted-event-class.md)|Indica il completamento di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] in una stored procedure.|  
|[Classe di evento SP:StmtStarting](../../relational-databases/event-classes/sp-stmtstarting-event-class.md)|Indica l'avvio di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] in una stored procedure.|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
