---
title: Modulo (Transact-SQL) | Documenti Microsoft
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
- modulo
- '% (Modulo)'
- MOD_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: f93c662e-f405-486e-bf23-a2d03907b5bd
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b417bbca6135db2f4ca6279bb9aac75d9d6f328
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="modulo-transact-sql"></a>Modulo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Viene restituito il resto di una divisione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Argomenti  
 *dividend*  
 Espressione numerica da dividere. *dividendo* deve essere un valore valido [espressione](../../t-sql/language-elements/expressions-transact-sql.md) uno qualsiasi dei tipi di dati nell'integer o di categorie di tipi di dati di tipo valuta, o **numerico** tipo di dati.  
  
 *divisor*  
 Espressione numerica per cui dividere il dividendo. *divisore* deve essere qualsiasi espressione valida di uno qualsiasi dei tipi di dati nell'integer o di categorie di tipi di dati di tipo valuta, o **numerico** tipo di dati.  
  
## <a name="result-types"></a>Tipi restituiti  
 Dipendenti dai tipi di dati dei due argomenti.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare l'operatore aritmetico modulo nell'elenco di selezione dell'istruzione SELECT con qualsiasi combinazione di nomi di colonna, costanti numeriche o qualsiasi espressione valida di integer e dati di valuta un tipo di categorie o **numerico** dati tipo.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-example"></a>A. Esempio semplice  
 Nell'esempio seguente viene diviso il numero 38 per 5. Questo comporta 7 come parte intera del risultato e viene illustrato come modulo, restituisce il resto di 3.  
  
```  
SELECT 38 / 5 AS Integer, 38 % 5 AS Remainder ;  
  
```  
  
### <a name="b-example-using-columns-in-a-table"></a>B. Esempio di utilizzo di colonne in una tabella  
 Nell'esempio seguente viene restituito il numero di serie del prodotto, il prezzo unitario del prodotto e il modulo (resto) della divisione tra il prezzo di ogni prodotto convertito in un valore intero e il numero di prodotti ordinati.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(100)ProductID, UnitPrice, OrderQty,  
   CAST((UnitPrice) AS int) % OrderQty AS Modulo  
FROM Sales.SalesOrderDetail;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example"></a>C: esempio  
 L'esempio seguente mostra i risultati per il `%` operatore quando si divide 3 per 2.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) 3%2 FROM dimEmployee;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
1         
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Ad esempio &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Modulo EQUALS &#40; Transact-SQL &#41;](../../t-sql/language-elements/modulo-equals-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  



