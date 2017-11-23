---
title: Selezionare @local_variable (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- variable_TSQL
- '@loca_variable'
- '@local'
- variable
- '@loca_variable_TSQL'
- '@local_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- variables [SQL Server], assigning
- SELECT statement [SQL Server], @local_variable
- '@local_variable'
- local variables [SQL Server]
ms.assetid: 8e1a9387-2c5d-4e51-a1fd-a2a95f026d6f
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 56303a563bce3def564fe3b92067eb6f4c6a2177
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="select-localvariable-transact-sql"></a>Selezionare @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Imposta una variabile locale per il valore di un'espressione.  
  
 Per l'assegnazione delle variabili, è consigliabile utilizzare [impostare @local_variable ](../../t-sql/language-elements/set-local-variable-transact-sql.md) anziché SELECT @*local_variable*.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SELECT { @local_variable { = | += | -= | *= | /= | %= | &= | ^= | |= } expression } 
    [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
@*local_variable*  
 Variabile dichiarata a cui deve essere assegnato un valore.  
  
{= | += | -= | \*= | /= | %= | &= | ^= | |= }   
Assegna il valore a destra alla variabile a sinistra.  
  
Operatore di assegnazione composto:  
  |operatore |action |   
  |-----|-----|  
  | = | Assegna l'espressione seguente, la variabile. |  
  | += | Aggiungere e assegnare |   
  | -= | Sottrazione e assegnazione |  
  | \*= | Moltiplicare e assegnare |  
  | /= | Divisione e assegnazione |  
  | %= | Modulo e assegnare |  
  | &= | AND bit per bit e assegnazione |  
  | ^= | XOR bit per bit e assegnare |  
  | \|= | OR bit per bit e assegnazione |  
  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md). Include una sottoquery scalare.  
  
## <a name="remarks"></a>Osservazioni  
 SELECT @*local_variable* viene in genere utilizzata per restituire un singolo valore nella variabile. Tuttavia, quando *espressione* è il nome di una colonna, può restituire più valori. Se l'istruzione SELECT restituisce più valori, alla variabile viene assegnato l'ultimo valore restituito.  
  
 Se l'istruzione SELECT non restituisce righe, la variabile mantiene il valore corrente. Se *espressione* è una sottoquery scalare che restituisce alcun valore, la variabile non viene impostata su NULL.  
  
 Un'istruzione SELECT può inizializzare più variabili locali.  
  
> [!NOTE]  
>  Un'istruzione SELECT che include l'assegnazione di un valore a una variabile non può essere utilizzata anche per eseguire normali operazioni di recupero del set di risultati.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-use-select-localvariable-to-return-a-single-value"></a>A. Utilizzare un'istruzione SELECT @local_variable per restituire un valore singolo  
 Nell'esempio seguente alla variabile `@var1` viene assegnato `Generic Name` come valore. La query eseguita nella tabella `Store` non restituisce righe perché il valore specificato per `CustomerID` non esiste nella tabella. La variabile mantiene il valore `Generic Name`.  
  
```sql  
-- Uses AdventureWorks    
  
DECLARE @var1 varchar(30);         
SELECT @var1 = 'Generic Name';         
SELECT @var1 = Name         
FROM Sales.Store         
WHERE CustomerID = 1000 ;        
SELECT @var1 AS 'Company Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Company Name  
 ------------------------------  
 Generic Name  
 ```  
  
### <a name="b-use-select-localvariable-to-return-null"></a>B. Utilizzare un'istruzione SELECT @local_variable per restituire null  
 Nell'esempio seguente viene utilizzata una sottoquery per assegnare un valore a `@var1`. Poiché il valore richiesto da `CustomerID` non esiste, la sottoquery non restituisce valori e la variabile viene impostata su `NULL`.  
  
```sql  
-- Uses AdventureWorks  
  
DECLARE @var1 varchar(30)   
SELECT @var1 = 'Generic Name'   
SELECT @var1 = (SELECT Name   
FROM Sales.Store   
WHERE CustomerID = 1000)   
SELECT @var1 AS 'Company Name' ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Company Name  
----------------------------  
NULL  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  
