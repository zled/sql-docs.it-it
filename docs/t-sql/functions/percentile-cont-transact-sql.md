---
title: PERCENTILE_CONT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/20/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PERCENTILE_CONT_TSQL
- PERCENTILE_CONT
dev_langs:
- TSQL
helpviewer_keywords:
- analytic functions, PERCENTILE_CONT
- PERCENTILE_CONT function
ms.assetid: d019419e-5297-4994-97d5-e9c8fc61bbf4
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 424e3ac668bb979a2d30446ff1ecb57346a0e8ac
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="percentilecont-transact-sql"></a>PERCENTILE_CONT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Calcola un percentile basato su una distribuzione continua del valore della colonna in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il risultato viene interpolato e potrebbe non essere uguale ad alcuno dei valori specifici nella colonna.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
PERCENTILE_CONT ( numeric_literal )   
    WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_literal*  
 Percentile da calcolare. Il valore deve essere compreso tra 0 e 1.  
  
 All'interno di gruppo **(** ORDER BY *argomento order_by_expression* [ **ASC** | DESC]**)**  
 Specifica un elenco di valori numerici per ordinare e calcolare il percentile. Un solo *argomento order_by_expression* è consentita. L'espressione deve restituire un tipo numerico esatto (**int**, **bigint**, **smallint**, **tinyint**, **numerico**, **bit**, **decimale**, **smallmoney**, **money**) o un tipo numerico approssimato ( **float**, **reale**). Altri tipi di dati non sono consentiti. Per impostazione predefinita, l'ordinamento è crescente.  
  
 SU **(** \<partition_by_clause > **)**  
 Suddivide il set di risultati generato dalla clausola FROM in partizioni alle quali viene applicata la funzione di percentile. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md). Il \<clausola ORDER BY > e \<righe o clausola range > della OVER sintassi non può essere specificata in una funzione PERCENTILE_CONT.  
  
## <a name="return-types"></a>Tipi restituiti  
 **float(53)**  
  
## <a name="compatibility-support"></a>Informazioni sulla compatibilità  
 Se il valore del livello di compatibilità è 110 o superiore, WITHIN GROUP è una parola chiave riservata. Per altre informazioni, vedere [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Tutti i valori Null nel set di dati vengono ignorati.  
  
 PERCENTILE_CONT è non deterministico. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-basic-syntax-example"></a>A. Esempio della sintassi di base  
 Nell'esempio seguente vengono utilizzate le funzioni PERCENTILE_CONT e PERCENTILE_DISC per trovare lo stipendio medio del dipendente in ogni reparto. Si noti che queste funzioni possono restituire valori diversi. Questa situazione si verifica perché PERCENTILE_CONT esegue l'interpolazione del valore appropriato, sia che esista o meno nel set di dati, mentre PERCENTILE_DISC restituisce sempre un valore effettivo dal set.  
  
```  
USE AdventureWorks2012;  
  
SELECT DISTINCT Name AS DepartmentName  
      ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianCont  
      ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianDisc  
FROM HumanResources.Department AS d  
INNER JOIN HumanResources.EmployeeDepartmentHistory AS dh   
    ON dh.DepartmentID = d.DepartmentID  
INNER JOIN HumanResources.EmployeePayHistory AS ph  
    ON ph.BusinessEntityID = dh.BusinessEntityID  
WHERE dh.EndDate IS NULL;  
```  
  
 Set di risultati parziale:  
  
 ```
DepartmentName        MedianCont    MedianDisc
--------------------   ----------   ----------
Document Control       16.8269      16.8269
Engineering            34.375       32.6923
Executive              54.32695     48.5577
Human Resources        17.427850    16.5865
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-basic-syntax-example"></a>B. Esempio della sintassi di base  
 Nell'esempio seguente vengono utilizzate le funzioni PERCENTILE_CONT e PERCENTILE_DISC per trovare lo stipendio medio del dipendente in ogni reparto. Si noti che queste funzioni possono restituire valori diversi. Questa situazione si verifica perché PERCENTILE_CONT esegue l'interpolazione del valore appropriato, sia che esista o meno nel set di dati, mentre PERCENTILE_DISC restituisce sempre un valore effettivo dal set.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT DepartmentName  
,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY BaseRate)  
    OVER (PARTITION BY DepartmentName) AS MedianCont  
,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY BaseRate)  
    OVER (PARTITION BY DepartmentName) AS MedianDisc  
FROM dbo.DimEmployee;  
  
```  
  
 Set di risultati parziale:  
  
 ```
DepartmentName        MedianCont    MedianDisc
--------------------   ----------   ----------
Document Control       16.826900    16.8269
Engineering            34.375000    32.6923
Human Resources        17.427850    16.5865
Shipping and Receiving 9.250000      9.0000
```  
  
## <a name="see-also"></a>Vedere anche  
 [PERCENTILE_DISC &#40; Transact-SQL &#41;](../../t-sql/functions/percentile-disc-transact-sql.md)  
  
  



