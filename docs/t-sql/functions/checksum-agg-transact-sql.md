---
title: CHECKSUM_AGG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHECKSUM_AGG
- CHECKSUM_AGG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- checksum values
- CHECKSUM_AGG function
- groups [SQL Server], checksum values
ms.assetid: cdede70c-4eb5-4c92-98ab-b07787ab7222
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 54e82e66d2f5ba49291cadf0cef198733cb7e0e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33052618"
---
# <a name="checksumagg-transact-sql"></a>CHECKSUM_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Questa funzione restituisce il valore di checksum dei valori di un gruppo. `CHECKSUM_AGG` ignora i valori Null. La [clausola OVER](../../t-sql/queries/select-over-clause-transact-sql.md) può seguire `CHECKSUM_AGG`.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CHECKSUM_AGG ( [ ALL | DISTINCT ] expression )  
```  
  
## <a name="arguments"></a>Argomenti  
**ALL**  
Applica la funzione di aggregazione a tutti i valori. L'argomento predefinito è ALL.
  
DISTINCT  
Specifica che `CHECKSUM_AGG` restituisce il valore di checksum di valori univoci.
  
*expression*  
[Espressione](../../t-sql/language-elements/expressions-transact-sql.md) integer. `CHECKSUM_AGG` non consente l'uso di funzioni o sottoquery di aggregazione.
  
## <a name="return-types"></a>Tipi restituiti
Restituisce il valore di checksum di tutti i valori di *expression* come valore **int**.
  
## <a name="remarks"></a>Remarks  
`CHECKSUM_AGG` consente di rilevare le modifiche in una tabella.
  
Il risultato `CHECKSUM_AGG` non dipende dall'ordine delle righe nella tabella. Le funzioni `CHECKSUM_AGG` consentono anche l'uso della parola chiave DISTINCT e della clausola GROUP BY.
  
Se un valore di elenco di espressioni cambia, è probabile che cambi anche l'elenco di valori di checksum dell'elenco. Esiste tuttavia una minima possibilità che il valore di checksum calcolato non verrà modificato.
  
`CHECKSUM_AGG` offre una funzionalità simile a quella di altre funzioni di aggregazione. Per altre informazioni, vedere [Funzioni di aggregazione &#40;Transact-SQL&#41;](../../t-sql/functions/aggregate-functions-transact-sql.md).
  
## <a name="examples"></a>Esempi  
Negli esempi seguenti viene usata la funzione `CHECKSUM_AGG` per rilevare le modifiche apportate nella colonna `Quantity` della tabella `ProductInventory` inclusa nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
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
[CHECKSUM &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-transact-sql.md)  
[Clausola OVER &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
