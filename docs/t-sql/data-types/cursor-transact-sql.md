---
title: cursori (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b9fa1c8e8fea6aabf8fe8a0e6e84f82f7220facf
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Tipo di dati per variabili o parametri di OUTPUT di stored procedure che contengono un riferimento a un cursore.
  
## <a name="remarks"></a>Osservazioni  
Le operazioni che è possono fare riferimento a variabili e parametri con un **cursore** sono di tipo di dati:
-   DECLARE  *@local_variable*  e impostare  *@local_variable*  istruzioni.  
-   Istruzioni di cursore OPEN, FETCH, CLOSE e DEALLOCATE.  
-   Parametri di output di stored procedure.  
-   Funzione CURSOR_STATUS.  
-   Il **sp_cursor_list**, **sp_describe_cursor**, **sp_describe_cursor_tables**, e **sp_describe_cursor_columns** system archiviati procedure.  
  
Il **cursor_name** colonna di output di **sp_cursor_list** e **sp_describe_cursor** restituisce il nome della variabile di cursore.
  
Le variabili create con la **cursore** tipo di dati sono ammessi valori null.
  
Il **cursore** tipo di dati non può essere utilizzato per una colonna in un'istruzione CREATE TABLE.
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-status-transact-sql.md)  
[Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DICHIARARE cursore &#40; Transact-SQL &#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
