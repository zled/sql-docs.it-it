---
title: SET CONTEXT_INFO (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_CONTEXT_INFO_TSQL
- SET CONTEXT_INFO
dev_langs: TSQL
helpviewer_keywords:
- context information [SQL Server]
- CONTEXT_INFO option
- SET CONTEXT_INFO statement
ms.assetid: a0b7b9f3-dbda-4350-a274-bd9ecd5c0a74
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4a93e9f40690f37c0c161c635aea95589d47ef1e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="set-contextinfo-transact-sql"></a>SET CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Associa fino a 128 byte di informazioni binarie alla sessione o connessione corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET CONTEXT_INFO { binary_str | @binary_var }  
```  
  
## <a name="arguments"></a>Argomenti  
 *binary_str*  
 È un **binario** costante o una costante che è implicitamente convertibile in **binario**, per associare la sessione o connessione corrente.  
  
 **@***binary_var*  
 È un **varbinary** o **binario** variabile che contiene un valore contestuale da associare alla sessione corrente o di una connessione.  
  
## <a name="remarks"></a>Osservazioni  
 Il modo preferito per recuperare informazioni sul contesto per la sessione corrente consiste nell'utilizzare la funzione CONTEXT_INFO. Informazioni sul contesto di sessione viene inoltre archiviati nel **context_info** colonne nelle viste di sistema seguente:  
  
-   **sys.dm_exec_requests**  
  
-   **sys.dm_exec_sessions**  
  
-   **sys.sysprocesses**  
  
 Non è possibile specificare l'istruzione SET CONTEXT_INFO in una funzione definita dall'utente. Per l'istruzione SET CONTEXT_INFO inoltre non è possibile specificare un valore Null perché la tabella sysprocesses non ammette valori Null.  
  
 L'opzione SET CONTEXT_INFO non supporta espressioni che non siano costanti o nomi di variabili. Per impostare le informazioni di contesto al risultato di una chiamata di funzione, è innanzitutto necessario inserire il risultato della chiamata di funzione in un **binario** o **varbinary** variabile.  
  
 Quando viene eseguita l'istruzione SET CONTEXT_INFO in una stored procedure o in un trigger, a differenza di altre istruzioni SET il nuovo valore impostato per le informazioni sul contesto viene mantenuto anche dopo il completamento della stored procedure o del trigger.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-setting-context-information-by-using-a-constant"></a>A. Impostazione delle informazioni relative al contesto tramite una costante  
 Nell'esempio seguente viene illustrato l'utilizzo della costante `SET CONTEXT_INFO`, mediante l'impostazione del valore e la visualizzazione dei risultati. Si noti che per l'esecuzione di una query su `sys.dm_exec_sessions` sono necessarie le autorizzazioni SELECT e VIEW SERVER STATE, mentre non lo sono per l'utilizzo della funzione CONTEXT_INFO.  
  
```  
SET CONTEXT_INFO 0x01010101;  
GO  
SELECT context_info   
FROM sys.dm_exec_sessions  
WHERE session_id = @@SPID;  
GO  
```  
  
### <a name="b-setting-context-information-by-using-a-function"></a>B. Impostazione delle informazioni relative al contesto tramite una funzione  
 Nell'esempio seguente viene illustrato come utilizzare l'output di una funzione per impostare il valore di contesto, in cui il valore dalla funzione necessario inserirlo in un **binario** variabile.  
  
```  
DECLARE @BinVar varbinary(128);  
SET @BinVar = CAST(REPLICATE( 0x20, 128 ) AS varbinary(128) );  
SET CONTEXT_INFO @BinVar;  
  
SELECT CONTEXT_INFO() AS MyContextInfo;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [Sys.dm exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [Sys.dm exec_sessions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)  
  
  
