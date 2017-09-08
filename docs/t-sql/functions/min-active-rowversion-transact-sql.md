---
title: MIN_ACTIVE_ROWVERSION (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MIN_ACTIVE_ROWVERSION
- MIN_ACTIVE_ROWVERSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MIN_ACTIVE_ROWVERSION function [Transact-SQL]
ms.assetid: 87c89547-8ea1-4820-b75e-36be683e4e10
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ed1254e0e35aa108d9866f30da49962b886a39ae
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="minactiverowversion-transact-sql"></a>MIN_ACTIVE_ROWVERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il valore **rowversion** attivo più basso nel database corrente. Un valore **rowversion** è attivo se viene usato in una transazione di cui non è ancora stato eseguito il commit. Per ulteriori informazioni, vedere [rowversion &#40; Transact-SQL &#41; ](../../t-sql/data-types/rowversion-transact-sql.md).  
  
> [!NOTE]  
>  Il **rowversion** tipo di dati è noto anche come **timestamp**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
MIN_ACTIVE_ROWVERSION  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce un **Binary (8)** valore.  
  
## <a name="remarks"></a>Osservazioni  
 MIN_ACTIVE_ROWVERSION è una funzione non deterministica che restituisce attivo più basso **rowversion** valore nel database corrente. Quando viene eseguita un'istruzione INSERT o UPDATE in una tabella contenente una colonna di tipo **rowversion** , viene solitamente generato un nuovo valore **rowversion**. Se non sono presenti valori attivi nel database, MIN_ACTIVE_ROWVERSION restituisce lo stesso valore di @@DBTS + 1.  
  
 MIN_ACTIVE_ROWVERSION è utile per scenari come la sincronizzazione dei dati che utilizzano **rowversion** valori per raggruppare set di modifiche. Se un'applicazione usa@DBTS anziché MIN_ACTIVE_ROWVERSION, è possibile eseguire modifiche di mancato riscontro che sono attive quando viene eseguita la sincronizzazione.  
  
 La funzione MIN_ACTIVE_ROWVERSION non è interessata dalle modifiche apportate ai livelli di isolamento delle transazioni.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce **rowversion** valori utilizzando `MIN_ACTIVE_ROWVERSION` e `@@DBTS`. Si noti che i valori sono diversi quando non vi sono transazioni attive nel database.  
  
```  
-- Create a table that has a ROWVERSION column in it.  
CREATE TABLE RowVersionTestTable (rv ROWVERSION)  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E2  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E3  
  
-- Insert a row.  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E3  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Insert a new row inside a transaction but do not commit.  
BEGIN TRAN  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
--0x00000000000007E4  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Commit the transaction.  
COMMIT  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E5  
```  
  
## <a name="see-also"></a>Vedere anche  
 [@@DBTS &#40;Transact-SQL&#41;](../../t-sql/functions/dbts-transact-sql.md)   
 [rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)  
  
  
