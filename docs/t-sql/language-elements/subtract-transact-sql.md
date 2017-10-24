---
title: '- (Sottrazione) (Transact-SQL) | Documenti Microsoft'
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
- subtract
- '-'
- -_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
- minus operator (-)
- subtracting numbers
ms.assetid: db23145f-f17d-4b90-be09-28a881cacd1a
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6f3013e03ddc1d7481c36be6ed8cce4cf4572c04
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="--subtract-transact-sql"></a>- (sottrazione) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Sottrae due numeri (operatore aritmetico di sottrazione). Consente inoltre di sottrarre un numero di giorni da una data.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) uno qualsiasi dei tipi di dati del valore numerico categoria, tipo di dati, ad eccezione di **bit** tipo di dati. Non può essere utilizzato con **data**, **ora**, **datetime2**, o **datetimeoffset** tipi di dati.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati dell'argomento con la priorità più alta. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-subtraction-in-a-select-statement"></a>A. Utilizzo della sottrazione in un'istruzione SELECT  
 Nell'esempio seguente viene calcolata la differenza tra l'aliquota di imposta applicata dallo stato o dalla provincia con l'aliquota più alta e l'aliquota di imposta applicata dallo stato o dalla provincia con l'aliquota più bassa.  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
```  
-- Uses AdventureWorks  
  
SELECT MAX(TaxRate) - MIN(TaxRate) AS 'Tax Rate Difference'  
FROM Sales.SalesTaxRate  
WHERE StateProvinceID IS NOT NULL;  
GO  
```  
  
 È tuttavia possibile modificare l'ordine di esecuzione tramite l'utilizzo delle parentesi. I calcoli tra parentesi vengono eseguiti per primi. Se le parentesi sono nidificate, ha precedenza il calcolo più interno.  
  
### <a name="b-using-date-subtraction"></a>B. Utilizzo della sottrazione di date  
 Nell'esempio seguente viene sottratto un numero di giorni da una data di tipo `datetime`.  
  
 Si applica a: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
```  
-- Uses AdventureWorks  
  
DECLARE @altstartdate datetime;  
SET @altstartdate = CONVERT(DATETIME, ''January 10, 1900 3:00 AM', 101);  
SELECT @altstartdate - 1.5 AS 'Subtract Date';  
```  
  
 Set di risultati:  
  
 ```
 Subtract Date  
 -----------------------  
 1900-01-08 15:00:00.000  

 (1 row(s) affected)
 ```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-subtraction-in-a-select-statement"></a>C: utilizzo della sottrazione in un'istruzione SELECT  
 Nell'esempio seguente calcola la differenza in una tariffa di base tra il dipendente con la frequenza di base più elevata e il dipendente con l'aliquota più bassa dal `dimEmployee` tabella.  
  
```  
-- Uses AdventureWorks  
  
SELECT MAX(BaseRate) - MIN(BaseRate) AS BaseRateDifference  
FROM DimEmployee;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori aritmetici &#40; Transact-SQL &#41;](../../t-sql/language-elements/arithmetic-operators-transact-sql.md)   
 [-&#40; Negativo &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/unary-operators-negative.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [-= &#40; Sottrarre EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/subtract-equals-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  



