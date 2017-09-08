---
title: TRIGGER_NESTLEVEL (Transact-SQL) | Documenti Microsoft
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
- TRIGGER_NESTLEVEL
- TRIGGER_NESTLEVEL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- triggers [SQL Server], number executed
- number of triggers
- TRIGGER_NESTLEVEL function
ms.assetid: 6a33e74a-0cf9-4ae1-a1e4-4a137a3ea39d
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 352ea0e82fa853639d94a6a151b3d7df5f5b2f21
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="triggernestlevel-transact-sql"></a>TRIGGER_NESTLEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il numero di trigger eseguiti per l'istruzione che ha attivato il trigger. TRIGGER_NESTLEVEL viene utilizzata nei trigger DML e DDL per determinare il livello di nidificazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
TRIGGER_NESTLEVEL ( [ object_id ] , [ 'trigger_type' ] , [ 'trigger_event_category' ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *object_id*  
 ID di oggetto di un trigger. Se *object_id* viene specificato, il numero di esecuzioni del trigger specificato per l'istruzione viene restituito. Se *object_id* non viene specificato, il numero di volte in cui tutti i trigger sono stati eseguiti per l'istruzione viene restituito.  
  
 **'** *trigger_type* **'**  
 Specifica se applicare TRIGGER_NESTLEVEL ai trigger AFTER oppure ai trigger INSTEAD OF. Specificare **AFTER** per i trigger AFTER. Specificare **IOT** per i trigger INSTEAD OF. Se *trigger_type* è specificato, *trigger_event_category* deve anche essere specificato.  
  
 **'** *trigger_event_category* **'**  
 Specifica se applicare TRIGGER_NESTLEVEL ai trigger DML o DDL. Specificare **DML** per i trigger DML. Specificare **DDL** per i trigger DDL. Se *trigger_event_category* è specificato, *trigger_type* deve anche essere specificato. Si noti che solo **AFTER** possono essere specificati con **DDL**, poiché i trigger DDL possono essere solo trigger AFTER.  
  
## <a name="remarks"></a>Osservazioni  
 Se non si specifica alcun parametro, TRIGGER_NESTLEVEL restituisce il numero totale di trigger nello stack di chiamate. Nel numero è incluso il parametro stesso. È possibile omettere i parametri quando un trigger esegue comandi che provocano l'attivazione di un altro trigger o crea una serie di attivazioni di trigger.  
  
 Per restituire il numero totale di trigger nello stack di chiamate per una categoria di tipo e all'evento trigger specifico, specificare *object_id* = 0.  
  
 TRIGGER_NESTLEVEL restituisce il valore 0 se viene eseguita all'esterno di un trigger e i parametri sono diversi da NULL.  
  
 Se i parametri vengono specificati in modo esplicito come NULL, viene restituito il valore NULL indipendentemente dal fatto che TRIGGER_NESTLEVEL sia stata utilizzata all'interno o all'esterno di un trigger.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-testing-the-nesting-level-of-a-specific-dml-trigger"></a>A. Controllo del livello di nidificazione di un trigger DML specifico  
  
```  
IF ( (SELECT TRIGGER_NESTLEVEL( OBJECT_ID('xyz') , 'AFTER' , 'DML' ) ) > 5 )  
   RAISERROR('Trigger xyz nested more than 5 levels.',16,-1)  
```  
  
### <a name="b-testing-the-nesting-level-of-a-specific-ddl-trigger"></a>B. Controllo del livello di nidificazione di un trigger DDL specifico  
  
```  
IF ( ( SELECT TRIGGER_NESTLEVEL ( ( SELECT object_id FROM sys.triggers  
WHERE name = 'abc' ), 'AFTER' , 'DDL' ) ) > 5 )  
   RAISERROR ('Trigger abc nested more than 5 levels.',16,-1)  
```  
  
### <a name="c-testing-the-nesting-level-of-all-triggers-executed"></a>C. Controllo del livello di nidificazione di tutti i trigger  
  
```  
IF ( (SELECT trigger_nestlevel() ) > 5 )  
   RAISERROR  
      ('This statement nested over 5 levels of triggers.',16,-1)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
