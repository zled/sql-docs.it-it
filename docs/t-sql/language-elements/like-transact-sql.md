---
title: LIKE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ESCAPE
- LIKE
- ESCAPE_TSQL
- LIKE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ESCAPE keyword
- '% (wildcard - character(s) to match)'
- ASCII pattern matching
- pattern searching [SQL Server]
- wildcard characters [SQL Server]
- literals [SQL Server], using wildcards
- character strings [SQL Server], LIKE
- exact matches [SQL Server]
- Boolean functions
- LIKE comparisons
- matching patterns [SQL Server]
- NOT LIKE keyword
ms.assetid: 581fb289-29f9-412b-869c-18d33a9e93d5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4fa2299a1efade9f44de85d02c60286a25aad8d0
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="like-transact-sql"></a>LIKE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Determina se una stringa di caratteri specifica corrisponde a un modello specificato. Il modello può contenere caratteri specifici e caratteri jolly. In una ricerca in base a un modello i normali caratteri devono corrispondere esattamente ai caratteri specificati nella stringa di caratteri del modello. I caratteri jolly tuttavia possono venire abbinati a frammenti arbitrari della stringa. L'utilizzo di caratteri jolly rende l'operatore LIKE più flessibile rispetto all'utilizzo degli operatori di confronto tra stringhe = e !=. Se il tipo di dati degli argomenti non corrisponde a quello della stringa di caratteri, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] converte automaticamente gli argomenti nel tipo di dati della stringa, se possibile.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
match_expression [ NOT ] LIKE pattern [ ESCAPE escape_character ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
match_expression [ NOT ] LIKE pattern  
```  
  
## <a name="arguments"></a>Argomenti  
 *match_expression*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) del tipo di dati carattere.  
  
 *pattern*  
 È la stringa di caratteri da cercare nella *match_expression*e possono includere i seguenti caratteri jolly validi. *modello* può contenere un massimo di 8.000 byte.  
  
|Carattere jolly|Description|Esempio|  
|------------------------|-----------------|-------------|  
|%|Stringa composta da zero o più caratteri.|WHERE title LIKE '%computer%' consente di individuare tutti i titoli di libri che contengono la parola "computer".|  
|_ (carattere di sottolineatura)|Carattere singolo.|WHERE au_fname LIKE '_ean' consente di individuare tutti i nomi di persona composti da quattro lettere che terminano in "ean" (Dean, Sean e così via).|  
|[ ]|Carattere singolo compreso nell'intervallo ([a-f]) o nel set ([abcdef]) specificato.|WHERE au_lname LIKE '[C-P]arsen' consente di individuare tutti gli autori il cui cognome termina in "arsen" e inizia con un carattere compreso tra C e P, ad esempio Carsen, Larsen, Karsen e così via. Nelle ricerche basate su intervalli i caratteri inclusi nell'intervallo possono variare a seconda delle regole di ordinamento delle regole di confronto.|  
|[^]|Carattere singolo non compreso nell'intervallo ([^a-f]) o nel set ([^abcdef]) specificato.|WHERE au_lname LIKE 'de[^l]%' consente di individuare tutti gli autori il cui cognome inizia con "de" e la lettera successiva è diversa da "l".|  
  
 *escape_character*  
 Carattere posto davanti a un carattere jolly a indicare che il carattere jolly deve essere interpretato come carattere normale e non come carattere jolly. *escape_character* è un'espressione di caratteri che non dispone di alcun valore predefinito e deve restituire un solo carattere.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="result-value"></a>Valore restituito  
 LIKE restituisce TRUE se il *match_expression* corrisponde al valore specificato *modello*.  
  
## <a name="remarks"></a>Osservazioni  
 Se si esegue un confronto di stringe utilizzando LIKE, tutti i caratteri nella stringa modello sono significativi, compresi gli spazi iniziali e finali. Se un confronto in una query deve restituire tutte le righe contenenti la stringa LIKE 'abc ' (abc seguito da uno spazio), una riga il cui valore per la colonna è abc (abc non seguito da alcuno spazio) non viene restituita. Gli spazi vuoti finali vengono tuttavia ignorati nell'espressione corrispondente al modello. Se un confronto in una query deve restituire tutte le righe contenenti la stringa LIKE 'abc' (abc non seguito da alcuno spazio), vengono restituite tutte le righe che iniziano con abc seguito da zero o più spazi vuoti finali.  
  
 Un confronto tra stringhe con uno schema che contiene **char** e **varchar** dati potrebbero non superare i confronti LIKE a causa di modalità di archiviazione di dati. È importante capire la modalità di archiviazione di ogni tipo di dati e i casi in cui i confronti LIKE potrebbero avere esito negativo. Nell'esempio seguente passa una variabile locale **char** variabile a una stored procedure e viene utilizzato un modello di corrispondenza per trovare tutti i dipendenti il cui cognome inizia con un set di caratteri specificato.  
  
```sql
-- Uses AdventureWorks  
  
CREATE PROCEDURE FindEmployee @EmpLName char(20)  
AS  
SELECT @EmpLName = RTRIM(@EmpLName) + '%';  
SELECT p.FirstName, p.LastName, a.City  
FROM Person.Person p JOIN Person.Address a ON p.BusinessEntityID = a.AddressID  
WHERE p.LastName LIKE @EmpLName;  
GO  
EXEC FindEmployee @EmpLName = 'Barb';  
GO  
```  
  
 Nel `FindEmployee` procedura, viene restituita alcuna riga perché la **char** variabile (`@EmpLName`) contiene spazi vuoti finali ogni volta che il nome contiene meno di 20 caratteri. Poiché il `LastName` colonna **varchar**, non esistono gli spazi vuoti finali. Questa procedura ha esito negativo in quanto gli spazi vuoti finali sono significativi.  
  
 Tuttavia, nell'esempio seguente ha esito positivo perché gli spazi vuoti finali non vengono aggiunti a un **varchar** variabile.  
  
```sql
-- Uses AdventureWorks  
  
CREATE PROCEDURE FindEmployee @EmpLName varchar(20)  
AS  
SELECT @EmpLName = RTRIM(@EmpLName) + '%';  
SELECT p.FirstName, p.LastName, a.City  
FROM Person.Person p JOIN Person.Address a ON p.BusinessEntityID = a.AddressID  
WHERE p.LastName LIKE @EmpLName;  
GO  
EXEC FindEmployee @EmpLName = 'Barb';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 FirstName      LastName            City
 ----------     -------------------- --------------- 
 Angela         Barbariol            Snohomish
 David          Barber               Snohomish
 (2 row(s) affected)  
 ``` 
 
## <a name="pattern-matching-by-using-like"></a>Ricerche con l'operatore LIKE basate su modello  
 LIKE supporta ricerche ASCII e ricerche Unicode. Quando tutti gli argomenti (*match_expression*, *modello*, e *escape_character*, se presente) sono tipi di dati carattere ASCII, criteri di ricerca ASCII viene eseguito. Se il tipo di dati di uno degli argomenti è Unicode, tutti gli argomenti vengono convertiti in Unicode e viene eseguita una ricerca Unicode. Quando si utilizzano dati Unicode (**nchar** o **nvarchar** tipi di dati) con LIKE, gli spazi vuoti finali sono significativi, tuttavia, per i dati non Unicode, spazi vuoti finali non sono significativi. L'operatore LIKE per Unicode è compatibile con lo standard ISO. L'operatore LIKE per ASCII è compatibile con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Negli esempi seguenti vengono illustrate le differenze tra le righe restituite da ricerche LIKE per ASCII e per Unicode.  
  
```sql  
-- ASCII pattern matching with char column  
CREATE TABLE t (col1 char(30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE col1 LIKE '% King';   -- returns 1 row  
  
-- Unicode pattern matching with nchar column  
CREATE TABLE t (col1 nchar(30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE col1 LIKE '% King';   -- no rows returned  
  
-- Unicode pattern matching with nchar column and RTRIM  
CREATE TABLE t (col1 nchar (30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE RTRIM(col1) LIKE '% King';   -- returns 1 row  
```  
  
> [!NOTE]  
>  I confronti tra stringhe con l'operatore LIKE sono interessati dalle regole di confronto. Per altre informazioni, vedere [COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md).  
  
## <a name="using-the--wildcard-character"></a>Utilizzo del carattere jolly %  
 Se si specifica il simbolo LIKE '5%', [!INCLUDE[ssDE](../../includes/ssde-md.md)] esegue la ricerca del numero 5 seguito da una stringa di zero o più caratteri.  
  
 Ad esempio, la query seguente visualizza tutte le viste a gestione dinamica nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in quanto tutte iniziano con le lettere `dm`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT Name  
FROM sys.system_views  
WHERE Name LIKE 'dm%';  
GO  
```  
  
 Per visualizzare tutti gli oggetti che non sono viste a gestione dinamica, utilizzare `NOT LIKE 'dm%'`. Se sono disponibili 32 oggetti e tramite l'operatore LIKE vengono trovati 13 nomi corrispondenti al modello specificato, NOT LIKE troverà i 19 oggetti che non corrispondono al modello LIKE.  
  
 Non sempre è possibile trovare gli stessi nomi utilizzando un modello quale, ad esempio, `LIKE '[^d][^m]%'`. Anziché 19 nomi, è possibile trovarne solo 14, ovvero tutti i nomi che iniziano con `d` o hanno la lettera `m` in seconda posizione vengono eliminati dai risultati, nonché i nomi delle viste a gestione dinamica. Ciò si verifica perché le stringhe individuate tramite caratteri jolly negativi vengono valutate in fasi successive, un carattere jolly alla volta. La voce viene eliminata se la corrispondenza ha esito negativo durante una qualunque fase della valutazione.  
  
## <a name="using-wildcard-characters-as-literals"></a>Utilizzo di caratteri jolly come valori letterali  
 Nelle ricerche è possibile utilizzare i caratteri jolly come caratteri letterali racchiudendo il carattere jolly tra virgolette. Nella tabella seguente vengono descritti vari esempi di utilizzo della parola chiave LIKE e dei caratteri jolly [ ].  
  
|Simbolo|Significato|  
|------------|-------------|  
|LIKE '5[%]'|5%|  
|LIKE '[_]n'|_n|  
|LIKE '[a-cdf]'|a, b, c, d oppure f|  
|LIKE '[-acdf]'|-, a, c, d oppure f|  
|LIKE '[ [ ]'|[|  
|LIKE ']'|]|  
|LIKE 'abc[_]d%'|abc_d e abc_de|  
|LIKE 'abc[def]'|abcd, abce e abcf|  
  
## <a name="pattern-matching-with-the-escape-clause"></a>Ricerche con la clausola ESCAPE  
 È possibile eseguire ricerche di stringhe di caratteri che includono uno o più caratteri speciali. Ad esempio, nella tabella discounts di un database customers è possibile archiviare i valori relativi allo sconto che includono il segno di percentuale (%). Per cercare il segno di percentuale come carattere e non come carattere jolly, è necessario specificare la parola chiave ESCAPE e il carattere di escape. Ad esempio, un database di esempio include una colonna denominata comment contenente il testo 30%. Per cercare le righe contenenti la stringa 30% all'interno della colonna dei commenti, specificare una clausola WHERE, ad esempio `WHERE comment LIKE '%30!%%' ESCAPE '!'`. Se ESCAPE e il carattere di escape non vengono specificati, [!INCLUDE[ssDE](../../includes/ssde-md.md)] restituisce tutte le righe contenenti la stringa 30.  
  
 Se dopo un carattere di escape non è presente alcun carattere nel modello LIKE, il modello non è valido e l'operatore LIKE restituisce FALSE. Se il carattere successivo al carattere di escape non è un carattere jolly, il carattere di escape viene eliminato e il carattere successivo viene considerato come un carattere normale nel modello. Ciò è valido per il segno di percentuale (%), il carattere di sottolineatura (_) e la parentesi quadra aperta ([) quando questi caratteri jolly sono racchiusi tra doppie parentesi quadre ([ ]). I caratteri di escape possono inoltre essere utilizzati all'interno di doppie parentesi quadre ([ ]), mentre è possibile far precedere da una carattere di escape anche l'accento circonflesso (^), il trattino (-) e la parentesi quadra chiusa (]).  
  
 0x0000 (**char(0)**) è un carattere non definito nelle regole di confronto di Windows e non può essere incluso in LIKE.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-like-with-the--wildcard-character"></a>A. Utilizzo dell'operatore LIKE con il carattere jolly %  
 Nell'esempio seguente viene eseguita una ricerca di tutti i numeri telefonici con prefisso `415` nella tabella `PersonPhone`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, ph.PhoneNumber  
FROM Person.PersonPhone AS ph  
INNER JOIN Person.Person AS p  
ON ph.BusinessEntityID = p.BusinessEntityID  
WHERE ph.PhoneNumber LIKE '415%'  
ORDER by p.LastName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
 
 ```
 FirstName             LastName             Phone
 -----------------     -------------------  ------------
 Ruben                 Alonso               415-555-124  
 Shelby                Cook                 415-555-0121  
 Karen                 Hu                   415-555-0114  
 John                  Long                 415-555-0147  
 David                 Long                 415-555-0123  
 Gilbert               Ma                   415-555-0138  
 Meredith              Moreno               415-555-0131  
 Alexandra             Nelson               415-555-0174  
 Taylor                Patterson            415-555-0170  
 Gabrielle              Russell             415-555-0197  
 Dalton                 Simmons             415-555-0115  
 (11 row(s) affected)  
 ``` 
 
### <a name="b-using-not-like-with-the--wildcard-character"></a>B. Utilizzo dell'operatore NOT LIKE con il carattere jolly %  
 Nell'esempio seguente viene eseguita una ricerca di tutti i numeri telefonici nella tabella `PersonPhone` il cui prefisso è diverso da `415`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, ph.PhoneNumber  
FROM Person.PersonPhone AS ph  
INNER JOIN Person.Person AS p  
ON ph.BusinessEntityID = p.BusinessEntityID  
WHERE ph.PhoneNumber NOT LIKE '415%' AND p.FirstName = 'Gail'  
ORDER BY p.LastName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
 
 ```
FirstName              LastName            Phone
---------------------- -------------------- -------------------
Gail                  Alexander            1 (11) 500 555-0120  
Gail                  Butler               1 (11) 500 555-0191  
Gail                  Erickson             834-555-0132  
Gail                  Erickson             849-555-0139  
Gail                  Griffin              450-555-0171  
Gail                  Moore                155-555-0169  
Gail                  Russell              334-555-0170  
Gail                  Westover             305-555-0100  
(8 row(s) affected)  
```  

### <a name="c-using-the-escape-clause"></a>C. Utilizzo della clausola ESCAPE  
 Nell'esempio seguente vengono utilizzati la clausola `ESCAPE` e il carattere di escape per cercare la stringa di caratteri esatta `10-15%` nella colonna `c1` della tabella `mytbl2`.  
  
```sql
USE tempdb;  
GO  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'mytbl2')  
   DROP TABLE mytbl2;  
GO  
USE tempdb;  
GO  
CREATE TABLE mytbl2  
(  
 c1 sysname  
);  
GO  
INSERT mytbl2 VALUES ('Discount is 10-15% off'), ('Discount is .10-.15 off');  
GO  
SELECT c1   
FROM mytbl2  
WHERE c1 LIKE '%10-15!% off%' ESCAPE '!';  
GO  
```  
  
### <a name="d-using-the---wildcard-characters"></a>D. Utilizzo del carattere jolly [ ]  
 Nell'esempio seguente consente di trovare i dipendenti nel `Person` tabella con il nome di `Cheryl` o `Sheryl`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT BusinessEntityID, FirstName, LastName   
FROM Person.Person   
WHERE FirstName LIKE '[CS]heryl';  
GO  
```  
  
 Nell'esempio seguente vengono restituite le righe relative ai dipendenti nella tabella `Person` con cognome `Zheng` o `Zhang`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT LastName, FirstName  
FROM Person.Person  
WHERE LastName LIKE 'Zh[ae]ng'  
ORDER BY LastName ASC, FirstName ASC;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-like-with-the--wildcard-character"></a>E. Utilizzo dell'operatore LIKE con il carattere jolly %  
 Nell'esempio seguente consente di individuare tutti i dipendenti di `DimEmployee` tabella con numeri di telefono che iniziano con `612`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone LIKE '612%'  
ORDER by LastName;  
```  
  
### <a name="f-using-not-like-with-the--wildcard-character"></a>F. Utilizzo dell'operatore NOT LIKE con il carattere jolly %  
 Nell'esempio seguente consente di individuare tutti i numeri di telefono di `DimEmployee` tabella che non iniziano con `612`.  tramite tabelle annidate.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone NOT LIKE '612%'  
ORDER by LastName;  
```  
  
### <a name="g-using-like-with-the--wildcard-character"></a>G. Utilizzo dell'operatore LIKE con il carattere jolly _  
 Nell'esempio seguente consente di individuare tutti i numeri di telefono che dispone di un codice di area, a partire da `6` e di fine `2` nel `DimEmployee` tabella. Si noti che il carattere jolly % è anche incluso alla fine del criterio di ricerca perché il codice di area è la prima parte del numero di telefono e caratteri aggiuntivi dopo aver sono il valore della colonna.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone LIKE '6_2%'  
ORDER by LastName;   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
 
