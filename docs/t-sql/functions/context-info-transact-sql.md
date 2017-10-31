---
title: CONTEXT_INFO (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd261b2f7f1cc4234792bec66c3662d6d9b8dcd8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="contextinfo--transact-sql"></a>CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il **context_info** valore impostato per il batch o la sessione corrente tramite il [SET CONTEXT_INFO](../../t-sql/statements/set-context-info-transact-sql.md) istruzione.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CONTEXT_INFO()  
```  
  
## <a name="return-value"></a>Valore restituito
Il valore di **context_info**.
  
Se **context_info** non è stato impostato:
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce NULL.  
-   In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] restituisce un GUID specifico di sessione univoco.  
  
## <a name="remarks"></a>Osservazioni  
Grazie alla funzionalità MARS (Multiple Active Result Set) le applicazioni sono in grado di eseguire più batch o richieste contemporaneamente utilizzando la stessa connessione. Se uno dei batch in una connessione MARS esegue l'istruzione SET CONTEXT_INFO, il nuovo valore del contesto viene restituito dalla funzione CONTEXT_INFO quando viene eseguita nello stesso batch dell'istruzione SET. Il nuovo valore non viene restituito dalla funzione CONTEXT_INFO eseguita in uno o più degli altri batch nella connessione a meno che tali batch non siano stati avviati dopo il completamento del batch che ha eseguito l'istruzione SET.
  
## <a name="permissions"></a>Permissions  
Non sono richieste autorizzazioni particolari. Le informazioni di contesto vengono archiviate anche nel **Sys.dm exec_requests**, **Sys.dm exec_sessions**, e **Sys. sysprocesses** viste di sistema, ma l'esecuzione di query direttamente le viste richiede le autorizzazioni SELECT e VIEW SERVER STATE.
  
## <a name="examples"></a>Esempi  
L'esempio seguente viene impostato il **context_info** valore `0x1256698456`e quindi utilizza il `CONTEXT_INFO` funzione per recuperare il valore.
  
```sql
SET CONTEXT_INFO 0x1256698456;  
GO  
SELECT CONTEXT_INFO();  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)
  
  

