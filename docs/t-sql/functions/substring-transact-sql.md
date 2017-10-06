---
title: SUBSTRING (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUBSTRING
- SUBSTRING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- portion of expression returned [SQL Server]
- part of expression returned [SQL Server]
- SUBSTRING function
- offsets [SQL Server]
- binary [SQL Server], returning part of
- expressions [SQL Server], part returned
- characters [SQL Server], returning part of
ms.assetid: a19c808f-aaf9-4a69-af59-b1a5fc3e5c4c
caps.latest.revision: 65
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7f36ec82c65e5d52c2186c67033adddbf1700c4d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="substring-transact-sql"></a>SUBSTRING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce parte di un'espressione di tipo carattere, binario, testo o immagine in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SUBSTRING ( expression ,start , length )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un **carattere**, **binario**, **testo**, **ntext**, o **immagine**[espressione](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *inizio*  
 È un numero intero o **bigint** espressione che specifica il punto di inizio dei caratteri restituiti. (La numerazione è 1 base, significa che il primo carattere dell'espressione è 1). Se *avviare* è minore di 1, l'espressione restituita inizierà con il primo carattere specificato in *espressione*. In questo caso, il numero di caratteri restituiti è il valore massimo della somma delle *avviare* + *lunghezza*- 1 oppure 0. Se *avviare* è maggiore del numero di caratteri nell'espressione valore, viene restituita un'espressione di lunghezza zero.  
  
 *length*  
 È un numero intero positivo o **bigint** espressione che specifica il numero di caratteri del *espressione* verranno restituiti. Se *lunghezza* è negativo, viene generato un errore e l'istruzione viene terminata. Se la somma di *avviare* e *lunghezza* è maggiore del numero di caratteri in *espressione*, l'intera espressione valore iniziando *avviare*viene restituito.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce dati di tipo carattere se *espressione* è uno dei tipi di dati carattere supportato. Restituisce dati binari se *espressione* è uno dei supportati **binario** tipi di dati. Il tipo di dati della stringa restituita corrisponde a quello dell'espressione specificata, con le eccezioni descritte nella tabella seguente.  
  
|Espressione specificata|Tipo restituito|  
|--------------------------|-----------------|  
|**Char**/**varchar**/**testo**|**varchar**|  
|**nchar**/**nvarchar**/**ntext**|**nvarchar**|  
|**binario**/**varbinary**/**immagine**|**varbinary**|  
  
## <a name="remarks"></a>Osservazioni  
 I valori per *avviare* e *lunghezza* deve essere specificato nel numero di caratteri per **ntext**, **char**, o **varchar**  tipi di dati e i byte per **testo**, **immagine**, **binario**, o **varbinary** tipi di dati.  
  
 Il *espressione* deve essere **varchar (max)** o **varbinary (max)** quando il *avviare* o *lunghezza* contiene un valore maggiore di 2.147.483.647.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
 Quando si utilizzano le regole di confronto di caratteri supplementari (SC), entrambi *avviare* e *lunghezza* contare ogni coppia di surrogati *espressione* come un singolo carattere. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-substring-with-a-character-string"></a>A. Utilizzo della funzione SUBSTRING con una stringa di caratteri  
 In questo esempio viene illustrato come restituire solo una parte di una stringa di caratteri. Dal `sys.databases` tabella, questa query restituisce il sistema i nomi di database nella prima colonna, la prima lettera del database nella seconda colonna e i terzi e quarto caratteri nella colonna finale.  
  
```  
SELECT name, SUBSTRING(name, 1, 1) AS Initial ,
SUBSTRING(name, 3, 2) AS ThirdAndFourthCharacters
FROM sys.databases  
WHERE database_id < 5;   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

|name |Initial |ThirdAndFourthCharacters|
|---|--|--|
|master  |m  |ST |
|tempdb  |t  |Management Pack |
|model   |m  |de |
|msdb    |m  |DB |


  
 Di seguito viene illustrato come visualizzare il secondo, il terzo e il quarto carattere della costante stringa `abcdef`.  
  
```  
SELECT x = SUBSTRING('abcdef', 2, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
x  
----------  
bcd  
  
(1 row(s) affected)
```  
  
### <a name="b-using-substring-with-text-ntext-and-image-data"></a>B. Utilizzo della funzione SUBSTRING con dati di tipo text, ntext e image  
  
> [!NOTE]  
>  Per eseguire gli esempi seguenti, è necessario installare il **pubs** database.  
  
 Nell'esempio seguente viene illustrato come restituire i primi 10 caratteri da ognuno di un **testo** e **immagine** colonna di dati nella `pub_info` tabella del `pubs` database. **testo** dati vengono restituiti come **varchar**, e **immagine** dati vengono restituiti come **varbinary**.  
  
```  
USE pubs;  
SELECT pub_id, SUBSTRING(logo, 1, 10) AS logo,   
   SUBSTRING(pr_info, 1, 10) AS pr_info  
FROM pub_info  
WHERE pub_id = '1756';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 pub_id logo    pr_info
------ ---------------------- ----------
1756   0x474946383961E3002500 This is sa

(1 row(s) affected)
```  
  
 Nell'esempio seguente viene illustrato l'effetto della SOTTOSTRINGA sia **testo** e **ntext** dati. In primo luogo nel database `pubs` viene creata una nuova tabella denominata `npub_info`. In secondo luogo viene creata la colonna `pr_info` nella tabella `npub_info` dai primi 80 caratteri della colonna `pub_info.pr_info` e come primo carattere viene aggiunto `ü`. Infine, un `INNER JOIN` recupera tutti i numeri di identificazione al server di pubblicazione e `SUBSTRING` di entrambi i **testo** e **ntext** colonne di informazioni di pubblicazione.  
  
```  
IF EXISTS (SELECT table_name FROM INFORMATION_SCHEMA.TABLES   
      WHERE table_name = 'npub_info')  
   DROP TABLE npub_info;  
GO  
-- Create npub_info table in pubs database. Borrowed from instpubs.sql.  
USE pubs;  
GO  
CREATE TABLE npub_info  
(  
 pub_id char(4) NOT NULL  
    REFERENCES publishers(pub_id)  
    CONSTRAINT UPKCL_npubinfo PRIMARY KEY CLUSTERED,  
pr_info ntext NULL  
);  
  
GO  
  
-- Fill the pr_info column in npub_info with international data.  
RAISERROR('Now at the inserts to pub_info...',0,1);  
  
GO  
  
INSERT npub_info VALUES('0736', N'üThis is sample text data for New Moon Books, publisher 0736 in the pubs database')  
,('0877', N'üThis is sample text data for Binnet & Hardley, publisher 0877 in the pubs databa')  
,('1389', N'üThis is sample text data for Algodata Infosystems, publisher 1389 in the pubs da')  
,('9952', N'üThis is sample text data for Scootney Books, publisher 9952 in the pubs database')  
,('1622', N'üThis is sample text data for Five Lakes Publishing, publisher 1622 in the pubs d')  
,('1756', N'üThis is sample text data for Ramona Publishers, publisher 1756 in the pubs datab')  
,('9901', N'üThis is sample text data for GGG&G, publisher 9901 in the pubs database. GGG&G i')  
,('9999', N'üThis is sample text data for Lucerne Publishing, publisher 9999 in the pubs data');  
GO  
-- Join between npub_info and pub_info on pub_id.  
SELECT pr.pub_id, SUBSTRING(pr.pr_info, 1, 35) AS pr_info,  
   SUBSTRING(npr.pr_info, 1, 35) AS npr_info  
FROM pub_info pr INNER JOIN npub_info npr  
   ON pr.pub_id = npr.pub_id  
ORDER BY pr.pub_id ASC;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-substring-with-a-character-string"></a>C. Utilizzo della funzione SUBSTRING con una stringa di caratteri  
 In questo esempio viene illustrato come restituire solo una parte di una stringa di caratteri. Questa query eseguita nella tabella `dbo.DimEmployee` restituisce il cognome in una colonna e l'iniziale del nome nella seconda colonna.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUBSTRING(FirstName, 1, 1) AS Initial  
FROM dbo.DimEmployee  
WHERE LastName LIKE 'Bar%'  
ORDER BY LastName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
LastName             Initial
-------------------- -------
Barbariol            A
Barber               D
Barreto de Mattos    P
```  
  
 Nell'esempio seguente viene illustrato come restituire il secondo, terzo e quarto carattere della costante stringa `abcdef`.  
  
```  
USE ssawPDW;  
  
SELECT TOP 1 SUBSTRING('abcdef', 2, 3) AS x FROM dbo.DimCustomer;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
x
-----
bcd
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  



