---
title: SET ARITHABORT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ARITHABORT_TSQL
- ARITHABORT
- SET ARITHABORT
- SET_ARITHABORT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- terminating queries
- queries [SQL Server], terminating
- overflow errors [SQL Server]
- ARITHABORT option
- divide-by-zero errors
- SET ARITHABORT statement
- ending queries [SQL Server]
- stopping queries
ms.assetid: f938a666-fdd1-4233-b97f-719f27b1a0e6
caps.latest.revision: 46
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 97f65f734e68cc0a1ec4c019d50ce72b9c7e1bde
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-arithabort-transact-sql"></a>SET ARITHABORT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Interrompe una query quando si verifica un errore di divisione per zero o di overflow durante l'esecuzione della query stessa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ARITHABORT { ON | OFF }  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ARITHABORT ON   
[ ; ]  
```  
  
## <a name="remarks"></a>Osservazioni  
 Impostare sempre ARITHABORT su ON nelle sessioni di accesso. L'impostazione ARITHABORT su OFF può influire negativamente sull'ottimizzazione delle query causando problemi di prestazioni.  
  
> [!WARNING]  
>  L'impostazione ARITHABORT predefinita per [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è ON. Se per le applicazioni client l'opzione ARITHABORT viene impostata su OFF, è possibile che si ricevano diversi piani di query e, di conseguenza, la risoluzione di errori di query con prestazioni scarse risulta difficile. In altre parole, la stessa query può essere eseguita rapidamente in Management Studio, ma lentamente nell'applicazione. Quando si risolvono i problemi relativi alle query con [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], far sempre corrispondere l'impostazione ARITHABORT del client.  
  
 Se SET ARITHABORT è impostata su ON e SET ANSI WARNINGS su ON, queste condizioni di errore provocano l'interruzione della query.  
  
 Se SET ARITHABORT è impostata su ON e SET ANSI WARNINGS su OFF, queste condizioni di errore provocano l'interruzione del batch. Se gli errori si verificano in una transazione, viene eseguito il rollback della transazione. Se l'opzione SET ARITHABORT è impostata su OFF e si verifica uno di questi errori, viene visualizzato un avviso e al risultato dell'espressione aritmetica viene assegnato il valore NULL.  
  
 Se SET ARITHABORT e SET ANSI WARNINGS sono impostati su OFF e si verifica uno di questi errori, viene visualizzato un messaggio di avviso e al risultato dell'espressione aritmetica viene assegnato il valore NULL.  
  
> [!NOTE]  
>  Se entrambe le opzioni SET ARITHABORT e SET ARITHIGNORE non sono state impostate, dopo l'esecuzione della query [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce NULL e un messaggio di avviso.  
  
 Quando il livello di compatibilità del database è impostato su 90 o su un valore maggiore, l'impostazione di ANSI_WARNINGS su ON comporta anche l'impostazione implicita di ARITHABORT su ON. Se il livello di compatibilità del database è impostato su 80 o su un valore inferiore, l'opzione ARITHABORT deve essere impostata esplicitamente su ON.  
  
 Quando un'istruzione INSERT, DELETE o UPDATE rileva un errore aritmetico (un errore di overflow, una divisione per zero o un errore di dominio) durante la valutazione di un'espressione, se SET ARITHABORT è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inserisce o aggiorna un valore Null. Se la colonna di destinazione non ammette valori Null, l'operazione di inserimento o aggiornamento ha esito negativo e viene generato un errore per l'utente.  
  
 Se l'opzione SET ARITHABORT o SET ARITHIGNORE è impostata su OFF e l'opzione SET ANSI_WARNINGS è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce comunque un messaggio di errore quando si verificano errori di divisione per zero o di overflow.  
  
 Se SET ARITHABORT è impostata su OFF e si verifica un errore di interruzione durante la valutazione della condizione booleana di un'istruzione IF, verrà eseguito il segmento di codice associato alla valutazione FALSE.  
  
 È necessario che l'opzione SET ARITHABORT sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate. Se l'opzione è impostata su OFF, le istruzioni CREATE, UPDATE, INSERT e DELETE eseguite nelle tabelle che includono indici in colonne calcolate o viste indicizzate hanno esito negativo.  
  
 L'opzione SET ARITHABORT viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Per visualizzare l'impostazione corrente per questa impostazione, eseguire la query riportata di seguito.  
  
```  
DECLARE @ARITHABORT VARCHAR(3) = 'OFF';  
IF ( (64 & @@OPTIONS) = 64 ) SET @ARITHABORT = 'ON';  
SELECT @ARITHABORT AS ARITHABORT;  
  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono illustrati gli errori di divisione per zero e gli errori di overflow associati a impostazioni di `SET ARITHABORT`.  
  
```  
-- SET ARITHABORT  
-------------------------------------------------------------------------------  
-- Create tables t1 and t2 and insert data values.  
CREATE TABLE t1 (  
   a TINYINT,   
   b TINYINT  
);  
CREATE TABLE t2 (  
   a TINYINT  
);  
GO  
INSERT INTO t1   
VALUES (1, 0);  
INSERT INTO t1   
VALUES (255, 1);  
GO  
  
PRINT '*** SET ARITHABORT ON';  
GO  
-- SET ARITHABORT ON and testing.  
SET ARITHABORT ON;  
GO  
  
PRINT '*** Testing divide by zero during SELECT';  
GO  
SELECT a / b AS ab   
FROM t1;  
GO  
  
PRINT '*** Testing divide by zero during INSERT';  
GO  
INSERT INTO t2  
SELECT a / b AS ab    
FROM t1;  
GO  
  
PRINT '*** Testing tinyint overflow';  
GO  
INSERT INTO t2  
SELECT a + b AS ab   
FROM t1;  
GO  
  
PRINT '*** Resulting data - should be no data';  
GO  
SELECT *   
FROM t2;  
GO  
  
-- Truncate table t2.  
TRUNCATE TABLE t2;  
GO  
  
-- SET ARITHABORT OFF and testing.  
PRINT '*** SET ARITHABORT OFF';  
GO  
SET ARITHABORT OFF;  
GO  
  
-- This works properly.  
PRINT '*** Testing divide by zero during SELECT';  
GO  
SELECT a / b AS ab    
FROM t1;  
GO  
  
-- This works as if SET ARITHABORT was ON.  
PRINT '*** Testing divide by zero during INSERT';  
GO  
INSERT INTO t2  
SELECT a / b AS ab    
FROM t1;  
GO  
PRINT '*** Testing tinyint overflow';  
GO  
INSERT INTO t2  
SELECT a + b AS ab   
FROM t1;  
GO  
  
PRINT '*** Resulting data - should be 0 rows';  
GO  
SELECT *   
FROM t2;  
GO  
  
-- Drop tables t1 and t2.  
DROP TABLE t1;  
DROP TABLE t2;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ARITHIGNORE &#40; Transact-SQL &#41;](../../t-sql/statements/set-arithignore-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  

