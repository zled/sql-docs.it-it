---
title: CUME_DIST (Transact-SQL) | Documenti Microsoft
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
- CUME_DIST
- CUME_DIST_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CUME_DIST function
- analytic functions, CUME_DIST
ms.assetid: 491b07f3-9ffd-4cdd-93e5-5abb636fc5ef
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 22364fce2c5c8bfa2707f1f270dd728735096a31
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cumedist-transact-sql"></a>CUME_DIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-asdw-xxx-md.md)]

Calcola la distribuzione cumulativa di un valore in un gruppo di valori in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. ovvero CUME_DIST calcola la posizione relativa di un valore specificato in un gruppo di valori. Per una riga *r*, presumendo un ordine crescente, il CUME_DIST di *r* è il numero di righe con valori inferiori o uguali al valore di *r*, diviso per il numero di righe valutata nel set di risultati di query o partizione. CUME_DIST è simile alla funzione PERCENT_RANK.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CUME_DIST( )  
    OVER ( [ partition_by_clause ] order_by_clause )  
  
```  
  
## <a name="arguments"></a>Argomenti  
SU **(** [ *partition_by_clause* ] *order_by_clause***)**  
*partition_by_clause* suddivide il set di risultati generato dalla clausola FROM in partizioni a cui viene applicata la funzione. Se non specificato, la funzione tratta tutte le righe del set di risultati della query come un unico gruppo. *order_by_clause* determina l'ordine logico in cui viene eseguita l'operazione. *order_by_clause* è obbligatorio. Il \<righe o clausola range > della OVER sintassi non può essere specificata in una funzione CUME_DIST. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Tipi restituiti
**float(53)**
  
## <a name="remarks"></a>Osservazioni  
L'intervallo di valori restituiti da CUME_DIST è maggiore di 0 e minore o uguale a 1. I valori restituiscono sempre lo stesso valore di distribuzione cumulativo. I valori NULL sono inclusi per impostazione predefinita e vengono trattati come i valori minori consentiti.
  
CUME_DIST è non deterministico. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene utilizzata la funzione CUME_DIST per calcolare il percentile del salario per ogni dipendente all'interno di un reparto specificato. Il valore restituito dalla funzione CUME_DIST rappresenta la percentuale di dipendenti che dispongono di un salario minore o uguale al dipendente corrente nello stesso reparto. La funzione PERCENT_RANK calcola il rango percentuale dello stipendio del dipendente in un reparto. La clausola PARTITION BY è specificata per suddividere le righe nel set di risultati in base al reparto. La clausola ORDER BY specificata nella clausola OVER ordina le righe in ogni partizione in modo logico. La clausola ORDER BY nell'istruzione SELECT determina l'ordine di visualizzazione del set di risultati.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT Department, LastName, Rate,   
       CUME_DIST () OVER (PARTITION BY Department ORDER BY Rate) AS CumeDist,   
       PERCENT_RANK() OVER (PARTITION BY Department ORDER BY Rate ) AS PctRank  
FROM HumanResources.vEmployeeDepartmentHistory AS edh  
    INNER JOIN HumanResources.EmployeePayHistory AS e    
    ON e.BusinessEntityID = edh.BusinessEntityID  
WHERE Department IN (N'Information Services',N'Document Control')   
ORDER BY Department, Rate DESC;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
  
Department             LastName               Rate                  CumeDist               PctRank  
---------------------- ---------------------- --------------------- ---------------------- ----------------------  
Document Control       Arifin                 17.7885               1                      1  
Document Control       Norred                 16.8269               0.8                    0.5  
Document Control       Kharatishvili          16.8269               0.8                    0.5  
Document Control       Chai                   10.25                 0.4                    0  
Document Control       Berge                  10.25                 0.4                    0  
Information Services   Trenary                50.4808               1                      1  
Information Services   Conroy                 39.6635               0.9                    0.888888888888889  
Information Services   Ajenstat               38.4615               0.8                    0.666666666666667  
Information Services   Wilson                 38.4615               0.8                    0.666666666666667  
Information Services   Sharma                 32.4519               0.6                    0.444444444444444  
Information Services   Connelly               32.4519               0.6                    0.444444444444444  
Information Services   Berg                   27.4038               0.4                    0  
Information Services   Meyyappan              27.4038               0.4                    0  
Information Services   Bacon                  27.4038               0.4                    0  
Information Services   Bueno                  27.4038               0.4                    0  
(15 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[PERCENT_RANK &#40; Transact-SQL &#41;](../../t-sql/functions/percent-rank-transact-sql.md)
  
  

