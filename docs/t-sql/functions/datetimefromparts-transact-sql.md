---
title: DATETIMEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATETIMEFROMPARTS_TSQL
- DATETIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEFROMPARTS function
ms.assetid: 6008148b-bf75-4c98-9392-68a89fa0711c
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 754e91dcebdc7d040802de11ba0285f6cf472a4a
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37784722"
---
# <a name="datetimefromparts-transact-sql"></a>DATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Questa funzione restituisce un valore di tipo **datetime** per gli argomenti date e time.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATETIMEFROMPARTS ( year, month, day, hour, minute, seconds, milliseconds )  
```  
  
## <a name="arguments"></a>Argomenti  
*year*  
Espressione Integer che specifica un anno.
  
*month*  
Espressione Integer che specifica un mese.
  
*day*  
Espressione Integer che specifica un giorno.
  
*hour*  
Espressione Integer che specifica le ore.
  
*minute*  
Espressione Integer che specifica i minuti.
  
*secondi*  
Espressione Integer che specifica i secondi.
  
*milliseconds*  
Espressione Integer che specifica i millisecondi.
  
## <a name="return-types"></a>Tipi restituiti
**datetime**
  
## <a name="remarks"></a>Remarks  
`DATETIMEFROMPARTS` restituisce un valore di tipo **datetime** completamente inizializzato. `DATETIMEFROMPARTS` genererà un errore se almeno un argomento obbligatorio ha un valore non valido. `DATETIMEFROMPARTS` restituisce null se almeno un argomento obbligatorio ha un valore null.
  
Questa funzione supporta la comunicazione remota con i server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e versioni successive. Non supporterà la comunicazione remota con i server con versioni precedenti a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Esempi  
  
```sql
SELECT DATETIMEFROMPARTS ( 2010, 12, 31, 23, 59, 59, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[datetime &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md)
  
  

