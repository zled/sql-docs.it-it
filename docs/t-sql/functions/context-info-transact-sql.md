---
title: CONTEXT_INFO (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONTEXT_INFO_TSQL
- CONTEXT_INFO
dev_langs:
- TSQL
helpviewer_keywords:
- CONTEXT_INFO function
- Multiple Active Result Sets
- context information [SQL Server]
- MARS [SQL Server]
- session context information [SQL Server]
ms.assetid: 571320f5-7228-4b0e-9d01-ab732d2d1eab
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 98a275622a809b3856b66d825cd48e2698fea51b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="contextinfo--transact-sql"></a>CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il valore di **context_info** impostato per la sessione o il batch corrente usando l'istruzione [SET CONTEXT_INFO](../../t-sql/statements/set-context-info-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CONTEXT_INFO()  
```  
  
## <a name="return-value"></a>Valore restituito
Valore di **context_info**.
  
Se **context_info** non è stato impostato:
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce NULL.  
-   In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] restituisce un GUID univoco specifico della sessione.  
  
## <a name="remarks"></a>Remarks  
Grazie alla funzionalità MARS (Multiple Active Result Set) le applicazioni sono in grado di eseguire più batch o richieste contemporaneamente utilizzando la stessa connessione. Se uno dei batch in una connessione MARS esegue l'istruzione SET CONTEXT_INFO, il nuovo valore del contesto viene restituito dalla funzione CONTEXT_INFO quando viene eseguita nello stesso batch dell'istruzione SET. Il nuovo valore non viene restituito dalla funzione CONTEXT_INFO eseguita in uno o più degli altri batch nella connessione a meno che tali batch non siano stati avviati dopo il completamento del batch che ha eseguito l'istruzione SET.
  
## <a name="permissions"></a>Autorizzazioni  
Non sono richieste autorizzazioni particolari. Le informazioni sul contesto sono archiviate anche nelle viste di sistema **sys.dm_exec_requests**, **sys.dm_exec_sessions** e **sys.sysprocesses**, ma per l'esecuzione di query direttamente su tali viste sono necessarie direttamente le autorizzazioni SELECT e VIEW SERVER STATE.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene impostato il valore di **context_info** su `0x1256698456` e quindi viene usata la funzione `CONTEXT_INFO` per recuperare il valore.
  
```sql
SET CONTEXT_INFO 0x1256698456;  
GO  
SELECT CONTEXT_INFO();  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[SET CONTEXT_INFO &#40;Transact-SQL&#41;](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
