---
title: sp_trace_setfilter (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_trace_setfilter
- sp_trace_setfilter_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_trace_setfilter
ms.assetid: 11e7c7ac-a581-4a64-bb15-9272d5c1f7ac
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 01394d92e71c69de60bbf2015ea58c4c8d53f0a4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sptracesetfilter-transact-sql"></a>sp_trace_setfilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Applica un filtro a una traccia. **sp_trace_setfilter** può essere eseguita solo su tracce esistenti che sono state arrestate (*stato* è **0**). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Restituisce un errore se questa stored procedure viene eseguita su una traccia che non esiste o il cui *stato* non **0**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, usare Eventi estesi.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_trace_setfilter [ @traceid = ] trace_id   
          , [ @columnid = ] column_id  
          , [ @logical_operator = ] logical_operator  
          , [ @comparison_operator = ] comparison_operator  
          , [ @value = ] value  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@traceid=** ] *trace_id*  
 ID della traccia a cui applicare il filtro. *trace_id* è **int**, non prevede alcun valore predefinito. L'utente può *trace_id* valore per identificare, modificare e controllare la traccia.  
  
 [  **@columnid=** ] *column_id*  
 ID della colonna a cui applicare il filtro. *column_id* è **int**, non prevede alcun valore predefinito. Se *column_id* è NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cancella tutti i filtri per la traccia specificata.  
  
 [  **@logical_operator**  =] *logical_operator*  
 Specifica se l'operazione di AND (**0**) o OR (**1**) viene applicato l'operatore. *logical_operator* è **int**, non prevede alcun valore predefinito.  
  
 [  **@comparison_operator=** ] *operatore_confronto*  
 Specifica il tipo di confronto da eseguire. *operatore_confronto* è **int**, non prevede alcun valore predefinito. Nella tabella seguente vengono descritti gli operatori di confronto e i valori che li rappresentano.  
  
|Valore|Operatore di confronto|  
|-----------|-------------------------|  
|**0**|= (uguaglianza)|  
|**1**|<> (disuguaglianza)|  
|**2**|> (maggiore di)|  
|**3**|< (minore di)|  
|**4**|>= (maggiore o uguale a)|  
|**5**|<= (minore o uguale a)|  
|**6**|LIKE|  
|**7**|Non simile a|  
  
 [  **@value=** ] *valore*  
 Specifica il valore in base a cui applicare il filtro. Il tipo di dati *valore* deve corrispondere al tipo di dati della colonna da filtrare. Ad esempio, se il filtro è impostato su una colonna di ID di oggetto che è un **int** tipo di dati, *valore* deve essere **int**. Se *valore* è **nvarchar** o **varbinary**, può avere una lunghezza massima di 8000.  
  
 Quando l'operatore di confronto è LIKE o NOT LIKE, l'operatore logico può includere "%" o un filtro appropriato per l'operazione LIKE.  
  
 È possibile specificare NULL per *valore* per filtrare gli eventi con valori di colonna NULL. Solo **0** (= uguaglianza) e **1** gli operatori (<> non uguale) sono validi con valori NULL. In questo caso, tali operatori sono equivalenti agli operatori [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL e IS NOT NULL.  
  
 Per applicare il filtro in un intervallo di valori di colonna, **sp_trace_setfilter** deve essere eseguita due volte, una volta con un maggiore-di-or-equals ('> ='), operatore di confronto e una seconda volta con un minore di-di-or-equals ('< =') (operatore) .  
  
 Per ulteriori informazioni sui tipi di dati colonna di dati, vedere il [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nella tabella seguente vengono descritti i possibili valori di codice visualizzati al completamento della stored procedure.  
  
|Codice restituito|Description|  
|-----------------|-----------------|  
|0|Nessun errore.|  
|1|Errore sconosciuto.|  
|2|La traccia è in esecuzione. Se si modifica la traccia mentre è in esecuzione, viene generato un errore.|  
|4|La colonna specificata non è valida.|  
|5|La colonna specificata non supporta l'applicazione di filtri. Questo valore viene restituito solo da **sp_trace_setfilter**.|  
|6|L'operatore di confronto specificato non è valido.|  
|7|L'operatore logico specificato non è valido.|  
|9|L'handle di traccia specificato non è valido.|  
|13|Memoria esaurita. Restituito quando la quantità di memoria disponibile non è sufficiente per eseguire l'azione specificata.|  
|16|Funzione non valida per la traccia.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_trace_setfilter** è un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure che esegue molte delle azioni eseguite dalle stored procedure estese disponibili nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilizzare **sp_trace_setfilter** anziché il **xp_trace_set\*filtro** delle stored procedure estese per creare, applicare, rimuovere o manipolare i filtri applicati alle tracce. Per ulteriori informazioni, vedere [filtrare una traccia](../../relational-databases/sql-trace/filter-a-trace.md).  
  
 Tutti i filtri per una determinata colonna devono essere abilitati contemporaneamente in un'esecuzione di **sp_trace_setfilter**. Se, ad esempio, un utente desidera applicare due filtri alla colonna dei nomi di applicazione e un filtro alla colonna dei nomi utente, deve specificare i filtri per il nome dell'applicazione in sequenza. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore se l'utente tenta di specificare un filtro per il nome dell'applicazione nella chiamata a un stored procedure, seguito da un filtro per il nome utente e quindi da un altro filtro per il nome dell'applicazione.  
  
 I parametri di traccia SQL tutte le stored procedure (**sp_trace_xx**) sono fortemente tipizzati. Se tali parametri non vengono chiamati con i tipi di dati corretti per i parametri di input, come indicato nella descrizione dell'argomento, la stored procedure restituisce un errore.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve disporre delle autorizzazioni ALTER TRACE.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono impostati tre filtri in Trace `1`. I filtri `N'SQLT%'` e `N'MS%'` vengono applicati alla colonna `AppName`, valore `10`, tramite l'operatore di confronto "`LIKE`". Il filtro `N'joe'` viene applicato a una colonna diversa, ovvero `UserName`, valore `11`, tramite l'operatore di confronto "`EQUAL`".  
  
```  
sp_trace_setfilter  1, 10, 0, 6, N'SQLT%';  
sp_trace_setfilter  1, 10, 0, 6, N'MS%';  
sp_trace_setfilter  1, 11, 0, 0, N'joe';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Traccia SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
