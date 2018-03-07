---
title: CURRENT_TRANSACTION_ID (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURRENT_TRANSACTION_ID
- CURRENT_TRANSACTION_ID_TSQL
- sys.CURRENT_TRANSACTION_ID
- sys.CURRENT_TRANSACTION_ID_TSQL
helpviewer_keywords:
- CURRENT_TRANSACTION_ID function
ms.assetid: 82cd9f92-d935-45a0-a433-620d6e15b467
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ef8f593f50ce1d27642d1d179a57bebb2b4473e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="currenttransactionid-transact-sql"></a>CURRENT_TRANSACTION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Restituisce l'ID della transazione della transazione corrente nella sessione corrente.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CURRENT_TRANSACTION_ID( )  
  
```  
  
## <a name="return-types"></a>Tipi restituiti
**bigint**
  
## <a name="return-value"></a>Valore restituito  
ID della transazione della transazione corrente nella sessione corrente, eseguita da [sys.dm_tran_current_transaction &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-tran-current-transaction-transact-sql.md).
  
## <a name="permissions"></a>Permissions  
Qualsiasi utente può restituire l'ID della transazione della sessione corrente.
  
## <a name="examples"></a>Esempi  
L'esempio seguente restituisce l'ID della transazione della sessione corrente:
  
```sql
SELECT CURRENT_TRANSACTION_ID();  
```  
  
## <a name="see-also"></a>Vedere anche
[sp_set_session_context &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)  
[SESSION_CONTEXT &#40; Transact-SQL &#41;](../../t-sql/functions/session-context-transact-sql.md)  
[Sicurezza a livello di riga](../../relational-databases/security/row-level-security.md)  
[CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)  
[SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
