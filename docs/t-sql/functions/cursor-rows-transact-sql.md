---
title: '@@CURSOR_ROWS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@CURSOR_ROWS'
- '@@CURSOR_ROWS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CURSOR_ROWS function'
- cursors [SQL Server], last-opened
- last-opened cursor
- asynchronous cursors [SQL Server]
ms.assetid: 31bd7a97-7f28-42a8-ba24-24d16d22973d
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 481c4205bec9032b31b4405830827405050abb8b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="x40x40cursorrows-transact-sql"></a>&#x40;&#x40;CURSOR_ROWS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il numero delle righe attualmente risultanti nell'ultimo cursore aperto sulla connessione. Per migliorare le prestazioni, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può popolare i cursori statistici e i set di chiavi di grandi dimensioni in modo asincrono. È possibile chiamare la funzione @@CURSOR_ROWS in modo che il recupero del numero delle righe per un cursore venga eseguito al momento della chiamata alla funzione @@CURSOR_ROWS.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```
@@CURSOR_ROWS  
```  
  
## <a name="return-types"></a>Tipi restituiti
**integer**
  
## <a name="return-value"></a>Valore restituito  
  
|Valore restituito|Description|  
|---|---|
|-*m*|Il cursore viene popolato in modo asincrono. Il valore restituito (-*m*) corrisponde al numero di righe risultanti per il set di chiavi.|  
|-1|Il cursore è dinamico. Poiché nei cursori dinamici vengono riportate tutte le modifiche, il numero delle righe risultanti per il cursore è variabile. Non è possibile affermare in modo definitivo che tutte le righe restituite sono state recuperate.|  
|0|Non è stato aperto alcun cursore, nessuna riga è stata restituita per l'ultimo cursore aperto oppure l'ultimo cursore aperto è chiuso o deallocato.|  
|*n*|Il cursore è completamente popolato. Il valore restituito (*n*) corrisponde al numero totale di righe nel cursore.|  
  
## <a name="remarks"></a>Remarks  
Il numero restituito dalla funzione @@CURSOR_ROWS è negativo se l'ultimo cursore è stato aperto in modo asincrono. I driver del set di chiavi o i cursori statistici vengono aperti in modo asincrono se il valore della soglia del cursore sp_configure è maggiore di 0 e il numero di righe nel set di risultati del cursore è maggiore del valore soglia del cursore.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene dichiarato un cursore e viene utilizzata l'istruzione `SELECT` per visualizzare il valore della funzione `@@CURSOR_ROWS`. Prima dell'apertura del cursore il valore della funzione è `0`. Il valore `-1` indica che il set di chiavi del cursore è stato popolato in modo asincrono.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@CURSOR_ROWS;  
DECLARE Name_Cursor CURSOR FOR  
SELECT LastName ,@@CURSOR_ROWS FROM Person.Person;  
OPEN Name_Cursor;  
FETCH NEXT FROM Name_Cursor;  
SELECT @@CURSOR_ROWS;  
CLOSE Name_Cursor;  
DEALLOCATE Name_Cursor;  
GO             
```  
  
Set di risultati.
  
```
-----------
0  
```

```
LastName
---------------
Sanchez
```

```
-----------
-1
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni per i cursori &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md)  
[OPEN &#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)
  
  
