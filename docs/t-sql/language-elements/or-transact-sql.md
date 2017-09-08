---
title: O (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OR_TSQL
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- conditions [SQL Server], combining
- combining conditions
- OR operator
ms.assetid: b730a256-4a63-4880-9906-65b05cd9caf2
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 590410dd84275f63bc610ac436410c7d323eb8e3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="or-transact-sql"></a>OR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combina due condizioni. Quando un'istruzione include più operatori logici, gli operatori OR vengono valutati dopo gli operatori AND. È tuttavia possibile modificare l'ordine di valutazione tramite l'utilizzo delle parentesi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
boolean_expression OR boolean_expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *boolean_expression*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) che restituisce TRUE, FALSE o UNKNOWN.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="result-value"></a>Valore restituito  
 OR restituisce TRUE quando una delle due condizioni è TRUE.  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente viene illustrato il risultato dell'operatore OR.  
  
||TRUE|FALSE|UNKNOWN|  
|------|----------|-----------|-------------|  
|**TRUE**|TRUE|TRUE|TRUE|  
|**FALSE**|TRUE|FALSE|UNKNOWN|  
|**SCONOSCIUTO**|TRUE|UNKNOWN|UNKNOWN|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata la vista `vEmployeeDepartmentHistory` per recuperare i nomi del personale di `Quality Assurance` con turno serale o con turno notturno. Se le parentesi vengono omesse, la query restituisce i dipendenti di `Quality Assurance` con turno serale e tutti i dipendenti con turno notturno.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Shift   
FROM HumanResources.vEmployeeDepartmentHistory  
WHERE Department = 'Quality Assurance'  
   AND (Shift = 'Evening' OR Shift = 'Night');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `FirstName    LastName         Shift`  
  
 `------------ ---------------- -------`  
  
 `Andreas      Berglund         Evening`  
  
 `Sootha       Charncherngkha   Night`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'esempio seguente recupera i nomi dei dipendenti di ottenere un `BaseRate` inferiore a 20 o dispone di un `HireDate` 1 gennaio 2001 o versione successiva.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, BaseRate, HireDate   
FROM DimEmployee  
WHERE BaseRate < 10 OR HireDate >= '2001-01-01';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  



