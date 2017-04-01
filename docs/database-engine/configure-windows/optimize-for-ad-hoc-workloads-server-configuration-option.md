---
title: "ottimizzare per l&#39;opzione di configurazione del server dei carichi di lavoro a hoc | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "optimize for ad hoc workloads - opzione"
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# ottimizzare per l&#39;opzione di configurazione del server dei carichi di lavoro a hoc
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  L'opzione **optimize for ad hoc workloads** consente di migliorare l'efficienza della cache dei piani per carichi di lavoro che contengono molti batch ad hoc a uso singolo. Quando questa opzione viene impostata su 1, alla prima compilazione di un batch il [!INCLUDE[ssDE](../../includes/ssde-md.md)] archivia un piccolo stub del piano compilato nella cache dei piani, anziché il piano compilato completo. In questo modo si riducono le richieste di memoria evitando che la cache dei piani si riempia con piani compilati che non vengono riutilizzati.  
  
 Poiché grazie allo stub del piano compilato il [!INCLUDE[ssDE](../../includes/ssde-md.md)] riconosce che il batch ad hoc è stato compilato in precedenza e ha archiviato solo uno stub del piano compilato, quando il batch viene nuovamente richiamato (compilato o eseguito), il [!INCLUDE[ssDE](../../includes/ssde-md.md)] compila il batch, rimuove lo stub del piano compilato dalla cache dei piani e aggiunge il piano compilato completo alla cache dei piani.  
  
 L'impostazione dell'opzione **optimize for ad hoc workloads** su 1 influisce solo sui nuovi piani, mentre non si applica ai piani già presenti nella cache dei piani.  
  
 Lo stub del piano compilato è uno dei cacheobjtype visualizzato nella vista del catalogo sys.dm_exec_cached_plans. Dispone di handle SQL e del piano univoci. Lo stub del piano compilato non ha un piano di esecuzione associato e l'esecuzione di query per l'handle del piano non restituisce uno showplan XML.  
  
 Con il flag di traccia 8032 è possibile ripristinare i parametri dei limiti di cache all'impostazione RTM di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] che consente, in generale, di aumentare le dimensioni delle cache. Usare questa impostazione quando le voci della cache riutilizzate di frequente non rientrano nella cache e quando l'opzione di configurazione server Ottimizza per carichi di lavoro ad hoc non riesce a risolvere il problema della cache dei piani.  
  
> [!WARNING]  
>  Il flag di traccia 8032 può provocare prestazioni ridotte se cache di grandi dimensioni rendono disponibile meno memoria per altri consumer di memoria, ad esempio il pool di buffer.  
  
## Vedere anche  
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  