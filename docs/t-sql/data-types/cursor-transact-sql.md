---
title: cursori (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4b0b96a3bc147f51102fa10f2dff96b7f1761759
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
  
  

