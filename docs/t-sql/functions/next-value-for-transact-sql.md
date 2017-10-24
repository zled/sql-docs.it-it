---
title: Il valore successivo per (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/19/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEXT_VALUE_TSQL
- NEXT
- NEXT VALUE
- NEXT VALUE FOR
- NEXT_TSQL
- NEXT_VALUE_FOR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEXT VALUE FOR function
- sequence number object, NEXT VALUE FOR function
ms.assetid: 92632ed5-9f32-48eb-be28-a5e477ef9076
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aab8020fa04b978d7ec1b657fe0a1084123dfb48
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="next-value-for-transact-sql"></a>NEXT VALUE FOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Genera un numero di sequenza dall'oggetto sequenza specificato.  
  
 Per una descrizione completa della creazione e utilizzo delle sequenze, vedere [numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md). Utilizzare [sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md) per generare un intervallo di numeri di sequenza.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NEXT VALUE FOR [ database_name . ] [ schema_name . ]  sequence_name  
   [ OVER (<over_order_by_clause>) ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database contenente l'oggetto sequenza.  
  
 *schema_name*  
 Nome dello schema contenente l'oggetto sequenza.  
  
 *sequence_name*  
 Nome dell'oggetto sequenza che genera il numero.  
  
 *over_order_by_clause*  
 Determina l'ordine in cui il valore della sequenza viene assegnato alle righe in una partizione. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce un numero utilizzando il tipo della sequenza.  
  
## <a name="remarks"></a>Osservazioni  
 Il **NEXT VALUE FOR** funzione può essere utilizzata in stored procedure e trigger.  
  
 Quando il **NEXT VALUE FOR** funzione viene utilizzata in un vincolo predefinito o di query, se lo stesso oggetto sequenza viene utilizzato più di una volta o se lo stesso oggetto sequenza viene utilizzato nell'istruzione che fornisce i valori e in un vincolo predefinito l'esecuzione, verrà restituito lo stesso valore per tutte le colonne che fanno riferimento alla stessa sequenza all'interno di una riga nel set di risultati.  
  
 Il **NEXT VALUE FOR** funzione è non deterministica ed è consentita solo in contesti in cui il numero di valori di sequenza generati è ben definito. Di seguito è riportata la definizione del numero di valori che verranno utilizzati per ogni oggetto sequenza a cui viene fatto riferimento in una determinata istruzione:  
  
-   **Selezionare** -per ogni oggetto sequenza a cui fa riferimento, un nuovo valore viene generato una volta per ogni riga nel risultato dell'istruzione.  
  
-   **INSERIRE** ... **I valori** -per ogni oggetto sequenza a cui fa riferimento, un nuovo valore viene generato una volta per ogni riga inserita nell'istruzione.  
  
-   **AGGIORNAMENTO** -per ogni oggetto sequenza a cui fa riferimento, viene generato un nuovo valore per ogni riga aggiornata dall'istruzione.  
  
-   Istruzioni procedurali (ad esempio **DECLARE**, **impostare**e così via), per ogni oggetto sequenza a cui fa riferimento, viene generato un nuovo valore per ogni istruzione.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Il **NEXT VALUE FOR** funzione non può essere utilizzata nelle situazioni seguenti:  
  
-   Il database è in modalità sola lettura.  
  
-   Come argomento per una funzione con valori di tabella.  
  
-   Come argomento per una funzione di aggregazione.  
  
-   Nelle sottoquery che includono espressioni di tabella comuni e tabelle derivate.  
  
-   Nelle viste, nelle funzioni definite dall'utente o nelle colonne calcolate.  
  
-   In un'istruzione che usa il **DISTINCT**, **unione**, **UNION ALL**, **EXCEPT** o **INTERSECT** operatore.  
  
-   In un'istruzione che usa il **ORDER BY** clausola a meno che non **NEXT VALUE FOR** ... **SU** (**ORDER BY** ...) viene utilizzato.  
  
-   Nelle clausole seguenti: **recuperare**, **su**, **OUTPUT**, **ON**, **PIVOT**,  **La trasformazione UNPIVOT**, **RAGGRUPPARE**, **HAVING**, **calcolo**, **COMPUTE BY**, o **diFORXML**.  
  
-   In espressioni condizionali utilizzando **CASE**, **scegliere**, **COALESCE**, **IIF**, **ISNULL**, o  **NULLIF**.  
  
-   In un **valori** clausola che non fa parte di un **inserire** istruzione.  
  
-   Nella definizione di un vincolo CHECK.  
  
-   Nella definizione di un oggetto predefinito o di una regola. Può essere utilizzata in un vincolo predefinito.  
  
-   Come valore predefinito in un tipo di tabella definito dall'utente.  
  
-   In un'istruzione che usa **TOP**, **OFFSET**, o quando il **ROWCOUNT** opzione è impostata.  
  
-   Nel **dove** clausola di un'istruzione.  
  
-   In un **MERGE** istruzione. (Tranne quando la **NEXT VALUE FOR** funzione viene utilizzata in un vincolo predefinito nella tabella di destinazione e l'impostazione predefinita viene utilizzata per la **crea** istruzione del **MERGE** istruzione.)  
  
## <a name="using-a-sequence-object-in-a-default-constraint"></a>Utilizzo di un oggetto sequenza in un vincolo predefinito  
 Quando si utilizza il **NEXT VALUE FOR** funzione in un vincolo predefinito, applicano le regole seguenti:  
  
-   È possibile fare riferimento a un singolo oggetto sequenza dai vincoli predefiniti in più tabelle.  
  
-   La tabella e l'oggetto sequenza devono risiedere nello stesso database.  
  
-   L'utente che aggiunge il vincolo predefinito deve disporre dell'autorizzazione REFERENCES per l'oggetto sequenza.  
  
-   Non è possibile eliminare un oggetto sequenza a cui viene fatto riferimento da un vincolo predefinito prima che venga eliminato il vincolo predefinito.  
  
-   Lo stesso numero di sequenza viene restituito per tutte le colonne di una riga se più vincoli predefiniti utilizzano lo stesso oggetto sequenza o se lo stesso oggetto sequenza viene utilizzato sia nell'istruzione che fornisce i valori, sia in un vincolo predefinito di cui è in corso l'esecuzione.  
  
-   I riferimenti al **NEXT VALUE FOR** funzione in un vincolo predefinito non è possibile specificare il **su** clausola.  
  
-   È possibile modificare un oggetto sequenza a cui viene fatto riferimento in un vincolo predefinito.  
  
-   In caso di un `INSERT … SELECT` o `INSERT … EXEC` istruzione in cui i dati inseriti provengono da una query tramite un **ORDER BY** clausola, i valori restituiti dal **NEXT VALUE FOR** sarà (funzione) generati nell'ordine specificato da di **ORDER BY** clausola.  
  
## <a name="using-a-sequence-object-with-an-over-order-by-clause"></a>Utilizzo di un oggetto sequenza con una clausola OVER ORDER BY  
 Il **NEXT VALUE FOR** funzione supporta la generazione di valori di sequenza ordinati applicando la **su** clausola per la **NEXT VALUE FOR** chiamare. Tramite il **su** clausola, un utente si garantisce che i valori restituiti vengono generati nell'ordine del **su** della clausola **ordine B**sottoclausola Y. Le regole aggiuntive seguenti si applicano quando si utilizza il **NEXT VALUE FOR** utilizzabile con il **su** clausola:  
  
-   Più chiamate al metodo di **NEXT VALUE FOR** funzionerà per lo stesso generatore di sequenza in una singola istruzione deve tutte utilizzare la stessa **su** definizione della clausola.  
  
-   Più chiamate al metodo di **NEXT VALUE FOR** funzione che riferimento generatori di sequenza diversi in una singola istruzione possono avere diversi **su** definizioni della clausola.  
  
-   Un **su** clausola applicata al **NEXT VALUE FOR** funzione non supporta il **PARTITION BY** clausola sub.  
  
-   Se tutte le chiamate per il **NEXT VALUE FOR** funzionare in un **selezionare** istruzione specifica il **su** clausola, un **ORDER BY** clausola può essere utilizzata in il **selezionare** istruzione.  
  
-   Il **su** clausola è consentita con la **NEXT VALUE FOR** funzionano se utilizzati in un **selezionare** istruzione o `INSERT … SELECT …` istruzione. Utilizzare il **su** clausola con il **NEXT VALUE FOR** funzione non è consentita **aggiornamento** o **MERGE** istruzioni.  
  
-   Se un altro processo accede contemporaneamente all'oggetto sequenza, i numeri restituiti potrebbero presentare vuoti.  
  
## <a name="metadata"></a>Metadati  
 Per informazioni sulle sequenze, eseguire una query di [Sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md) vista del catalogo.  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
 Richiede **aggiornamento** l'autorizzazione per l'oggetto sequenza o lo schema della sequenza. Per un esempio relativo alla concessione di autorizzazioni, vedere l'esempio F più avanti in questo argomento.  
  
### <a name="ownership-chaining"></a>Concatenamento della proprietà  
 Gli oggetti sequenza supportano il concatenamento della proprietà. Se l'oggetto sequenza appartiene allo stesso proprietario della tabella, del trigger o della stored procedure chiamante (con oggetto sequenza come vincolo predefinito), non è necessario effettuare alcuna verifica delle autorizzazioni per l'oggetto sequenza. Se l'oggetto sequenza non appartiene allo stesso utente della tabella, del trigger o della stored procedure chiamante, è necessario effettuare la verifica delle autorizzazioni per l'oggetto sequenza.  
  
 Quando il **NEXT VALUE FOR** funzione viene utilizzata come valore predefinito in una tabella, gli utenti richiedono sia **inserire** autorizzazione per la tabella, e **aggiornamento** autorizzazione per l'oggetto sequenza , per inserire dati utilizzando il valore predefinito.  
  
-   Se il vincolo predefinito appartiene allo stesso proprietario dell'oggetto sequenza, non sono necessarie autorizzazioni per l'oggetto sequenza quando viene chiamato il vincolo predefinito.  
  
-   Se il vincolo predefinito e l'oggetto sequenza non appartengono allo stesso utente, sono necessarie autorizzazioni per l'oggetto sequenza anche se viene chiamato attraverso il vincolo predefinito.  
  
### <a name="audit"></a>Controllo  
 Per controllare il **NEXT VALUE FOR** di funzione, monitorare SCHEMA_OBJECT_ACCESS_GROUP.  
  
## <a name="examples"></a>Esempi  
 Per esempi di creazione di sequenze e utilizzando il **NEXT VALUE FOR** funzione per generare numeri di sequenza, vedere [numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 Negli esempi seguenti viene utilizzata una sequenza denominata `CountBy1` in uno schema denominato `Test`. Eseguire l'istruzione seguente per creare la sequenza `Test.CountBy1`. Gli esempi C e E utilizzano il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], pertanto la sequenza `CountBy1` viene creata in questo database.  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Test;  
GO  
  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="a-using-a-sequence-in-a-select-statement"></a>A. Utilizzo di una sequenza in un'istruzione SELECT  
 Nell'esempio seguente viene creata una sequenza denominata `CountBy1` che aumenta di uno ogni volta che viene utilizzata.  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1 AS FirstUse;  
SELECT NEXT VALUE FOR Test.CountBy1 AS SecondUse;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FirstUse  
1  
  
SecondUse  
2
```  
  
### <a name="b-setting-a-variable-to-the-next-sequence-value"></a>B. Impostazione di una variabile sul valore di sequenza successivo  
 Nell'esempio seguente vengono illustrati tre modi per impostare una variabile sul valore successivo di un numero di sequenza.  
  
```  
DECLARE @myvar1 bigint = NEXT VALUE FOR Test.CountBy1  
DECLARE @myvar2 bigint ;  
DECLARE @myvar3 bigint ;  
SET @myvar2 = NEXT VALUE FOR Test.CountBy1 ;  
SELECT @myvar3 = NEXT VALUE FOR Test.CountBy1 ;  
SELECT @myvar1 AS myvar1, @myvar2 AS myvar2, @myvar3 AS myvar3 ;  
GO  
```  
  
### <a name="c-using-a-sequence-with-a-ranking-window-function"></a>C. Utilizzo di una sequenza con una funzione finestra di rango  
  
```  
USE AdventureWorks2012 ;  
GO  
  
SELECT NEXT VALUE FOR Test.CountBy1 OVER (ORDER BY LastName) AS ListNumber,  
    FirstName, LastName  
FROM Person.Contact ;  
GO  
```  
  
### <a name="d-using-the-next-value-for-function-in-the-definition-of-a-default-constraint"></a>D. Utilizzo della funzione NEXT VALUE FOR nella definizione di un vincolo predefinito  
 Utilizzo di **NEXT VALUE FOR** funzione nella definizione di un vincolo predefinito è supportata. Per un esempio di utilizzo **NEXT VALUE FOR** in un **CREATE TABLE** istruzione, vedere l'esempio C[numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md). Nell'esempio seguente viene utilizzato `ALTER TABLE` per aggiungere una sequenza come impostazione predefinita a una tabella corrente.  
  
```  
CREATE TABLE Test.MyTable  
(  
    IDColumn nvarchar(25) PRIMARY KEY,  
    name varchar(25) NOT NULL  
) ;  
GO  
  
CREATE SEQUENCE Test.CounterSeq  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
ALTER TABLE Test.MyTable  
    ADD   
        DEFAULT N'AdvWorks_' +   
        CAST(NEXT VALUE FOR Test.CounterSeq AS NVARCHAR(20))   
        FOR IDColumn;  
GO  
  
INSERT Test.MyTable (name)  
VALUES ('Larry') ;  
GO  
  
SELECT * FROM Test.MyTable;  
GO  
```  
  
### <a name="e-using-the-next-value-for-function-in-an-insert-statement"></a>E. Utilizzo della funzione NEXT VALUE FOR in un'istruzione INSERT  
 Nell'esempio seguente viene creata una tabella denominata `TestTable` e viene utilizzata la funzione `NEXT VALUE FOR` per inserire una riga.  
  
```  
CREATE TABLE Test.TestTable  
     (CounterColumn int PRIMARY KEY,  
    Name nvarchar(25) NOT NULL) ;   
GO  
  
INSERT Test.TestTable (CounterColumn,Name)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Syed') ;  
GO  
  
SELECT * FROM Test.TestTable;   
GO  
  
```  
  
### <a name="e-using-the-next-value-for-function-with-select--into"></a>E. Uso della funzione NEXT VALUE FOR con SELECT ... INTO  
 L'esempio seguente usa il `SELECT … INTO` istruzione per creare una tabella denominata `Production.NewLocation` e utilizza il `NEXT VALUE FOR` funzione per numerare ogni riga.  
  
```  
USE AdventureWorks2012 ;   
GO  
  
SELECT NEXT VALUE FOR Test.CountBy1 AS LocNumber, Name   
    INTO Production.NewLocation  
    FROM Production.Location ;  
GO  
  
SELECT * FROM Production.NewLocation ;  
GO  
```  
  
### <a name="f-granting-permission-to-execute-next-value-for"></a>F. Concessione dell'autorizzazione per eseguire NEXT VALUE FOR  
 Nell'esempio seguente viene concessa **aggiornamento** autorizzazione a un utente denominato `AdventureWorks\Larry` dell'autorizzazione per eseguire `NEXT VALUE FOR` utilizzando il `Test.CounterSeq` sequenza.  
  
```  
GRANT UPDATE ON OBJECT::Test.CounterSeq TO [AdventureWorks\Larry] ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [Numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  

