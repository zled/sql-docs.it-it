---
title: La funzione PARSENAME (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSENAME_TSQL
- PARSENAME
dev_langs:
- TSQL
helpviewer_keywords:
- PARSENAME function
- parsing [SQL Server], PARSENAME function
- names [SQL Server], objects
- objects [SQL Server], names
- part of object names [SQL Server]
ms.assetid: abf34f99-9ee9-460b-85b2-930ca5c4b5ae
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 5664c0a98663897f1d0a3cfa46e8dabab0d6ef7a
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="parsename-transact-sql"></a>PARSENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Restituisce la parte specificata del nome di un oggetto. Le parti di un oggetto che è possibile recuperare sono il nome dell'oggetto, il nome del proprietario, il nome del database e il nome del server.  
  
> [!NOTE]  
>  La funzione PARSENAME non indica se esiste un oggetto avente il nome specificato. PARSENAME restituisce solo la parte specificata del nome di oggetto specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
PARSENAME ( 'object_name' , object_piece )   
```  
  
## <a name="arguments"></a>Argomenti  
 '*object_name*'  
 Nome dell'oggetto per cui recuperare la parte specificata. *object_name* è **sysname**. Questo parametro rappresenta un nome di oggetto che può essere qualificato facoltativamente. Se vengono qualificate tutte le parti del nome dell'oggetto, il nome può essere costituito da quattro parti, ovvero nome del server, nome del database, nome del proprietario e nome dell'oggetto.  
  
 *object_piece*  
 Parte dell'oggetto da restituire. *object_piece* è di tipo **int**e i valori sono i seguenti:  
  
 1 = nome dell'oggetto  
  
 2 = nome dello schema  
  
 3 = nome del database  
  
 4 = nome del server  
  
## <a name="return-types"></a>Tipi restituiti  
 **nchar**  
  
## <a name="remarks"></a>Osservazioni  
 PARSENAME restituisce NULL se si verifica una delle condizioni seguenti:  
  
-   Entrambi *object_name* o *object_piece* è NULL.  
  
-   Si verifica un errore di sintassi.  
  
 La parte dell'oggetto richiesta ha una lunghezza pari a 0 e non è un valido [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificatore. Se la lunghezza del nome dell'oggetto è pari a 0, il nome completo risulta non valido.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato `PARSENAME` per restituire informazioni sulla tabella `Person` nel database `AdventureWorks2012`.  
  
```  
-- Uses AdventureWorks  
  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```
Object Name
------------------------------
DimCustomer

(1 row(s) affected)

Schema Name
------------------------------
dbo

(1 row(s) affected)

Database Name
------------------------------
AdventureWorksPDW2012

(1 row(s) affected)

Server Name
------------------------------
(null)

(1 row(s) affected)
```
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Funzioni di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


