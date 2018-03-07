---
title: char e varchar (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- varchar
- varchar_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fixed-length data types [SQL Server]
- character data type
- char data type
- varchar(max) data type
- variable-length data types [SQL Server]
- varchar data type
ms.assetid: 282cd982-f4fb-4b22-b2df-9e8478f13f6a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4c383e3b3ff5b79604454f80443c9042633797bf
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="char-and-varchar-transact-sql"></a>char and varchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Questi tipi di dati sono di lunghezza fissa o a lunghezza variabile.  
  
## <a name="arguments"></a>Argomenti  
**Char** [(  *n*  )] lunghezza fissa, dati di tipo stringa non Unicode. *n*definisce la lunghezza della stringa e deve essere un valore compreso tra 1 e 8.000. Le dimensioni di archiviazione sono  *n*  byte. Il sinonimo ISO per **char** è **carattere**.
  
**varchar** [(  *n*   |  **max** )] a lunghezza variabile, i dati di stringa non Unicode. *n*definisce la lunghezza della stringa e può essere un valore compreso tra 1 e 8.000. **max** indica che le dimensioni massime di archiviazione sono 2 ^ 31-1 byte (2 GB). Le dimensioni dello spazio di archiviazione corrispondono alla lunghezza effettiva dei dati immessi + 2 byte. I sinonimi di ISO per **varchar** sono **charvarying** o **charactervarying**.
  
## <a name="remarks"></a>Osservazioni  
Quando  *n*  non è specificato nella definizione dei dati o istruzione di dichiarazione di variabile, la lunghezza predefinita è 1. Quando  *n*  non viene specificato quando si utilizzano le funzioni CAST e CONVERT, la lunghezza predefinita è 30.
  
Gli oggetti che utilizzano **char** o **varchar** vengono assegnate le regole di confronto predefinite del database, a meno che non viene assegnato un regole di confronto specifiche tramite la clausola COLLATE. Le regole di confronto controllano la tabella codici utilizzata per l'archiviazione dei dati di tipo carattere.
  
Se si dispone di siti che supportano più lingue, considerare l'utilizzo di Unicode **nchar** o **nvarchar** tipi di dati per ridurre al minimo i problemi di conversione. Se si utilizza **char** o **varchar**, si consiglia quanto segue:
- Utilizzare **char** quando le dimensioni delle voci della colonna sono coerenti.  
- Utilizzare **varchar** quando le dimensioni delle voci della colonna variano notevolmente.  
- Utilizzare **varchar (max)** quando le dimensioni delle voci della colonna variano notevolmente e le dimensioni possono essere superiori a 8.000 byte.  
  
Se l'opzione SET ANSI_PADDING è impostata su OFF quando viene eseguita l'istruzione CREATE TABLE o ALTER TABLE, un **char** colonna definita come NULL vengono gestite come **varchar**.
  
Quando la tabella codici delle regole di confronto utilizza caratteri a byte doppio, le dimensioni di archiviazione sono ancora  *n*  byte. A seconda della stringa di caratteri, le dimensioni di archiviazione  *n*  byte possono essere minore di  *n*  caratteri.

> [!WARNING]
> Ogni varchar (max) non null o una colonna nvarchar (max) richiede 24 byte di allocazione fissa aggiuntiva che concorre il limite di riga di 8.060 byte durante un'operazione di ordinamento. Questo può creare un limite implicito per il numero di colonne nvarchar (max) che possono essere create in una tabella o di varchar (max) non null.  
Non vengono segnalati errori particolari (oltre il normale avviso che indica che le dimensioni massime per le righe superano il valore massimo consentito di 8060 byte) durante la creazione della tabella o l'inserimento dei dati. Queste dimensioni delle righe eccessive possono causare errori (ad esempio, l'errore 512) durante le normali operazioni, ad esempio un aggiornamento della chiave dell'indice cluster o l'ordinamento del set di colonne completo, che gli utenti non possono prevedere finché non eseguono un'operazione.
  
##  <a name="_character"></a>Conversione di dati di tipo carattere  
Se un'espressione di caratteri viene convertita in un tipo di dati carattere di dimensioni diverse, i valori troppo lunghi per il nuovo tipo di dati vengono troncati. Il **uniqueidentifier** viene considerato un tipo di carattere ai fini di conversione da un'espressione di caratteri e pertanto è soggetto alle regole di troncamento per la conversione in un tipo di carattere. Vedere la sezione Esempi riportata di seguito.
  
Quando un'espressione di caratteri viene convertita in un'espressione di caratteri di un tipo di dati diverso o le dimensioni, ad esempio da **char (5)** a **varchar (5)**, o **char (20)** a **char (15)**, il valore convertito vengono assegnate le regole di confronto del valore di input. Se un'espressione non di caratteri viene convertita in dati di tipo carattere, al valore convertito vengono assegnate le regole di confronto predefinite del database corrente. In entrambi i casi, è possibile assegnare regole di confronto specifiche tramite la [COLLATE](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9) clausola.
  
> [!NOTE]  
>  Conversioni di tabella codici sono supportate per **char** e **varchar** tipi di dati, ma non per **testo** tipo di dati. Come nel caso delle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la perdita di dati durante le conversioni di tabella codici non viene segnalata.  
  
Le espressioni che vengono convertite in un valore approssimato di caratteri **numerico** tipo di dati può includere una notazione esponenziale facoltativa (una e minuscola o maiuscola seguita da un segno facoltativo più (+) o meno (-) e quindi da un numero).
  
Le espressioni che vengono convertite in un valore esatto di caratteri **numerico** tipo di dati deve essere composto da cifre, un separatore decimale e facoltativa più (+) o meno (-). Gli spazi vuoti iniziali vengono ignorati. L'utilizzo della virgola come separatore, ad esempio come separatore decimale nel numero 123.456,00 non è consentito.
  
Per essere convertite in espressioni di caratteri **money** o **smallmoney** tipi di dati possono includere inoltre un separatore decimale facoltativo e il segno di dollaro ($). L'utilizzo della virgola come separatore decimale, ad esempio $ 123.456,00, è consentito.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-showing-the-default-value-of-n-when-used-in-variable-declaration"></a>A. Visualizzazione del valore predefinito di n se utilizzato per la dichiarazione di variabili.  
Nell'esempio seguente viene illustrato il valore predefinito di  *n*  è 1 per il `char` e `varchar` tipi di dati quando vengono utilizzati nella dichiarazione di variabile.
  
```sql
DECLARE @myVariable AS varchar = 'abc';  
DECLARE @myNextVariable AS char = 'abc';  
--The following returns 1  
SELECT DATALENGTH(@myVariable), DATALENGTH(@myNextVariable);  
GO  
```  
  
### <a name="b-showing-the-default-value-of-n-when-varchar-is-used-with-cast-and-convert"></a>B. Visualizzazione del valore predefinito di n se varchar viene utilizzato con CAST e CONVERT.  
Nell'esempio seguente viene illustrato che il valore predefinito di  *n*  è 30 quando il `char` o `varchar` vengono utilizzati tipi di dati con il `CAST` e `CONVERT` funzioni.
  
```sql
DECLARE @myVariable AS varchar(40);  
SET @myVariable = 'This string is longer than thirty characters';  
SELECT CAST(@myVariable AS varchar);  
SELECT DATALENGTH(CAST(@myVariable AS varchar)) AS 'VarcharDefaultLength';  
SELECT CONVERT(char, @myVariable);  
SELECT DATALENGTH(CONVERT(char, @myVariable)) AS 'VarcharDefaultLength';  
```  
  
### <a name="c-converting-data-for-display-purposes"></a>C. Conversione di dati per la visualizzazione  
Nell'esempio seguente vengono convertite due colonne in dati di tipo carattere e viene utilizzato uno stile che applica un formato specifico ai dati visualizzati. Oggetto **money** tipo viene convertito in dati di tipo carattere e viene applicato lo stile 1, che consente di visualizzare i valori con virgole ogni tre cifre a sinistra del separatore decimale e due cifre a destra del separatore decimale. Oggetto **datetime** tipo viene convertito in dati di tipo carattere e viene applicato lo stile 3, che consente di visualizzare i dati in formato gg/mm/aa. Nella clausola WHERE, una **money** viene eseguito il cast di tipo in un tipo di carattere per eseguire un'operazione di confronto di stringhe.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT  BusinessEntityID,   
   SalesYTD,   
   CONVERT (varchar(12),SalesYTD,1) AS MoneyDisplayStyle1,   
   GETDATE() AS CurrentDate,   
   CONVERT(varchar(12), GETDATE(), 3) AS DateDisplayStyle3  
FROM Sales.SalesPerson  
WHERE CAST(SalesYTD AS varchar(20) ) LIKE '1%';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
BusinessEntityID SalesYTD              DisplayFormat CurrentDate             DisplayDateFormat  
---------------- --------------------- ------------- ----------------------- -----------------  
278              1453719.4653          1,453,719.47  2011-05-07 14:29:01.193 07/05/11  
280              1352577.1325          1,352,577.13  2011-05-07 14:29:01.193 07/05/11  
283              1573012.9383          1,573,012.94  2011-05-07 14:29:01.193 07/05/11  
284              1576562.1966          1,576,562.20  2011-05-07 14:29:01.193 07/05/11  
285              172524.4512           172,524.45    2011-05-07 14:29:01.193 07/05/11  
286              1421810.9242          1,421,810.92  2011-05-07 14:29:01.193 07/05/11  
288              1827066.7118          1,827,066.71  2011-05-07 14:29:01.193 07/05/11  
```  
  
### <a name="d-converting-uniqueidentifer-data"></a>D. Conversione del tipo di dati uniqueidentifier  
Nell'esempio seguente un valore `uniqueidentifier` viene convertito in un tipo di dati `char`.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
Nell'esempio seguente viene illustrato il troncamento dei dati quando il valore è troppo lungo per il tipo di dati in cui avviene la conversione. Poiché il **uniqueidentifier** tipo è limitato a 36 caratteri, i caratteri che superano tale lunghezza vengono troncati.
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[nchar e nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Stimare le dimensioni di un database](../../relational-databases/databases/estimate-the-size-of-a-database.md)
  
  
