---
title: char e varchar (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0d07b9fec8168a21ff492ac216f08881ff278932
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33054748"
---
# <a name="char-and-varchar-transact-sql"></a>char and varchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Questi tipi di dati sono a lunghezza fissa o variabile.  
  
## <a name="arguments"></a>Argomenti  
**char** [ ( *n* ) ] Dati di stringa a lunghezza fissa, non-Unicode. *n* definisce la lunghezza della stringa e deve essere un valore compreso tra 1 e 8.000. Le dimensioni di archiviazione corrispondono a *n* byte. Il sinonimo ISO per **char** è **character**.
  
**varchar** [ ( *n* | **max** ) ] Dati di stringa a lunghezza variabile, non-Unicode. *n* definisce la lunghezza della stringa e può essere un valore compreso tra 1 e 8.000. **max** indica che le dimensioni massime della risorsa di archiviazione sono di 2^31-1 byte (2 GB). Le dimensioni dello spazio di archiviazione corrispondono alla lunghezza effettiva dei dati immessi + 2 byte. I sinonimi ISO per **varchar** sono **charvarying** o **charactervarying**.
  
## <a name="remarks"></a>Remarks  
Se *n* viene omesso in un'istruzione di definizione dei dati o di dichiarazione di variabili, la lunghezza predefinita è 1. Se *n* viene omesso nell'uso delle funzioni CAST e CONVERT, la lunghezza predefinita è 30.
  
Agli oggetti che usano **char** o **varchar** vengono assegnate le regole di confronto predefinite del database, a meno che non vengano assegnate regole di confronto specifiche tramite la clausola COLLATE. Le regole di confronto controllano la tabella codici utilizzata per l'archiviazione dei dati di tipo carattere.
  
Nel caso di siti che supportano più lingue, è consigliabile usare i tipi di dati Unicode **nchar** o **nvarchar** per ridurre al minimo i problemi di conversione dei caratteri. Se si usano i tipi di dati **char** o **varchar**, è consigliabile:
- Usare **char** quando le dimensioni delle voci di dati delle colonne sono coerenti.  
- Usare **varchar** quando le dimensioni delle voci di dati delle colonne presentano notevoli differenze.  
- Usare il tipo di dati **varchar(max)** quando le dimensioni delle voci di dati delle colonne variano in modo significativo e possono essere superiori a 8.000 byte.  
  
Se l'opzione SET ANSI_PADDING è impostata su OFF quando si esegue l'istruzione CREATE TABLE o ALTER TABLE, le colonne di tipo **char** definite come NULL vengono gestite come colonne di tipo **varchar**.
  
Quando la tabella codici delle regole di confronto usa caratteri a doppio byte, le dimensioni di archiviazione risultano comunque pari a *n* byte. In base alla stringa di caratteri, le dimensioni della risorsa di archiviazione di *n* byte possono corrispondere a meno di *n* caratteri.

> [!WARNING]
> Ogni colonna non Null varchar(max) o nvarchar(max) richiede 24 byte di allocazione fissa aggiuntiva che concorre al raggiungimento del limite delle righe di 8.060 byte durante un'operazione di ordinamento. Ciò può creare un limite implicito per il numero di colonne non Null varchar(max) o nvarchar(max) che è possibile creare in una tabella.  
Non vengono segnalati errori particolari (oltre il normale avviso che indica che le dimensioni massime per le righe superano il valore massimo consentito di 8060 byte) durante la creazione della tabella o l'inserimento dei dati. Queste dimensioni delle righe eccessive possono causare errori (ad esempio, l'errore 512) durante le normali operazioni, ad esempio un aggiornamento della chiave dell'indice cluster o l'ordinamento del set di colonne completo, che gli utenti non possono prevedere finché non eseguono un'operazione.
  
##  <a name="_character"></a> Conversione dei dati di tipo carattere  
Se un'espressione di caratteri viene convertita in un tipo di dati carattere di dimensioni diverse, i valori troppo lunghi per il nuovo tipo di dati vengono troncati. Per la conversione da un'espressione di caratteri, il tipo **uniqueidentifier** è considerato un tipo di dati carattere ed è pertanto soggetto alle regole di troncamento per la conversione in un tipo di dati carattere. Vedere la sezione Esempi riportata di seguito.
  
Se un'espressione di caratteri viene convertita in un'espressione di caratteri con tipo di dati o dimensioni diverse, ad esempio da**char(5)** a **varchar(5)**, o da **char(20)** a **char(15)**, al valore convertito vengono assegnate le regole di confronto del valore di input. Se un'espressione non di caratteri viene convertita in dati di tipo carattere, al valore convertito vengono assegnate le regole di confronto predefinite del database corrente. In entrambi i casi è possibile assegnare regole di confronto specifiche mediante la clausola [COLLATE](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9).
  
> [!NOTE]  
>  Le conversioni tra tabelle codici sono supportate per i tipi di dati **char** e **varchar**, ma non per il tipo di dati **text**. Come nel caso delle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la perdita di dati durante le conversioni di tabella codici non viene segnalata.  
  
Le espressioni di caratteri che vengono convertite in un tipo di dati **numeric** approssimato possono includere una notazione esponenziale facoltativa: una e minuscola o maiuscola seguita da un segno più (+) o meno (-) facoltativo e quindi da un numero.
  
Le espressioni di caratteri che vengono convertite in un tipo di dati **numeric** esatto devono includere cifre, il separatore decimale e un segno più (+) o meno (-) facoltativo. Gli spazi vuoti iniziali vengono ignorati. L'utilizzo della virgola come separatore, ad esempio come separatore decimale nel numero 123.456,00 non è consentito.
  
Le espressioni di caratteri che vengono convertite nel tipo di dati **money** o **smallmoney** possono includere anche un separatore decimale e il simbolo di dollaro ($) facoltativi. L'utilizzo della virgola come separatore decimale, ad esempio $ 123.456,00, è consentito.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-showing-the-default-value-of-n-when-used-in-variable-declaration"></a>A. Visualizzazione del valore predefinito di n se utilizzato per la dichiarazione di variabili.  
L'esempio seguente indica che il valore predefinito di *n* è 1 per i tipi di dati `char` e `varchar` quando vengono usati per la dichiarazione di variabili.
  
```sql
DECLARE @myVariable AS varchar = 'abc';  
DECLARE @myNextVariable AS char = 'abc';  
--The following returns 1  
SELECT DATALENGTH(@myVariable), DATALENGTH(@myNextVariable);  
GO  
```  
  
### <a name="b-showing-the-default-value-of-n-when-varchar-is-used-with-cast-and-convert"></a>B. Visualizzazione del valore predefinito di n se varchar viene utilizzato con CAST e CONVERT.  
L'esempio seguente indica che il valore predefinito di *n* è 30 quando i tipi di dati `char` e `varchar` vengono usati con le funzioni `CAST` e `CONVERT`.
  
```sql
DECLARE @myVariable AS varchar(40);  
SET @myVariable = 'This string is longer than thirty characters';  
SELECT CAST(@myVariable AS varchar);  
SELECT DATALENGTH(CAST(@myVariable AS varchar)) AS 'VarcharDefaultLength';  
SELECT CONVERT(char, @myVariable);  
SELECT DATALENGTH(CONVERT(char, @myVariable)) AS 'VarcharDefaultLength';  
```  
  
### <a name="c-converting-data-for-display-purposes"></a>C. Conversione di dati per la visualizzazione  
Nell'esempio seguente vengono convertite due colonne in dati di tipo carattere e viene utilizzato uno stile che applica un formato specifico ai dati visualizzati. Un tipo di dati **money** viene convertito in dati di tipo carattere e viene applicato lo stile 1. Tale stile consente di visualizzare i valori con le virgole ogni tre cifre a sinistra del separatore decimale e due cifre a destra del separatore decimale. Il tipo **datetime** viene convertito nei dati di tipo carattere e viene applicato lo stile 3, che consente di visualizzare i dati nel formato gg/mm/aa. Nella clausola WHERE il cast del tipo **money** viene eseguito a un tipo carattere per eseguire un'operazione di confronto tra stringhe.
  
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
  
Nell'esempio seguente viene illustrato il troncamento dei dati quando il valore è troppo lungo per il tipo di dati in cui avviene la conversione. Poiché la lunghezza del tipo **uniqueidentifier** è limitata a 36 caratteri, i caratteri eccedenti vengono troncati.
  
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
[COLLATE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[Conversione del tipo di dati &#40;motore di database&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Stima delle dimensioni di un database](../../relational-databases/databases/estimate-the-size-of-a-database.md)
  
  
