---
title: Sys.dm exec_input_buffer (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_input_buffer
- sys.dm_exec_input_buffer _tsql
- dm_exec_input_buffer
- dm_exec_input_buffer_tsql
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_input_buffer dynamic management function
ms.assetid: fb34a560-bde9-4ad9-aa96-0d4baa4fc104
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 147ac7627ba30a8a249e00cbf03e37887368de09
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="sysdmexecinputbuffer-transact-sql"></a>Sys.dm exec_input_buffer (Transact-SQL)
[!INCLUDE[tsql-appliesto-2014sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2014sp2-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sulle istruzioni inviate a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_exec_input_buffer ( session_id , request_id )
```  
  
## <a name="arguments"></a>Argomenti  
*session_id*  
L'id di sessione è in esecuzione il batch da ricercare. *session_id* è **smallint**. *session_id* può essere ottenuto dagli oggetti a gestione dinamica seguenti:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)   
  
*request_id*  
Il request_id da [Sys.dm exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md). *request_id* è **int**.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**event_type**|**nvarchar(256)**|Il tipo di evento nel buffer di input per il valore spid specificato.|  
|**parametri**|**smallint**|I parametri forniti per l'istruzione.|  
|**event_info**|**nvarchar(max)**|Il testo dell'istruzione nel buffer di input per il valore spid specificato.|  
  
## <a name="permissions"></a>Autorizzazioni  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se l'utente dispone dell'autorizzazione VIEW SERVER STATE, l'utente vedrà le sessioni in esecuzione tutti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; in caso contrario, l'utente vedrà solo la sessione corrente.  
  
 In [!INCLUDE[ssSDS](../../includes/sssds-md.md)], se l'utente è il proprietario del database, l'utente vedrà le sessioni in esecuzione tutti nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)]; in caso contrario, l'utente vedrà solo la sessione corrente.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione a gestione dinamica può essere utilizzata in combinazione con Sys.dm exec_sessions o Sys.dm exec_requests attraverso la pratica **CROSS APPLY**.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-example"></a>A. Esempio semplice  
 Nell'esempio seguente viene illustrato come passare un id di sessione (SPID) e un id di richiesta alla funzione.  
  
```sql  
SELECT * FROM sys.dm_exec_input_buffer (52, 0);
GO
```  
  
### <a name="b-using-cross-apply-to-additional-information"></a>B. Tra si applicano alle informazioni aggiuntive  
 Nell'esempio seguente vengono elencati i buffer di input per le sessioni con id di sessione superiore a 50.  
  
```sql  
SELECT es.session_id, ib.event_info   
FROM sys.dm_exec_sessions AS es  
CROSS APPLY sys.dm_exec_input_buffer(es.session_id, NULL) AS ib  
WHERE es.session_id > 50;
GO
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40; relative all'esecuzione Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Sys.dm exec_sessions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [Sys.dm exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [DBCC INPUTBUFFER &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)  
