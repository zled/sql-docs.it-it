---
title: '@@CURSOR_ROWS (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 10a3a6cabae8d25de670cbacb037a62f4c5a2d54
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40cursorrows-transact-sql"></a>& #x 40; & #x 40; CURSOR_ROWS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il numero delle righe attualmente risultanti nell'ultimo cursore aperto sulla connessione. Per migliorare le prestazioni, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può popolare i cursori statistici e i set di chiavi di grandi dimensioni in modo asincrono. @@CURSOR_ROWS può essere chiamato per determinare che il numero di righe che soddisfano le condizioni per un cursore viene recuperato in fase di @@CURSOR_ROWS viene chiamato.
  
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
|-*m*|Il cursore viene popolato in modo asincrono. Il valore restituito (-*m*) è il numero di righe correntemente nel keyset.|  
|-1|Il cursore è dinamico. Poiché nei cursori dinamici vengono riportate tutte le modifiche, il numero delle righe risultanti per il cursore è variabile. Non è possibile affermare in modo definitivo che tutte le righe restituite sono state recuperate.|  
|0|Non è stato aperto alcun cursore, nessuna riga è stata restituita per l'ultimo cursore aperto oppure l'ultimo cursore aperto è chiuso o deallocato.|  
|*n*|Il cursore è completamente popolato. Il valore restituito (*n*) è il numero totale di righe nel cursore.|  
  
## <a name="remarks"></a>Osservazioni  
Il numero restituito da@CURSOR_ROWS è negativo se l'ultimo cursore è stato aperto in modo asincrono. I driver o i cursori statistici vengono aperti in modo asincrono se il valore di sp_configure cursor threshold è maggiore di 0 e il numero di righe nel set di risultati del cursore è maggiore della soglia del cursore.
  
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
[Funzioni di cursore &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-functions-transact-sql.md)  
[Apri &#40; Transact-SQL &#41;](../../t-sql/language-elements/open-transact-sql.md)
  
  

