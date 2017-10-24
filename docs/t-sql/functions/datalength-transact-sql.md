---
title: DATALENGTH (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATALENGTH_TSQL
- DATALENGTH
dev_langs:
- TSQL
helpviewer_keywords:
- number of bytes representing expression
- data types [SQL Server], length
- DATALENGTH function
- expressions [SQL Server], length
- lengths [SQL Server], data
ms.assetid: 00f377f1-cc3e-4eac-be47-b3e3f80267c9
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: d8887c50cb482e27bce63e08aa18b8ca54616faa
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il numero di byte utilizzati per rappresentare un'espressione.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>Argomenti  
*espressione*  
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di dati.
  
## <a name="return-types"></a>Tipi restituiti
**bigint** se *espressione* è il **varchar (max)**, **nvarchar (max)** o **varbinary (max)** tipi di dati. in caso contrario **int**.
  
## <a name="remarks"></a>Osservazioni  
DATALENGTH è particolarmente utile con **varchar**, **varbinary**, **testo**, **immagine**, **nvarchar**, e **ntext** tipi di dati perché questi tipi di dati è possono archiviare dati a lunghezza variabile.
  
Il valore DATALENGTH di NULL è NULL.
  
> [!NOTE]  
>  I livelli di compatibilità possono influire sui valori restituiti. Per informazioni sui livelli di compatibilità supportati, vedere [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene individuata la lunghezza della colonna `Name` nella tabella `Product`.
  
```sql
-- Uses AdventureWorks  
  
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[LEN &#40; Transact-SQL &#41;](../../t-sql/functions/len-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Funzioni di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  


