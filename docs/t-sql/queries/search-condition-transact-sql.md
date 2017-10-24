---
title: Condizione (Transact-SQL) di ricerca | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- search
- Search Condition
- condition
dev_langs:
- TSQL
helpviewer_keywords:
- OR operator [Transact-SQL]
- CONTAINS predicate (Transact-SQL)
- ESCAPE keyword
- operators [Transact-SQL], search condition
- search conditions [SQL Server]
- WHERE clause, search conditions
- ALL keyword
- FREETEXT predicate (Transact-SQL)
- EXISTS keyword
- search conditions [SQL Server], about search conditions
- NOT operator [Transact-SQL]
- BETWEEN operator
- SOME | ANY keyword
- predicates [full-text search]
- AND, about search conditions
- logical operators [SQL Server], about search conditions
- precedence [SQL Server], logical operators
- logical operators [SQL Server], precedence
- LIKE comparisons
ms.assetid: 09974469-c5d2-4be8-bc5a-78e404660b2c
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: ad0a32f2f11c7b0ca781c7e01635204da38fcbdd
ms.contentlocale: it-it
ms.lasthandoff: 10/24/2017

---
# <a name="search-condition-transact-sql"></a>Condizione di ricerca (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combinazione di uno o più predicati tramite gli operatori logici AND, OR e NOT.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
<search_condition> ::=   
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | ! > | < | < = | ! < } expression   
    | string_expression [ NOT ] LIKE string_expression   
  [ ESCAPE 'escape_character' ]   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | CONTAINS   
  ( { column | * } , '<contains_search_condition>' )   
    | FREETEXT ( { column | * } , 'freetext_string' )   
    | expression [ NOT ] IN ( subquery | expression [ ,...n ] )   
    | expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
  { ALL | SOME | ANY} ( subquery )   
    | EXISTS ( subquery )     }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
< search_condition > ::=   
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | < | < = } expression   
    | string_expression [ NOT ] LIKE string_expression   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | expression [ NOT ] IN (subquery | expression [ ,...n ] )   
    | expression [ NOT ] EXISTS (subquery)     }   
```  
  
## <a name="arguments"></a>Argomenti  
 \<search_condition >  
 Specifica le condizioni per le righe restituite nel set dei risultati di un'istruzione SELECT, di un'espressione di query o di una sottoquery. Per un'istruzione UPDATE specifica le righe da aggiornare. Per un'istruzione DELETE specifica le righe da eliminare. Non sussiste alcun limite per il numero di predicati che è possibile includere in una condizione di ricerca di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 NOT  
 Nega l'espressione booleana specificata dal predicato. Per ulteriori informazioni, vedere [non &#40; Transact-SQL &#41; ](../../t-sql/language-elements/not-transact-sql.md).  
  
 AND  
 Combina due condizioni e restituisce TRUE quando entrambe le condizioni sono TRUE. Per ulteriori informazioni, vedere [AND &#40; Transact-SQL &#41; ](../../t-sql/language-elements/and-transact-sql.md).  
  
 o  
 Combina due condizioni e restituisce TRUE quando una delle due condizioni è TRUE. Per ulteriori informazioni, vedere [o &#40; Transact-SQL &#41; ](../../t-sql/language-elements/or-transact-sql.md).  
  
 \<predicato >  
 Espressione che restituisce TRUE, FALSE o UNKNOWN.  
  
 *espressione*  
 Nome di colonna, costante, funzione, variabile, sottoquery scalare o qualsiasi combinazione di costanti, funzioni e nomi di colonna collegati da uno o più operatori oppure da una sottoquery. L'espressione può inoltre includere l'espressione CASE.  
  
> [!NOTE]  
>  Quando si fa riferimento a tipi di dati carattere Unicode **nchar**, **nvarchar**, e **ntext**, 'expression' deve essere preceduto dalla lettera maiuscola ' N' '. Se la lettera "N" non è specificata, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la stringa viene convertita in base alla tabella codici corrispondente alle regole di confronto predefinite del database o della colonna. Tutti i caratteri non trovati nella tabella codici vengono persi.  
  
 =  
 Operatore utilizzato per verificare l'uguaglianza di due espressioni.  
  
 <>  
 Operatore utilizzato per verificare la disuguaglianza di due espressioni.  
  
 !=  
 Operatore utilizzato per verificare la disuguaglianza di due espressioni.  
  
 \>  
 Operatore utilizzato per verificare che un'espressione sia maggiore di un'altra.  
  
 \>=  
 Operatore utilizzato per verificare che un'espressione sia maggiore o uguale a un'altra.  
  
 !>  
 Operatore utilizzato per verificare che un'espressione non sia maggiore di un'altra.  
  
 <  
 Operatore utilizzato per verificare che un'espressione sia minore di un'altra.  
  
 <=  
 Operatore utilizzato per verificare che un'espressione sia minore o uguale a un'altra.  
  
 !<  
 Operatore utilizzato per verificare che un'espressione non sia minore di un'altra.  
  
 *string_expression*  
 Stringa di caratteri e caratteri jolly.  
  
 [ NOT ] LIKE  
 Indica che la successiva stringa di caratteri deve essere utilizzata come criterio di ricerca. Per ulteriori informazioni, vedere [come &#40; Transact-SQL &#41; ](../../t-sql/language-elements/like-transact-sql.md).  
  
 Carattere di ESCAPE **'***escape_ carattere***'**  
 Consente la ricerca di un carattere jolly come carattere effettivo in una stringa di caratteri, ignorando la funzionalità di carattere jolly. *escape_character* è il carattere inserito davanti al carattere jolly per specificarne l'utilizzo speciale.  
  
 [ NOT ] BETWEEN  
 Specifica un intervallo di valori inclusivo. Utilizzare l'operatore AND per separare il valore iniziale da quello finale. Per ulteriori informazioni, vedere [BETWEEN &#40; Transact-SQL &#41; ](../../t-sql/language-elements/between-transact-sql.md).  
  
 IS [NOT] NULL  
 Specifica una ricerca di valori Null o non Null, a seconda delle parole chiave utilizzate. Un'espressione con un operatore bit per bit o aritmetico restituisce NULL se uno degli operandi è NULL.  
  
 CONTAINS  
 Cerca le colonne che contengono dati di tipo carattere per precisa o meno preciso (*fuzzy*) corrisponde a singole parole e frasi, della prossimità delle parole entro una certa distanza una da altra e le corrispondenze ponderate. È possibile utilizzare questa opzione solo con istruzioni SELECT. Per ulteriori informazioni, vedere [CONTAINS &#40; Transact-SQL &#41; ](../../t-sql/queries/contains-transact-sql.md).  
  
 FREETEXT  
 Implementa un tipo semplice di query in linguaggio naturale per l'esecuzione di ricerche in colonne che includono dati di tipo carattere, per individuare valori che corrispondano al significato piuttosto che alle parole esatte del predicato. È possibile utilizzare questa opzione solo con istruzioni SELECT. Per ulteriori informazioni, vedere [FREETEXT &#40; Transact-SQL &#41; ](../../t-sql/queries/freetext-transact-sql.md).  
  
 [ NOT ] IN  
 Specifica la ricerca di un'espressione in base alla presenza o meno di tale espressione in un elenco. L'espressione di ricerca può essere una costante o un nome di colonna. L'elenco può essere un set di costanti o, più comunemente, una sottoquery. Racchiudere l'elenco di valori tra parentesi. Per ulteriori informazioni, vedere [IN &#40; Transact-SQL &#41; ](../../t-sql/language-elements/in-transact-sql.md).  
  
 *sottoquery*  
 Può essere considerato un'istruzione SELECT con restrizioni ed è simile a \<query_expression > nell'istruzione SELECT. La clausola ORDER BY e la parola chiave INTO non sono consentite. Per ulteriori informazioni, vedere [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
 ALL  
 Utilizzato con un operatore di confronto e una sottoquery. Restituisce TRUE per \<predicato > quando tutti i valori recuperati per la sottoquery soddisfano l'operazione di confronto oppure FALSE se non tutti i valori soddisfano il confronto oppure quando la sottoquery non restituisce righe all'istruzione esterna. Per ulteriori informazioni, vedere [tutti &#40; Transact-SQL &#41; ](../../t-sql/language-elements/all-transact-sql.md).  
  
 { SOME | ANY }  
 Utilizzato con un operatore di confronto e una sottoquery. Restituisce TRUE per \<predicato > quando qualsiasi valore recuperato per la sottoquery soddisfa l'operazione di confronto oppure FALSE se nessun valore nella sottoquery soddisfa il confronto oppure quando la sottoquery non restituisce righe all'istruzione esterna. Negli altri casi, l'espressione è UNKNOWN. Per ulteriori informazioni, vedere [alcune &#124; I &#40; Transact-SQL &#41; ](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 EXISTS  
 Utilizzato con una sottoquery per verificare l'esistenza delle righe restituite dalla sottoquery. Per ulteriori informazioni, vedere [EXISTS &#40; Transact-SQL &#41; ](../../t-sql/language-elements/exists-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 L'ordine di precedenza degli operatori logici prevede NOT come operatore con precedenza massima, seguito da AND e quindi da OR. È possibile utilizzare le parentesi per ignorare tale ordine di precedenza in una condizione di ricerca. L'ordine di valutazione degli operatori logici può variare a seconda delle scelte effettuate da Query Optimizer. Per ulteriori informazioni su come gli operatori logici applicati a valori logici, vedere [AND &#40; Transact-SQL &#41; ](../../t-sql/language-elements/and-transact-sql.md), [o &#40; Transact-SQL &#41; ](../../t-sql/language-elements/or-transact-sql.md), e [non &#40; Transact-SQL &#41; ](../../t-sql/language-elements/not-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-where-with-like-and-escape-syntax"></a>A. Utilizzo della clausola WHERE con la sintassi LIKE ed ESCAPE  
 Nell'esempio seguente viene eseguita la ricerca di righe in cui il `LargePhotoFileName` colonna contiene i caratteri `green_`e utilizza il `ESCAPE` opzione perché _ è un carattere jolly. Senza specificare il `ESCAPE` opzione, la query verrebbe eseguita una ricerca per qualsiasi valore di descrizione che contengono la parola `green` seguita da qualsiasi carattere singolo diverso dal carattere _.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT *   
FROM Production.ProductPhoto  
WHERE LargePhotoFileName LIKE '%greena_%' ESCAPE 'a' ;  
```  
  
### <a name="b-using-where-and-like-syntax-with-unicode-data"></a>B. Utilizzo della clausola WHERE e della sintassi LIKE con dati Unicode  
 Nell'esempio seguente viene utilizzata la clausola `WHERE` per recuperare l'indirizzo postale delle società con sede al di fuori degli Stati Uniti (`US`) e in città il cui nome inizia con `Pa`.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT AddressLine1, AddressLine2, City, PostalCode, CountryRegionCode    
FROM Person.Address AS a  
JOIN Person.StateProvince AS s ON a.StateProvinceID = s.StateProvinceID  
WHERE CountryRegionCode NOT IN ('US')  
AND City LIKE N'Pa%' ;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-where-with-like"></a>C. Utilizzo della clausola WHERE con LIKE  
 Nell'esempio seguente viene eseguita la ricerca di righe in cui il `LastName` colonna contiene i caratteri `and`.  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE '%and%';  
```  
  
### <a name="d-using-where-and-like-syntax-with-unicode-data"></a>D. Utilizzo della clausola WHERE e della sintassi LIKE con dati Unicode  
 L'esempio seguente usa il `WHERE` clausola per eseguire una ricerca Unicode il `LastName` colonna.  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE N'%and%';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di aggregazione &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [CASE &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [Cursori &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  


