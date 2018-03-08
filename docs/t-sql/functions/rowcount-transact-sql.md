---
title: '@@ROWCOUNT (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 08/29/2017
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
- '@@ROWCOUNT_TSQL'
- '@@ROWCOUNT'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@ROWCOUNT function'
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 97a47998-81d9-4331-a244-9eb8b6fe4a56
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: dd23d2af2f35dd0d76557723639f1870ee22e0ee
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40rowcount-transact-sql"></a>&#x40;&#x40;Conteggio delle righe (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il numero di righe modificate dall'ultima istruzione. Se il numero di righe è superiore a 2 miliardi, utilizzare [ROWCOUNT_BIG](../../t-sql/functions/rowcount-big-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@ROWCOUNT  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]le istruzioni possono impostare il valore di @@ROWCOUNT nei modi seguenti:  
  
-   Impostare@ROWCOUNT al numero di righe modificate o lette. Le righe possono venire inviate al client o meno.  
  
-   Mantenere@ROWCOUNT dall'esecuzione dell'istruzione precedente.  
  
-   Reimpostare@ROWCOUNT su 0 ma non restituiscono il valore al client.  
  
 Le istruzioni che effettuano un'assegnazione semplice impostare sempre il @@ROWCOUNT valore su 1. Non vengono inviate righe al client. Esempi di queste istruzioni sono: SET @*local_variable*, RETURN, READTEXT e selezione senza query istruzioni quali SELECT GETDATE () o SELECT **'***testo generico* **'**.  
  
 Le istruzioni che effettuano un'assegnazione in una query o utilizzano RETURN in un set di query di @@ROWCOUNT valore per il numero di righe modificate o lette dalla query, ad esempio: SELECT @*local_variable* = c1 FROM t1.  
  
 Data manipulation language (DML) istruzioni set il @@ROWCOUNT valore per il numero di righe interessate dalla query e restituisce tale valore al client. Le istruzioni DML possono non inviare righe al client.  
  
 DECLARE CURSOR e FETCH impostare il @@ROWCOUNT valore su 1.  
  
 Le istruzioni EXECUTE mantengono il precedente @@ROWCOUNT.  
  
 Le istruzioni, ad esempio, utilizzare SET \<opzione >, DEALLOCATE CURSOR, CLOSE CURSOR, BEGIN TRANSACTION o COMMIT TRANSACTION Reimposta il valore ROWCOUNT su 0.  
  
 Le stored procedure compilate in modo nativo mantenere precedente @@ROWCOUNT. [!INCLUDE[tsql](../../includes/tsql-md.md)]le istruzioni all'interno di stored procedure compilate in modo nativo non si impostano@ROWCOUNT. Per ulteriori informazioni, vedere [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eseguita un'istruzione `UPDATE` e viene utilizzato `@@ROWCOUNT` per rilevare se sono state modificate righe.  
  
```  
USE AdventureWorks2012;  
GO  
UPDATE HumanResources.Employee   
SET JobTitle = N'Executive'  
WHERE NationalIDNumber = 123456789  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were updated';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [SET ROWCOUNT &#40; Transact-SQL &#41;](../../t-sql/statements/set-rowcount-transact-sql.md)  
  
  
