---
title: SET ANSI_WARNINGS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET ANSI_WARNINGS
- ANSI_WARNINGS_TSQL
- ANSI_WARNINGS
- SET_ANSI_WARNINGS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], ISO standard behavior
- warnings [SQL Server]
- SET ANSI_WARNINGS statement
- ANSI_WARNINGS option
ms.assetid: f82aaab0-334f-427b-89b0-de4af596b4fa
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 658de328868d08e808ee4f5cafd0b903aa7c717f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704261"
---
# <a name="set-ansiwarnings-transact-sql"></a>SET ANSI_WARNINGS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Specifica il funzionamento standard ISO in varie condizioni di errore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi
  
```
-- Syntax for SQL Server and Azure SQL Database
  
SET ANSI_WARNINGS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_WARNINGS ON
```

## <a name="remarks"></a>Remarks  
 L'opzione SET ANSI_WARNINGS risulta rilevante nelle condizioni seguenti:  
  
-   Quando è impostata su ON, se le funzioni di aggregazione quali SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP o COUNT includono valori Null, viene generato un messaggio di avviso. Quando è impostata su OFF, non viene generato alcun messaggio di avviso.  
  
-   Quando è impostata su ON, in seguito a errori di divisione per zero e di overflow aritmetico viene eseguito il rollback dell'istruzione e viene visualizzato un messaggio di errore. Quando è impostata su OFF, in seguito a errori di divisione per zero e di overflow aritmetico vengono restituiti valori Null. Si verifica un errore di divisione per zero o di overflow aritmetico se viene eseguita un'operazione INSERT o UPDATE in una colonna di tipo **character**, Unicode o **binary** in cui la lunghezza di un nuovo valore supera le dimensioni massime della colonna. Se l'opzione SET ANSI_WARNINGS è impostata su ON, l'istruzione INSERT o UPDATE viene annullata, come specificato dallo standard ISO. Nelle colonne di tipo carattere vengono ignorati gli spazi finali, mentre nelle colonne binarie vengono ignorati i valori Null finali. Quando l'opzione è impostata su OFF, i dati vengono troncati in base alle dimensioni della colonna e l'istruzione ha esito positivo.  
  
    > [!NOTE]  
    >  Se durante una conversione da o verso il tipo di dati **binary** o **varbinary** si verifica un troncamento, non viene visualizzato alcun avviso o errore, indipendentemente dalle opzioni SET.  
  
    > [!NOTE]  
    >  ANSI_WARNINGS non viene applicata quando vengono trasmessi parametri in una stored procedure o in una funzione definita dall'utente oppure in caso di dichiarazione e impostazione delle variabili in un'istruzione batch. Se, ad esempio, la variabile viene definita come **char(3)** e quindi impostata su un valore maggiore di tre caratteri, i dati verranno troncati alla dimensione definita e l'istruzione INSERT o UPDATE avrà esito positivo.  
  
 È possibile utilizzare l'opzione user options di sp_configure per definire l'impostazione predefinita di ANSI_WARNINGS per tutte le connessioni al server. Per altre informazioni, vedere [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 È necessario che l'opzione SET ANSI_WARNINGS sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate. Se l'opzione SET ANSI_WARNINGS è impostata su OFF, le istruzioni CREATE, UPDATE, INSERT e DELETE eseguite su tabelle che includono indici in colonne calcolate e viste indicizzate hanno esito negativo. Per altre informazioni sulle impostazioni dell'opzione SET necessarie per viste indicizzate e indici nelle colonne calcolate, vedere "Considerazioni sull'uso delle istruzioni SET" nell'argomento [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md).  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è inclusa l'opzione di database ANSI_WARNINGS. che equivale a SET ANSI_WARNINGS. Quando l'opzione SET ANSI_WARNINGS è impostata su ON, vengono generati errori o avvisi di divisione per zero, di stringa troppo estesa per la colonna di database e altri errori simili. Quando l'opzione SET ANSI_WARNINGS è impostata su OFF, questi errori e avvisi non vengono generati. Il valore predefinito per l'opzione SET ANSI_WARNINGS nel database modello è OFF. Se omessa, verrà applicata l'impostazione di ANSI_WARNINGS. Se l'opzione SET ANSI_WARNINGS è impostata su OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa il valore della colonna is_ansi_warnings_on nella vista del catalogo [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
 È necessario impostare l'opzione ANSI_WARNINGS su ON per l'esecuzione di query distribuite.  
  
 Il driver ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client e il provider OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impostano automaticamente l'opzione ANSI_WARNINGS su ON al momento della connessione. Può essere configurata nelle origini dati ODBC o negli attributi di connessione ODBC impostati nell'applicazione prima della connessione. L'impostazione predefinita dell'opzione SET ANSI_WARNINGS è OFF per le connessioni dalle applicazioni DB-Library.  
  
 Quando l'opzione SET ANSI_DEFAULTS è impostata su ON, l'opzione SET ANSI_WARNINGS risulta abilitata.  
  
 L'opzione SET ANSI_WARNINGS viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Se l'opzione SET ARITHABORT o SET ARITHIGNORE è impostata su OFF e l'opzione SET ANSI_WARNINGS è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce comunque un messaggio di errore quando si verificano errori di divisione per zero o di overflow.  
  
 Per visualizzare l'impostazione corrente per questa impostazione, eseguire la query riportata di seguito.  
  
```  
DECLARE @ANSI_WARN VARCHAR(3) = 'OFF';  
IF ( (8 & @@OPTIONS) = 8 ) SET @ANSI_WARN = 'ON';  
SELECT @ANSI_WARN AS ANSI_WARNINGS;  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono illustrate le tre situazioni sopra descritte con l'opzione SET ANSI_WARNINGS impostata su ON e su OFF.  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE T1   
(  
   a int,   
   b int NULL,   
   c varchar(20)  
);  
GO  
  
SET NOCOUNT ON;  
  
INSERT INTO T1   
VALUES (1, NULL, '')   
      ,(1, 0, '')  
      ,(2, 1, '')  
      ,(2, 2, '');  
  
SET NOCOUNT OFF;  
GO  
  
PRINT '**** Setting ANSI_WARNINGS ON';  
GO  
  
SET ANSI_WARNINGS ON;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (3, 3, 'Text string longer than 20 characters');  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
PRINT '**** Setting ANSI_WARNINGS OFF';  
GO  
SET ANSI_WARNINGS OFF;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (4, 4, 'Text string longer than 20 characters');  
GO  
SELECT a, b, c   
FROM T1  
WHERE a = 4;  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
DROP TABLE T1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [SESSIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  
