---
title: ISJSON (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISJSON
- ISJSON_TSQL
helpviewer_keywords:
- ISJSON function
- JSON, validating
ms.assetid: c836f3d3-3e17-44ae-92bf-f341918896c3
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0ecbcc4ced2b9503ec9161f7aa93a1a5266960ef
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Verifica se una stringa contiene JSON valido.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
ISJSON ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Stringa da testare.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce 1 se la stringa contiene JSON valido; in caso contrario, restituisce 0. Restituisce null se *espressione* è null.  
  
 Non restituisce errori.  
  
## <a name="remarks"></a>Osservazioni  
 **ISJSON** non verifica l'univocità delle chiavi allo stesso livello.  
  
## <a name="examples"></a>Esempi  
  
### <a name="example-1"></a>Esempio 1  
Nell'esempio seguente viene eseguito un blocco di istruzioni in modo condizionale se il valore del parametro `@param` include contenuto JSON valido.  
  
```sql  
DECLARE @param <data type>
SET @param = <value>

IF (ISJSON(@param) > 0)  
BEGIN  
     -- Do something with the valid JSON value of @param.  
END
 
```  
  
### <a name="example-2"></a>Esempio 2  
L'esempio seguente restituisce le righe in cui la colonna `json_col` include contenuto JSON valido.  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  
  
## <a name="see-also"></a>Vedere anche  
 [I dati JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
