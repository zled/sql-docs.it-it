---
title: REPLACE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REPLACE_TSQL
- REPLACE
dev_langs:
- TSQL
helpviewer_keywords:
- first string expression [SQL Server]
- replacing string expression
- third string expressions [SQL Server]
- second string expressions [SQL Server]
- REPLACE function
ms.assetid: 8a7aaaf2-62e3-46c0-8e44-fa22290dd86b
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8340c1b3af3ad843a0e3080cbfdc771d7353c7b7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="replace-transact-sql"></a>REPLACE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Sostituisce tutte le occorrenze di un valore stringa specificato con un altro valore stringa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
REPLACE ( string_expression , string_pattern , string_replacement )  
```  
  
## <a name="arguments"></a>Argomenti  
 *string_expression*  
 È la stringa [espressione](../../t-sql/language-elements/expressions-transact-sql.md) da cercare. *string_expression* può essere un tipo di dati carattere o binario.  
  
 *string_*modello  
 Sottostringa da individuare. *string_pattern* può essere un tipo di dati carattere o binario. *string_pattern* non può essere una stringa vuota (") e non deve superare il numero massimo di byte che rientra in una pagina.  
  
 *string_*sostituzione  
 Stringa di sostituzione. *string_replacement* può essere un tipo di dati carattere o binario.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce **nvarchar** se uno degli argomenti di input è del **nvarchar** il tipo di dati; in caso contrario, sostituire restituisce **varchar**.  
  
 Viene restituito NULL se un argomento qualsiasi è NULL.  
  
 Se *string_expression* non è di tipo **varchar (max)** o **nvarchar (max), REPLACE** tronca il valore restituito a 8.000 byte. Per restituire i valori maggiori di 8.000 byte, *string_expression* deve essere impostato in modo esplicito un tipo di dati di valori di grandi dimensioni.  
  
## <a name="remarks"></a>Osservazioni  
 Tramite REPLACE vengono effettuati confronti in base alle regole di confronto dell'input. Per eseguire un confronto in regole di confronto specificate, è possibile utilizzare [COLLATE](~/t-sql/statements/collations.md) per applicare regole di confronto esplicite all'input.  
  
 0x0000 (**char(0)**) è un carattere non definito nelle regole di confronto di Windows e non può essere incluso in REPLACE.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la stringa `cde` in `abcdefghi` viene sostituita da `xxx`.  
  
```sql  
SELECT REPLACE('abcdefghicde','cde','xxx');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------  
abxxxfghixxx  
(1 row(s) affected)  
```  
  
 Nell'esempio seguente viene utilizzata la funzione `COLLATE`.  
  
```sql  
SELECT REPLACE('This is a Test'  COLLATE Latin1_General_BIN,  
'Test', 'desk' );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------  
This is a desk  
(1 row(s) affected)  
```  

  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  

