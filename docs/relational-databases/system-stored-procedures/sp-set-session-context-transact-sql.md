---
title: sp_set_session_context (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- sp_set_session_context
- sp_set_session_context_TSQL
- sys.sp_set_session_context
- sys.sp_set_session_context_TSQL
helpviewer_keywords:
- sp_set_session_context
ms.assetid: 7a3a3b2a-1408-4767-a376-c690e3c1fc5b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a55ee31e1f4d9f5f98766550f60a16d3dd56843c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spsetsessioncontext-transact-sql"></a>sp_set_session_context (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Imposta una coppia chiave-valore nel contesto della sessione.  
  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_set_session_context [ @key= ] 'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @key=] 'key'  
 La chiave viene impostata, di tipo **sysname**. La dimensione massima della chiave è 128 byte.  
  
 [ @value=] 'value'  
 Il valore per la chiave specificata, di tipo **sql_variant**. Impostazione di un valore NULL libera la memoria. Le dimensioni massime sono pari a 8.000 byte.  
  
 [ @read_only= ] { 0 | 1 }  
 Un flag di tipo **bit**. Se è 1, quindi il valore per la chiave specificata non può essere modificato nuovamente questa connessione logica. Se 0 (impostazione predefinita), quindi il valore può essere modificato.  
  
## <a name="permissions"></a>Permissions  
 Qualsiasi utente può impostare un contesto di sessione per la sessione.  
  
## <a name="remarks"></a>Osservazioni  
 Analogamente alle altre stored procedure, solo i valori letterali e variabili (non a espressioni o chiamate di funzione) possono essere passate come parametri.  
  
 Le dimensioni totali del contesto della sessione sono limitata a 256 kb. Se impostato un valore che determina il superamento del limite, l'istruzione ha esito negativo. È possibile monitorare l'utilizzo della memoria globale in [Sys.dm os_memory_objects &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).  
  
 È possibile monitorare l'utilizzo della memoria globale eseguendo una query [Sys.dm os_memory_cache_counters &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md) come indicato di seguito:`SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come impostare e restituire quindi una chiave di contesto sessioni denominata lingua con un valore per la lingua inglese.  
  
```  
EXEC sp_set_session_context 'language', 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 Nell'esempio seguente viene illustrato l'utilizzo del flag di sola lettura facoltativo.  
  
```  
EXEC sp_set_session_context 'user_id', 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CURRENT_TRANSACTION_ID &#40; Transact-SQL &#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT &#40;Transact-SQL&#41;](../../t-sql/functions/session-context-transact-sql.md)   
 [Sicurezza a livello di riga](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
