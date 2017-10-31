---
title: SET ANSI_PADDING (Transact-SQL) | Documenti Microsoft
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
- ANSI_PADDING_TSQL
- ANSI_PADDING
- SET_ANSI_PADDING_TSQL
- SET ANSI_PADDING
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], short values
- ANSI_PADDING option
- short values [SQL Server]
- SET ANSI_PADDING statement
- trailing blanks
ms.assetid: 92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 426cbfe673bafe6e1770745ca16ba23fd068fb67
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansipadding-transact-sql"></a>SET ANSI_PADDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Controlla il modo in cui la colonna archivia i valori di dimensioni inferiori a quelle definite della colonna e i valori contenenti spazi vuoti finali nei dati **char**, **varchar**, **binary**e **varbinary** .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
SET ANSI_PADDING { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_PADDING ON;  
```  
  
## <a name="remarks"></a>Osservazioni  
 Le colonne definite con **char**, **varchar**, **binario**, e **varbinary** tipi di dati hanno dimensioni definite.  
  
 Questa impostazione influisce solo sulla definizione di nuove colonne. Dopo la creazione della colonna, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archivia i valori in base all'impostazione specificata in fase di creazione. Le successive modifiche dell'impostazione non influiscono sulle colonne esistenti.  
  
> [!NOTE]  
>  È consigliabile impostare l'opzione ANSI_PADDING sempre su ON.  
  
 La tabella seguente illustra gli effetti dell'impostazione di SET ANSI_PADDING quando i valori vengono inseriti in colonne con **char**, **varchar**, **binario**, e  **varbinary** tipi di dati.  
  
|Impostazione|Char (*n*) non NULL o binary (*n*) non NULL.|Char (*n*) NULL o binary (*n*) NULL|varchar (*n*) o varbinary (*n*)|  
|-------------|----------------------------------------------------|--------------------------------------------|----------------------------------------|  
|ON|Valore originale di riempimento (per gli spazi vuoti finali **char** colonne e con zeri per **binario** colonne) per la lunghezza della colonna.|Segue le stesse regole di **char (***n***)** o **binario (**  *n*  **)** NOT NULL quando l'opzione SET ANSI_PADDING è impostata su ON.|Gli spazi finali in valori di tipo carattere inseriti **varchar** colonne non vengono rimossi. Gli zeri finali in valori binari inseriti in **varbinary** colonne non vengono rimossi. I valori non vengono riempiti con caratteri nulli per l'intera lunghezza della colonna.|  
|OFF|Valore originale di riempimento (per gli spazi vuoti finali **char** colonne e con zeri per **binario** colonne) per la lunghezza della colonna.|Segue le stesse regole di **varchar** o **varbinary** quando SET ANSI_PADDING è OFF.|Gli spazi finali in valori di tipo carattere inseriti in un **varchar** colonna vengono tagliati. Gli zeri finali in valori binari inseriti in un **varbinary** colonna vengono tagliati.|  
  
> [!NOTE]  
>  Quando l'operazione di riempimento, **char** colonne vengono riempite con spazi vuoti, e **binario** colonne vengono riempite con zeri. Quando viene tagliato, **char** le colonne hanno gli spazi vuoti finali rimossi, e **binario** le colonne hanno vengono eliminati gli zeri finali.  
  
 È necessario che l'opzione SET ANSI_PADDING sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate. Per ulteriori informazioni sulle impostazioni dell'opzione SET necessarie con viste indicizzate e indici in colonne calcolate, vedere "Considerazioni quando si usa delle istruzioni SET" in [istruzioni SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 L'impostazione predefinita di SET ANSI_PADDING è ON. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider OLE DB per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impostano automaticamente l'opzione ANSI_PADDING su ON durante la connessione. Questa può essere configurata nelle origini dati ODBC, negli attributi di connessione ODBC o nelle proprietà di connessione OLE DB impostate nell'applicazione prima della connessione. L'opzione predefinita per SET ANSI_PADDING è OFF per le connessioni di applicazioni DB-Library.  
  
 L'impostazione SET ANSI_PADDING non interessa il **nchar**, **nvarchar**, **ntext**, **testo**, **immagine**, **varbinary (max)**, **varchar (max)**, e **nvarchar (max)** tipi di dati. Viene sempre applicata l'opzione SET ANSI_PADDING ON. Gli spazi vuoti e gli zero finali non vengono pertanto eliminati.  
  
 Quando l'opzione SET ANSI_DEFAULTS è impostata su ON, l'opzione SET ANSI_PADDING è abilitata.  
  
 L'opzione SET ANSI_PADDING viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Per visualizzare l'impostazione corrente per questa impostazione, eseguire la query riportata di seguito.  
  
```  
DECLARE @ANSI_PADDING VARCHAR(3) = 'OFF';  
IF ( (16 & @@OPTIONS) = 16 ) SET @ANSI_PADDING = 'ON';  
SELECT @ANSI_PADDING AS ANSI_PADDING;  
  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'impatto dell'impostazione sui diversi tipi di dati.  
  
```  
PRINT 'Testing with ANSI_PADDING ON'  
SET ANSI_PADDING ON;  
GO  
  
CREATE TABLE t1 (  
   charcol CHAR(16) NULL,   
   varcharcol VARCHAR(16) NULL,   
   varbinarycol VARBINARY(8)  
);  
GO  
INSERT INTO t1 VALUES ('No blanks', 'No blanks', 0x00ee);  
INSERT INTO t1 VALUES ('Trailing blank ', 'Trailing blank ', 0x00ee00);  
  
SELECT 'CHAR' = '>' + charcol + '\<', 'VARCHAR'='>' + varcharcol + '\<',  
   varbinarycol  
FROM t1;  
GO  
  
PRINT 'Testing with ANSI_PADDING OFF';  
SET ANSI_PADDING OFF;  
GO  
  
CREATE TABLE t2 (  
   charcol CHAR(16) NULL,   
   varcharcol VARCHAR(16) NULL,   
   varbinarycol VARBINARY(8)  
);  
GO  
INSERT INTO t2 VALUES ('No blanks', 'No blanks', 0x00ee);  
INSERT INTO t2 VALUES ('Trailing blank ', 'Trailing blank ', 0x00ee00);  
  
SELECT 'CHAR' = '>' + charcol + '\<', 'VARCHAR'='>' + varcharcol + '<',  
   varbinarycol  
FROM t2;  
GO  
  
DROP TABLE t1;  
DROP TABLE t2;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)  
  
  

