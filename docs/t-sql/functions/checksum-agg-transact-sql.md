---
title: CHECKSUM_AGG (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKSUM_AGG
- CHECKSUM_AGG_TSQL
dev_langs: TSQL
helpviewer_keywords:
- checksum values
- CHECKSUM_AGG function
- groups [SQL Server], checksum values
ms.assetid: cdede70c-4eb5-4c92-98ab-b07787ab7222
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3499cd8fb118d12fdbf450c23f2919fd0003cee7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="checksumagg-transact-sql"></a>CHECKSUM_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il valore di checksum dei valori di un gruppo. I valori Null vengono ignorati. Può essere seguito dal [clausola OVER](../../t-sql/queries/select-over-clause-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CHECKSUM_AGG ( [ ALL | DISTINCT ] expression )  
```  
  
## <a name="arguments"></a>Argomenti  
**ALL**  
Applica la funzione di aggregazione a tutti i valori. Il valore predefinito è ALL.
  
DISTINCT  
Specifica che la funzione CHECKSUM_AGG restituisce il valore di checksum di valori univoci.
  
*espressione*  
È un numero intero [espressione](../../t-sql/language-elements/expressions-transact-sql.md). Non è possibile utilizzare funzioni di aggregazione e sottoquery.
  
## <a name="return-types"></a>Tipi restituiti
Restituisce il checksum di tutti i *espressione* i valori come **int**.
  
## <a name="remarks"></a>Osservazioni  
La funzione CHECKSUM_AGG può essere utilizzata per rilevare modifiche in una tabella.
  
L'ordine delle righe nella tabella non influisce sul risultato della funzione CHECKSUM_AGG. È inoltre possibile utilizzare le funzioni CHECKSUM_AGG con la parola chiave DISTINCT e la clausola GROUP BY.
  
Se uno dei valori nell'elenco di espressioni cambia, in genere cambia anche il valore di checksum dell'elenco. È comunque possibile che il valore di checksum rimanga invariato.
  
La funzionalità di CHECKSUM_AGG è simile a quella di altre funzioni di aggregazione. Per ulteriori informazioni, vedere [funzioni di aggregazione &#40; Transact-SQL &#41; ](../../t-sql/functions/aggregate-functions-transact-sql.md).
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene utilizzata la funzione `CHECKSUM_AGG` per rilevare le modifiche apportate nella colonna `Quantity` della tabella `ProductInventory` inclusa nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
--Get the checksum value before the column value is changed.  
SELECT CHECKSUM_AGG(CAST(Quantity AS int))  
FROM Production.ProductInventory;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
------------------------  
262  
```  
  
```sql
UPDATE Production.ProductInventory   
SET Quantity=125  
WHERE Quantity=100;  
GO  
--Get the checksum of the modified column.  
SELECT CHECKSUM_AGG(CAST(Quantity AS int))  
FROM Production.ProductInventory;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
------------------------  
287  
```  
  
## <a name="see-also"></a>Vedere anche
[CHECKSUM &#40; Transact-SQL &#41;](../../t-sql/functions/checksum-transact-sql.md)  
[IN una clausola &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
