---
title: int, bigint, smallint e tinyint (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 9/8/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bigint_TSQL
- smallint
- bigint
- smallint_TSQL
- tinyint_TSQL
- int_TSQL
- int
- tinyint
dev_langs:
- TSQL
helpviewer_keywords:
- exact numeric data [SQL Server]
- numeric data
- tinyint data type
- int data type
- smallint data type
ms.assetid: 9bda5b0b-2380-4931-a1c8-f362fdefa99b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 2e99ccb97dc5c36f8b7870a042963d6302b3f1eb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="int-bigint-smallint-and-tinyint-transact-sql"></a>int, bigint, smallint e tinyint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Tipi di dati numerici esatti che utilizzano dati integer. Per risparmiare spazio nel database, utilizzare il tipo di dati più piccolo che può contenere in modo affidabile tutti i valori possibili. Ad esempio tinyint sarebbe sufficiente per età di una persona perché non si trova a più di 255 anni precedenti. Ma tinyint non sarebbero sufficienti per la durata di un edificio perché un edificio può essere più di 255 anni.
  
|Tipo di dati|Intervallo|Archiviazione|  
|---|---|---|
|**bigint**|da -2^63 (-9.223.372.036.854.775.808) a 2^63-1 (9.223.372.036.854.775.807)|8 byte|  
|**int**|da -2^31 (-2.147.483.648) a 2^31-1 (2.147.483.647)|4 byte|  
|**smallint**|da -2^15 (-32.768) a 2^15-1 (32.767)|2 byte|  
|**tinyint**|da 0 a 255|1 byte|  
  
## <a name="remarks"></a>Osservazioni  
Il **int** tipo di dati è il tipo di dati integer primario in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il **bigint** quando i valori interi potrebbero superare l'intervallo supportato dal tipo di dati deve essere utilizzato il **int** tipo di dati.
  
**bigint** compreso tra **smallmoney** e **int** nel grafico di precedenza tipo di dati.
  
Le funzioni restituiscono **bigint** solo se l'espressione del parametro è un **bigint** tipo di dati. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]non promuove automaticamente altri tipi di dati integer (**tinyint**, **smallint**, e **int**) per **bigint**.
  
> [!CAUTION]  
>  Quando si utilizza il +, -, \*, /, % operatori aritmetici per eseguire la conversione implicita o esplicita di o **int**, **smallint**, **tinyint**, o  **bigint** valori costanti di **float**, **reale**, **decimale** o **numerico** tipi di dati, le regole che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si applica quando si calcola il tipo di dati e la precisione dei risultati delle espressioni variano a seconda che la query sia attivata la parametrizzazione automatica o meno.  
>   
>  Per questo motivo, in alcuni casi espressioni simili nelle query possono dare risultati diversi. Quando una query non è attivata la parametrizzazione automatica, il valore costante viene prima convertito in **numerico**, la cui precisione è sufficiente a contenere il valore della costante, prima di convertire in tipo di dati specificato. Ad esempio, il valore costante 1 viene convertito in **numeric (1, 0)**, mentre il valore costante 250 viene convertito in **numeric (3, 0)**.  
>   
>  Quando una query con parametrizzazione automatica, il valore costante viene sempre convertito in **numeric (10, 0)** prima della conversione al tipo di dati finale. Se viene utilizzato l'operatore /, sia la precisione del tipo di risultati che il valore del risultato di query simili possono essere diversi. Ad esempio, il valore di risultato di una query con parametrizzazione automatica che include l'espressione `SELECT CAST (1.0 / 7 AS float)`, differisce dal valore del risultato della query stessa non è attivata la parametrizzazione automatica, in quanto i risultati della query con parametrizzazione automatica, vengono troncati per rientrare nel il **numeric (10, 0)** tipo di dati.  
  
## <a name="converting-integer-data"></a>Conversione di dati integer
Quando i numeri interi vengono convertiti implicitamente in un tipo di dati carattere, se il numero intero è troppo grande per adattarsi al campo del carattere, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] immette il carattere ASCII 42, l'asterisco (*).
  
Costanti integer maggiori di 2.147.483.647 vengono convertite le **decimale** del tipo di dati, non il **bigint** tipo di dati. L'esempio seguente mostra che quando il valore di soglia viene superato, il tipo di dati del risultato viene modificato da un **int** per un **decimale**.
  
```sql
SELECT 2147483647 / 2 AS Result1, 2147483649 / 2 AS Result2 ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result1      Result2  
1073741823   1073741824.500000  
```  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene creata una tabella utilizzando il **bigint**, **int**, **smallint**, e **tinyint** tipi di dati. I valori vengono inseriti in ogni colonna e restituiti nell'istruzione SELECT.
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyBigIntColumn bigint  
,MyIntColumn  int
,MySmallIntColumn smallint
,MyTinyIntColumn tinyint
);  
  
GO  
  
INSERT INTO dbo.MyTable VALUES (9223372036854775807, 2147483647,32767,255);  
 GO  
SELECT MyBigIntColumn, MyIntColumn, MySmallIntColumn, MyTinyIntColumn  
FROM dbo.MyTable;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyBigIntColumn       MyIntColumn MySmallIntColumn MyTinyIntColumn  
-------------------- ----------- ---------------- ---------------  
9223372036854775807  2147483647  32767            255  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Sys. Types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
