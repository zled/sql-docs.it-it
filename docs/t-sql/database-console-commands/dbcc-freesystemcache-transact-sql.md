---
title: DBCC FREESYSTEMCACHE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREESYSTEMCACHE_TSQL
- DBCC_FREESYSTEMCACHE_TSQL
- DBCC FREESYSTEMCACHE
- FREESYSTEMCACHE
dev_langs: TSQL
helpviewer_keywords:
- clearing unused cache entries
- DBCC FREESYSTEMCACHE statement
- unused cache entries
- releasing unused cache entries
- freeing unused cache entries
- cleaning unused cache entries
ms.assetid: 4b5c460b-e4ad-404a-b4ca-d65aba38ebbb
caps.latest.revision: "35"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d5c6924da3ef9ac85683c857c786337b9d9b978b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-freesystemcache-transact-sql"></a>DBCC FREESYSTEMCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Rilascia tutte le voci non utilizzate da tutte le cache. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] rimuove in background le voci non utilizzate nella cache per liberare memoria per le voci correnti. Tuttavia, è possibile utilizzare questo comando per rimuovere manualmente le voci inutilizzate da tutte le cache o da una cache di pool di Resource Governor specificata.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
```sql
DBCC FREESYSTEMCACHE   
    ( 'ALL' [, pool_name ] )   
    [WITH   
    { [ MARK_IN_USE_FOR_REMOVAL ] , [ NO_INFOMSGS ]  }  
    ]  
```  
  
## <a name="arguments"></a>Argomenti  
 ('Tutte' [,*pool_name* ])  
 ALL specifica tutte le cache supportate.  
 *pool_name* specifica una cache di pool di Resource Governor. Verranno liberate solo le voci associate a questo pool.  
  
 MARK_IN_USE_FOR_REMOVAL  
 Libera in modalità asincrona le voci utilizzate dalle relative cache non appena tali voci risultano inutilizzate. Le nuove voci create nella cache dopo l'esecuzione di DBCC FREESYSTEMCACHE WITH MARK_IN_USE_FOR_REMOVAL rimangono invariate.  
  
 NO_INFOMSGS  
 Disattiva tutti i messaggi informativi.  
  
## <a name="remarks"></a>Osservazioni  
L'esecuzione di DBCC FREESYSTEMCACHE comporta la cancellazione della cache dei piani per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La cancellazione della cache dei piani comporta la ricompilazione di tutti i piani di esecuzione successivi e può causare un peggioramento improvviso e temporaneo delle prestazioni di esecuzione delle query. Il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene il messaggio informativo seguente per ogni archivio cache cancellato nella cache dei piani: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato %d occorrenza/e di scaricamento dell'archivio cache '%s' (parte della cache dei piani) a causa di operazioni 'DBCC FREEPROCCACHE' o 'DBCC FREESYSTEMCACHE'". Questo messaggio viene registrato ogni cinque minuti per tutta la durata dello scaricamento della cache.

## <a name="result-sets"></a>Set di risultati  
DBCC FREESYSTEMCACHE restituisce: "esecuzione DBCC completata. Se sono stati visualizzati messaggi di errore DBCC, rivolgersi all'amministratore di sistema".
  
## <a name="permissions"></a>Autorizzazioni  
È necessario disporre dell'autorizzazione ALTER SERVER STATE per il server.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-releasing-unused-cache-entries-from-a-resource-governor-pool-cache"></a>A. Rilascio delle voci inutilizzate da una cache di pool di Resource Governor  
Nell'esempio seguente viene illustrato come pulire le cache dedicate a un pool di risorse di Resource Governor specificato.
  
```sql
-- Clean all the caches with entries specific to the resource pool named "default".  
DBCC FREESYSTEMCACHE ('ALL', default);  
```  
  
### <a name="b-releasing-entries-from-their-respective-caches-after-they-become-unused"></a>B. Rilascio delle voci dalle relative cache non appena tali voci diventano inutilizzate  
Nell'esempio seguente viene utilizzata la clausola MARK_IN_USE_FOR_REMOVAL per rilasciare le voci da tutte le cache correnti non appena le voci diventano inutilizzate.
  
```sql
DBCC FREESYSTEMCACHE ('ALL') WITH MARK_IN_USE_FOR_REMOVAL;  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)  
[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-freesessioncache-transact-sql.md)  
[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)
  
  
