---
title: SWITCHOFFSET (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/02/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SWITCHTZ
- SWITCHTZ_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- functions [SQL Server], time
- functions [SQL Server], date and time
- SWITCHOFFSET function [SQL Server]
- time [SQL Server], functions
- date and time [SQL Server], SWITCHOFFSET
- time zones [SQL Server]
ms.assetid: 32a48e36-0aa4-4260-9fe9-cae9197d16c5
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 3c81153c233e68d12347dc47ae9c232f4a5ee030
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="switchoffset-transact-sql"></a>SWITCHOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce un **datetimeoffset** valore che viene modificato dalla differenza di fuso orario archiviata in una differenza di fuso orario nuova specificata.  
  
 Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SWITCHOFFSET ( DATETIMEOFFSET, time_zone )   
```  
  
## <a name="arguments"></a>Argomenti  
 *DATETIMEOFFSET*  
 È un'espressione che può essere risolta in un **DateTimeOffset (n)** valore.  
  
 *fuso orario*  
 È una stringa di caratteri nel formato [+ |-] tzh o un intero con segno (minuti) che rappresenta la differenza di fuso orario, si presuppone che sia legale e regolata.  
  
## <a name="return-type"></a>Tipo restituito  
 **DateTimeOffset** con la precisione frazionaria di *DATETIMEOFFSET* argomento.  
  
## <a name="remarks"></a>Sezione Osservazioni  
 Utilizzare SWITCHOFFSET per selezionare un **datetimeoffset** valore in un fuso orario è diverso dalla differenza di fuso orario memorizzato in origine. SWITCHOFFSET non aggiorna archiviato *fuso orario* valore.  
  
 SWITCHOFFSET può essere utilizzato per aggiornare un **datetimeoffset** colonna.  
  
 Utilizzo di SWITCHOFFSET con la funzione GETDATE () può causare la query venga eseguita lentamente. In questo modo query optimizer non riesce a ottenere le stime di cardinalità corrette per il valore datetime. Per risolvere questo problema, utilizzare l'hint per la query OPTION (RECOMPILE) per forzare il query optimizer di ricompilare un piano di query alla successiva esecuzione della stessa query. Query optimizer disporrà di stime precise sulla cardinalità e produrrà un piano di query più efficiente. Per ulteriori informazioni sull'hint per la query RECOMPILE, vedere [hint per la Query &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-query.md).  
  
```  
DECLARE @dt datetimeoffset = switchoffset (CONVERT(datetimeoffset, GETDATE()), '-04:00');   
SELECT * FROM t    
WHERE c1 > @dt OPTION (RECOMPILE);  
  
```  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa `SWITCHOFFSET` per visualizzare un offset di fusi orari diversi rispetto al valore archiviato nel database.  
  
```  
CREATE TABLE dbo.test   
    (  
    ColDatetimeoffset datetimeoffset  
    );  
GO  
INSERT INTO dbo.test   
VALUES ('1998-09-20 7:45:50.71345 -5:00');  
GO  
SELECT SWITCHOFFSET (ColDatetimeoffset, '-08:00')   
FROM dbo.test;  
GO  
--Returns: 1998-09-20 04:45:50.7134500 -08:00  
SELECT ColDatetimeoffset  
FROM dbo.test;  
--Returns: 1998-09-20 07:45:50.7134500 -05:00  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [FUSO orario &AMP;#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  



