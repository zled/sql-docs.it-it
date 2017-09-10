---
title: CHARINDEX (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHARINDEX
- CHARINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], pattern searching
- CHARINDEX function
- pattern searching [SQL Server]
- starting point of expression in character string
ms.assetid: 78c10341-8373-4b30-b404-3db20e1a3ac4
caps.latest.revision: 52
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5049508aac52724bbf0b05c9962b154db7af1474
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="charindex-transact-sql"></a>CHARINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Consente di cercare in un'espressione un'altra espressione e restituisce la posizione iniziale se la trova.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
CHARINDEX ( expressionToFind , expressionToSearch [ , start_location ] )   
```  
  
## <a name="arguments"></a>Argomenti  
*expressionToFind*  
È un carattere [espressione](../../t-sql/language-elements/expressions-transact-sql.md) che contiene la sequenza da trovare. *expressionToFind* è limitato a 8000 caratteri.
  
*expressionToSearch*  
Espressione di caratteri da cercare.
  
*start_location*  
È un **intero** o **bigint** expression in corrispondenza del quale inizia la ricerca. Se *start_location* non è specificato, è un numero negativo o è 0, la ricerca viene avviata all'inizio di *expressionToSearch*.
  
## <a name="return-types"></a>Tipi restituiti
**bigint** se *expressionToSearch* è il **varchar (max)**, **nvarchar (max)**, o **varbinary (max)** dati errore. in caso contrario, **int**.
  
## <a name="remarks"></a>Osservazioni  
Se il valore *expressionToFind* o *expressionToSearch* è un tipo di dati Unicode (**nvarchar** o **nchar**) e l'altro non lo è, il altri viene convertito in un tipo di dati Unicode. CHARINDEX non può essere utilizzato con **testo**, **ntext**, e **immagine** tipi di dati.
  
Se il valore *expressionToFind* o *expressionToSearch* è NULL, CHARINDEX restituisce NULL.
  
Se *expressionToFind* non viene trovato all'interno di *expressionToSearch*, CHARINDEX restituisce 0.
  
CHARINDEX esegue confronti in base alle regole di confronto dell'input. Per eseguire un confronto in base a regole di confronto specifiche, è possibile utilizzare COLLATE per applicare regole di confronto esplicite all'input.
  
La posizione di inizio restituita è in base 1 e non in base 0.
  
0x0000 (**char(0)**) è un carattere non definito nelle regole di confronto di Windows e non può essere incluso in CHARINDEX.
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
Quando si utilizzano regole di confronto SC, sia *start_location* e le coppie di surrogati conteggio di valore restituito come un carattere, non due. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-starting-position-of-an-expression"></a>A. Restituzione della posizione iniziale di un'espressione  
Nell'esempio seguente viene restituita la posizione in corrispondenza della quale inizia la sequenza di caratteri `bicycle` nella colonna `DocumentSummary` della tabella `Document` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
DECLARE @document varchar(64);  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bicycle', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
48            
```  
  
### <a name="b-searching-from-a-specific-position"></a>B. Ricerca da una posizione specifica  
L'esempio seguente usa l'opzione facoltativa *start_location* parametro per avviare la ricerca di `vital` dal quinto carattere del `DocumentSummary` colonna il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('vital', @document, 5);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
16            
  
(1 row(s) affected)  
```  
  
### <a name="c-searching-for-a-nonexistent-expression"></a>C. Ricerca di un'espressione inesistente  
Nell'esempio seguente il set di risultati quando *expressionToFind* non viene trovato all'interno di *expressionToSearch*.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bike', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`-----------`
  
 `0`  
  
`(1 row(s) affected)`
  
### <a name="d-performing-a-case-sensitive-search"></a>D. Esecuzione di una ricerca con distinzione tra maiuscole e minuscole  
Nell'esempio seguente viene eseguita una ricerca tra maiuscole e minuscole per la stringa `'TEST'` in `'This is a Test``'`.
  
```sql
USE tempdb;  
GO  
--perform a case sensitive search  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`-----------`
  
 `0`  
  
Nell'esempio seguente viene eseguita una ricerca tra maiuscole e minuscole per la stringa `'Test'` in `'This is a Test'`.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'Test',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`-----------`
  
 `13`  
  
### <a name="e-performing-a-case-insensitive-search"></a>E. Esecuzione di una ricerca senza distinzione tra maiuscole e minuscole  
Nell'esempio seguente viene eseguita una ricerca senza distinzione tra maiuscole e minuscole per la stringa `'TEST'` in `'This is a Test'`.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CI_AS);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`-----------`
  
 `13`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="f-searching-from-the-start-of-a-string-expression"></a>F. La ricerca dall'inizio di un'espressione stringa  
L'esempio seguente restituisce la prima posizione del `is` stringa in `This is a string`, a partire dalla posizione 1 (il primo carattere) nella stringa.
  
```sql
SELECT CHARINDEX('is', 'This is a string');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`---------`
  
 `3`  
  
### <a name="g-searching-from-a-position-other-than-the-first-position"></a>G. Ricerca da una posizione della posizione del primo  
L'esempio seguente restituisce la prima posizione del `is` stringa in `This is a string`, che inizia con la posizione del quarto.
  
```sql
SELECT CHARINDEX('is', 'This is a string', 4);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`---------`
  
 `6`  
  
### <a name="h-results-when-the-string-is-not-found"></a>H. Risultati quando non viene trovata la stringa  
Nell'esempio seguente il valore restituito quando il *string_pattern* non viene trovato nella stringa di ricerca.
  
```sql
SELECT TOP(1) CHARINDEX('at', 'This is a string') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`---------`
  
 `0`  
  
## <a name="see-also"></a>Vedere anche
[Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
[+ &#40; Concatenazione di stringhe &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
[Regole di confronto e supporto Unicode](../../relational-databases/collations/collation-and-unicode-support.md)
  
  



