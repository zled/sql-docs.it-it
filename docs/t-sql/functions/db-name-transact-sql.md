---
title: Db_name (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DB_NAME
- DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database names [SQL Server], DB_NAME
- names [SQL Server], databases
- viewing database names
- displaying database names
- DB_NAME function
ms.assetid: e21fb33a-a3ea-49b0-bb6b-8f789a675a0e
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5743ccb1374640078a77d84a140e9e5d0fdaef0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbname-transact-sql"></a>DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il nome del database.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DB_NAME ( [ database_id ] )  
```  
  
## <a name="arguments"></a>Argomenti  
*database_id*  
Numero di identificazione (ID) del database da restituire. *database_id* è **int**, non prevede alcun valore predefinito. Se non viene specificato alcun ID, viene restituito il nome del database corrente.
  
## <a name="return-types"></a>Tipi restituiti
**nvarchar (128)**
  
## <a name="permissions"></a>Permissions  
Se il chiamante di **DB_NAME** non è il proprietario del database e il database non è **master** o **tempdb**, le autorizzazioni minime necessarie per visualizzare la riga corrispondente sono Autorizzazione a livello di server ALTER ANY DATABASE o VIEW ANY DATABASE oppure l'autorizzazione CREATE DATABASE nel **master** database. Il database a cui è connesso il chiamante può essere sempre visualizzato in **sys.databases**.
  
> [!IMPORTANT]  
>  Per impostazione predefinita, il ruolo public dispone dell'autorizzazione VIEW ANY DATABASE, consentendo a tutti gli account di accesso visualizzare informazioni sul database. Per bloccare un account di accesso alla possibilità di rilevare un database, revocare l'autorizzazione VIEW ANY DATABASE da public o negare l'autorizzazione VIEW ANY DATABASE per singoli account di accesso.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-current-database-name"></a>A. Restituzione del nome del database corrente  
Nell'esempio seguente viene restituito il nome del database corrente.
  
```sql
SELECT DB_NAME() AS [Current Database];  
GO  
```  
  
### <a name="b-returning-the-database-name-of-a-specified-database-id"></a>B. Restituzione del nome di un database con l'ID specificato  
Nell'esempio seguente viene restituito il nome del database con l'ID `3`.
  
```sql
USE master;  
GO  
SELECT DB_NAME(3)AS [Database Name];  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-return-the-current-database-name"></a>C. Restituire il nome del database corrente  
  
```sql
SELECT DB_NAME() AS [Current Database];  
```  
  
### <a name="d-return-the-name-of-a-database-by-using-the-database-id"></a>D. Restituire il nome di un database utilizzando l'ID del database  
L'esempio seguente restituisce il nome del database e database_id per ogni database.
  
```sql
SELECT DB_NAME(database_id) AS [Database], database_id  
FROM sys.databases;  
```  
  
## <a name="see-also"></a>Vedere anche
[DB_ID &#40; Transact-SQL &#41;](../../t-sql/functions/db-id-transact-sql.md)  
[Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
  
  


