---
title: SESSION_CONTEXT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/22/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SESSION_CONTEXT
- sys.SESSION_CONTEXT
- SESSION_CONTEXT_TSQL
- sys.SESSION_CONTEXT_TSQL
helpviewer_keywords: SESSION_CONTEXT function
ms.assetid: b6bdbc54-331a-43cc-ab3d-3872d6a12100
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3bf9da8f88f28b71e4133900384f27d37729d695
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sessioncontext-transact-sql"></a>SESSION_CONTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Restituisce il valore della chiave specificata nel contesto della sessione corrente. Il valore viene impostato utilizzando il [sp_set_session_context &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md) procedura.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SESSION_CONTEXT(N'key')  
```  
  
## <a name="arguments"></a>Argomenti  
 'key'  
 La chiave (tipo sysname) del valore da recuperare.  
  
## <a name="return-type"></a>Tipo restituito  
 **sql_variant**  
  
## <a name="return-value"></a>Valore restituito  
 Il valore associato alla chiave specificata nel contesto della sessione oppure NULL se non è stato impostato alcun valore per tale chiave.  
  
## <a name="permissions"></a>Permissions  
 Qualsiasi utente può leggere il contesto della sessione per la sessione.  
  
## <a name="remarks"></a>Osservazioni  
 Il comportamento di MARS del SESSION_CONTEXT è simile a quello di CONTEXT_INFO. Se un batch MARS imposta una coppia chiave-valore, il nuovo valore non restituirà in altri batch MARS nella stessa connessione, a meno che non sono avviati dopo aver completato il batch che ha impostato il nuovo valore. Se più batch MARS non sono attive su una connessione, non è possibile impostare valori come "read_only". Questo comportamento impedisce race condition e non deterministico su quale valore "wins".  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente imposta il valore di contesto di sessione per la chiave `user_id` 4, e viene utilizzata la **SESSION_CONTEXT** funzione per recuperare il valore.  
  
```  
EXEC sp_set_session_context 'user_id', 4;  
SELECT SESSION_CONTEXT(N'user_id');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_set_session_context &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)   
 [CURRENT_TRANSACTION_ID &#40; Transact-SQL &#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [Sicurezza a livello di riga](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
