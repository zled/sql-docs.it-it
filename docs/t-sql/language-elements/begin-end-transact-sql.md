---
title: BEGIN...END (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BEGIN
- BEGIN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- BEGIN statement
- control-of-flow language [SQL Server], BEGIN...END statement
- BEGIN...END keyword
- grouping statements, BEGIN...END statement
- executing Transact-SQL statements together [SQL Server]
- statements [SQL Server], grouping
ms.assetid: fc2c7f76-f1f9-4f91-beef-bc8ef0da2feb
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 660e238a453c7438f726847c8c3ce0811c0731ea
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="beginend-transact-sql"></a>BEGIN...END (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Include una serie di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] per consentire l'esecuzione di un gruppo di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)]. BEGIN ed END sono parole chiave del linguaggio per il controllo di flusso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
BEGIN  
    { sql_statement | statement_block }   
END  
```  
  
## <a name="arguments"></a>Argomenti  
 { *sql_statement* | *statement_block* }  
 Qualsiasi istruzione o raggruppamento di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] valide definito mediante l'utilizzo di un blocco di istruzioni.  
  
## <a name="remarks"></a>Osservazioni  
 I blocchi BEGIN...END possono essere nidificati.  
  
 Tutte le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] sono valide all'interno di un blocco BEGIN...END. Alcune istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)], tuttavia, non devono essere raggruppate nello stesso batch o blocco di istruzioni.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente `BEGIN` ed `END` definiscono una serie di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguite insieme. Se il blocco `BEGIN...END` non fosse incluso, verrebbero eseguite entrambe le istruzioni `ROLLBACK TRANSACTION` e verrebbero restituiti entrambi i messaggi `PRINT`.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
GO  
IF @@TRANCOUNT = 0  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM Person.Person WHERE LastName = 'Adams';  
    ROLLBACK TRANSACTION;  
    PRINT N'Rolling back the transaction two times would cause an error.';  
END;  
ROLLBACK TRANSACTION;  
PRINT N'Rolled back the transaction.';  
GO  
/*  
Rolled back the transaction.  
*/  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente, `BEGIN` e `END` definire una serie di [!INCLUDE[DWsql](../../includes/dwsql-md.md)] istruzioni che vengono eseguite insieme. Se il `BEGIN...END` blocco non sono inclusi, nell'esempio seguente è in un ciclo continuo.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @Iteration Integer = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams';  
SET @Iteration += 1  
END;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Il controllo di flusso Language &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [END &#40;BEGIN...END&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)  
  
  


