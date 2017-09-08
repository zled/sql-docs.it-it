---
title: SET QUOTED_IDENTIFIER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 02/03/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QUOTED_IDENTIFIER_TSQL
- SET_QUOTED_IDENTIFIER_TSQL
- SET QUOTED_IDENTIFIER
- QUOTED_IDENTIFIER
dev_langs:
- TSQL
helpviewer_keywords:
- delimited identifiers [SQL Server]
- identifiers [SQL Server], delimited
- QUOTED_IDENTIFIER option
- quoted identifiers
- ISO delimited identifiers rules
- SET QUOTED_IDENTIFIER statement
ms.assetid: 10f66b71-9241-4a3a-9292-455ae7252565
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c6ba7962a9721dad3c3f043f960c72f718f6062
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-quotedidentifier-transact-sql"></a>SET QUOTED_IDENTIFIER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Impone in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la conformità alle regole ISO relative all'utilizzo delle virgolette per delimitare identificatori e stringhe letterali. Gli identificatori delimitati da virgolette doppie possono essere parole chiave riservate [!INCLUDE[tsql](../../includes/tsql-md.md)] o possono includere caratteri normalmente non consentiti dalle regole della sintassi [!INCLUDE[tsql](../../includes/tsql-md.md)] per gli identificatori.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET QUOTED_IDENTIFIER { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET QUOTED_IDENTIFIER ON   
```  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione SET QUOTED_IDENTIFIER è impostata su ON, è possibile delimitare gli identificatori con virgolette doppie, mentre i valori letterali devono essere delimitati da virgolette singole. Quando l'opzione SET QUOTED_IDENTIFIER è impostata su OFF, non è possibile racchiudere tra virgolette gli identificatori, i quali devono essere conformi alle regole per gli identificatori di [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per altre informazioni, vedere [Identificatori del database](../../relational-databases/databases/database-identifiers.md). È possibile delimitare i valori letterali con virgolette singole o doppie.  
  
 Quando l'opzione SET QUOTED_IDENTIFIER è impostata su ON (impostazione predefinita), tutte le stringhe delimitate da virgolette doppie vengono interpretate come identificatori di oggetto. Gli identificatori delimitati pertanto non devono necessariamente essere conformi alle regole per gli identificatori di [!INCLUDE[tsql](../../includes/tsql-md.md)]. Possono essere parole chiave riservate e includere caratteri normalmente non consentiti negli identificatori [!INCLUDE[tsql](../../includes/tsql-md.md)]. Non è possibile utilizzare le virgolette doppie per delimitare espressioni di stringhe letterali. Inoltre le stringhe letterali devono essere racchiuse tra virgolette singole. Se una virgoletta singola (**'**) fa parte della stringa letterale, può essere rappresentato da due virgolette singole (**"**). Quando si utilizzano parole chiave riservate per nomi di oggetti nel database, è necessario che l'opzione SET QUOTED_IDENTIFIER sia impostata su ON.  
  
 Quando l'opzione SET QUOTED_IDENTIFIER è impostata su OFF, è possibile delimitare le stringhe letterali nelle espressioni con virgolette singole o doppie. Se una stringa letterale è delimitata da virgolette doppie, la stringa può includere virgolette singole, ad esempio gli apostrofi.  
  
 È necessario che l'opzione SET QUOTED_IDENTIFIER sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate. Se l'opzione SET QUOTED_IDENTIFIER è impostata su OFF, le istruzioni CREATE, UPDATE, INSERT e DELETE eseguite su tabelle che includono indici in colonne calcolate o viste indicizzate hanno esito negativo. Per ulteriori informazioni sulle impostazioni dell'opzione SET necessarie con viste indicizzate e indici in colonne calcolate, vedere "Considerazioni quando si usa delle istruzioni SET" in [istruzioni SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 SET QUOTED_IDENTIFIER deve essere impostata su ON durante la creazione di un indice filtrato.  
  
 SET QUOTED_IDENTIFIER deve essere impostata su ON quando si richiamano metodi con tipo di dati XML.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider OLE DB per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impostano automaticamente l'opzione QUOTED_IDENTIFIER su ON durante la connessione. È possibile configurare questa impostazione nelle origini dei dati ODBC, negli attributi di connessione ODBC o nelle proprietà di connessione OLE DB. L'impostazione predefinita dell'opzione SET QUOTED_IDENTIFIER è OFF per le connessioni dalle applicazioni DB-Library.  
  
 Durante la creazione di una tabella l'opzione QUOTED IDENTIFIER viene sempre archiviata impostata su ON nei metadati della tabella se l'opzione è stata precedentemente impostata su OFF.  
  
 Quando viene creata una stored procedure, le impostazioni delle opzioni SET QUOTED_IDENTIFIER e SET ANSI_NULLS vengono acquisite e utilizzate per le successive chiamate della stored procedure.  
  
 Quando viene eseguita all'interno di una stored procedure, l'impostazione dell'opzione SET QUOTED_IDENTIFIER non viene modificata.  
  
 Quando l'opzione SET ANSI_DEFAULTS è impostata su ON, l'opzione SET QUOTED_IDENTIFIER risulta abilitata.  
  
 SET QUOTED_IDENTIFIER corrisponde inoltre all'impostazione QUOTED_IDENTIFER di ALTER DATABASE. Per ulteriori informazioni sulle impostazioni del database, vedere [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 SET QUOTED_IDENTIFIER è ha effetto in fase di analisi e influisce solo sulle analisi, non l'esecuzione di query.  
  
 Per un livello superiore Ad-Hoc batch durante l'analisi viene avviato tramite l'impostazione corrente della sessione per QUOTED_IDENTIFIER.  Come viene analizzato il batch di tutte le occorrenze dell'opzione SET QUOTED_IDENTIFIER modificare il comportamento di analisi da tale punto in e salvare tale impostazione per la sessione.  Pertanto il batch viene analizzato ed eseguito, impostazione QUOTED_IDENTIFER della sessione verrà impostato in base l'ultima occorrenza dell'opzione SET QUOTED_IDENTIFIER nel batch.  
 SQL statico in una stored procedure viene analizzato utilizzando l'impostazione di QUOTED_IDENTIFIER in uso per il batch che ha creato o modificato la stored procedure.  SET QUOTED_IDENTIFIER non ha alcun effetto quando viene visualizzato nel corpo di una stored procedure SQL statico.  
  
 Per un batch nidificato utilizzando sp_executesql o EXEC () l'analisi viene avviato tramite l'impostazione di QUOTED_IDENTIFIER della sessione.  Se il batch nidificato all'interno di una stored procedure, che l'analisi viene avviata tramite l'impostazione di QUOTED_IDENTIFIER della stored procedure.  Come viene analizzato il batch nidificato qualsiasi occorrenza dell'opzione SET QUOTED_IDENTIFIER verrà modificati il comportamento di analisi da tale punto, ma impostazione QUOTED_IDENTIFIER della sessione non verrà aggiornato.  
  
 Utilizzando le parentesi, **[** e **]**, per delimitare gli identificatori non è interessato dalla configurazione dell'impostazione di QUOTED_IDENTIFIER.  
  
 Per visualizzare l'impostazione corrente per questa impostazione, eseguire la query riportata di seguito.  
  
```  
DECLARE @QUOTED_IDENTIFIER VARCHAR(3) = 'OFF';  
IF ( (256 & @@OPTIONS) = 256 ) SET @QUOTED_IDENTIFIER = 'ON';  
SELECT @QUOTED_IDENTIFIER AS QUOTED_IDENTIFIER;  
  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-the-quoted-identifier-setting-and-reserved-word-object-names"></a>A. Utilizzo dell'impostazione per l'identificatore delimitato e di nomi di oggetto corrispondenti a parole chiave riservate  
 Nell'esempio seguente viene illustrato come, per poter creare e utilizzare oggetti con nomi che corrispondono a parole chiave riservate, sia necessario impostare l'opzione `SET QUOTED_IDENTIFIER` su `ON` e racchiudere tra virgolette doppie le parole chiave nei nomi di tabella.  
  
```  
SET QUOTED_IDENTIFIER OFF  
GO  
-- An attempt to create a table with a reserved keyword as a name  
-- should fail.  
CREATE TABLE "select" ("identity" INT IDENTITY NOT NULL, "order" INT NOT NULL);  
GO  
  
SET QUOTED_IDENTIFIER ON;  
GO  
  
-- Will succeed.  
CREATE TABLE "select" ("identity" INT IDENTITY NOT NULL, "order" INT NOT NULL);  
GO  
  
SELECT "identity","order"   
FROM "select"  
ORDER BY "order";  
GO  
  
DROP TABLE "SELECT";  
GO  
  
SET QUOTED_IDENTIFIER OFF;  
GO  
```  
  
### <a name="b-using-the-quoted-identifier-setting-with-single-and-double-quotation-marks"></a>B. Utilizzo dell'opzione per l'identificatore delimitato con virgolette singole e doppie  
 Nell'esempio seguente viene illustrato l'utilizzo di virgolette singole e doppie in espressioni stringa con l'opzione `SET QUOTED_IDENTIFIER` impostata su `ON` e `OFF`.  
  
```  
SET QUOTED_IDENTIFIER OFF;  
GO  
USE AdventureWorks2012;  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'Test')  
   DROP TABLE dbo.Test;  
GO  
USE AdventureWorks2012;  
CREATE TABLE dbo.Test (ID INT, String VARCHAR(30)) ;  
GO  
  
-- Literal strings can be in single or double quotation marks.  
INSERT INTO dbo.Test VALUES (1, "'Text in single quotes'");  
INSERT INTO dbo.Test VALUES (2, '''Text in single quotes''');  
INSERT INTO dbo.Test VALUES (3, 'Text with 2 '''' single quotes');  
INSERT INTO dbo.Test VALUES (4, '"Text in double quotes"');  
INSERT INTO dbo.Test VALUES (5, """Text in double quotes""");  
INSERT INTO dbo.Test VALUES (6, "Text with 2 """" double quotes");  
GO  
  
SET QUOTED_IDENTIFIER ON;  
GO  
  
-- Strings inside double quotation marks are now treated   
-- as object names, so they cannot be used for literals.  
INSERT INTO dbo."Test" VALUES (7, 'Text with a single '' quote');  
GO  
  
-- Object identifiers do not have to be in double quotation marks  
-- if they are not reserved keywords.  
SELECT ID, String   
FROM dbo.Test;  
GO  
  
DROP TABLE dbo.Test;  
GO  
  
SET QUOTED_IDENTIFIER OFF;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `ID          String`  
  
 `----------- ------------------------------`  
  
 `1           'Text in single quotes'`  
  
 `2           'Text in single quotes'`  
  
 `3           Text with 2 '' single quotes`  
  
 `4           "Text in double quotes"`  
  
 `5           "Text in double quotes"`  
  
 `6           Text with 2 "" double quotes`  
  
 `7           Text with a single ' quote`  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [sp_rename &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)  
  
  

