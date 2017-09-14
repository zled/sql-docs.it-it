---
title: IMPOSTARE @local_variable (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- SET @local_variable
- variables [SQL Server], assigning
- SET statement, @local_variable
- local variables [SQL Server]
ms.assetid: d410e06e-061b-4c25-9973-b2dc9b60bd85
caps.latest.revision: 52
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a92fa424de70d1ba9cccf437a2de49ab8432ba1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-localvariable-transact-sql"></a>IMPOSTARE @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Imposta la variabile locale specificata, creata in precedenza tramite DECLARE @*local_variable* istruzione per il valore specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET   
{ @local_variable  
    [ . { property_name | field_name } ] = { expression | udt_name { . | :: } method_name }  
}  
|  
{ @SQLCLR_local_variable.mutator_method  
}  
|  
{ @local_variable  
    {+= | -= | *= | /= | %= | &= | ^= | |= } expression  
}  
|   
  { @cursor_variable =   
    { @cursor_variable | cursor_name   
    | { CURSOR [ FORWARD_ONLY | SCROLL ]   
        [ STATIC | KEYSET | DYNAMIC | FAST_FORWARD ]   
        [ READ_ONLY | SCROLL_LOCKS | OPTIMISTIC ]   
        [ TYPE_WARNING ]   
    FOR select_statement   
        [ FOR { READ ONLY | UPDATE [ OF column_name [ ,...n ] ] } ]   
      }   
    }  
}   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET @local_variable {+= | -= | *= | /= | %= | &= | ^= | |= } expression  
  
```  
  
## <a name="arguments"></a>Argomenti  
 **@***local_variable*  
 È il nome di una variabile di qualsiasi tipo tranne **cursore**, **testo**, **ntext**, **immagine**, o **tabella**. I nomi delle variabili devono iniziare con un simbolo di chiocciola (**@**). I nomi delle variabili devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 *property_name*  
 Proprietà di un tipo definito dall'utente.  
  
 *nome_campo*  
 Campo pubblico di un tipo definito dall'utente.  
  
 *udt_name*  
 Nome di un tipo CLR (Common Language Runtime) definito dall'utente.  
  
 { **.** | **::** }  
 Specifica un metodo di un tipo CRL definito dall'utente. Per un metodo di istanza (non statico), utilizzare un punto (**.**). Per un metodo statico, utilizzare due punti (**::**). Per richiamare un metodo, una proprietà o un campo di un tipo CLR definito dall'utente, è necessario disporre dell'autorizzazione EXECUTE per il tipo.  
  
 *nome_metodo* **(** *argomento* [ **,**... *n* ] **)**  
 Metodo di un tipo definito dall'utente che accetta uno o più argomenti per modificare lo stato di un'istanza di un tipo. I metodi statici devono essere pubblici.  
  
 **@***SQLCLR_local_variable*  
 È una variabile il cui tipo è situato in un assembly. Per altre informazioni, vedere [Concetti relativi alla programmazione dell'integrazione con CLR &#40;Common Language Runtime&#41;](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md).  
  
 *mutator_method*  
 Metodo dell'assembly che può modificare lo stato dell'oggetto. SQLMethodAttribute.IsMutator verrà applicato a questo metodo.  
  
 { **+=** | **-=** | **\*=** | **/=** | **%=** | **&=** | **^=** | **|=** }  
 Operatore di assegnazione composto:  
  
 + = Aggiunta e assegnazione  
  
 -= Sottrazione e assegnazione  
  
 * = Moltiplicazione e assegnazione  
  
 / = Divisione e assegnazione  
  
 % = Applicazione del coefficiente e assegnazione  
  
 &=              AND bit per bit e assegnazione  
  
 ^ = XOR bit per bit e assegnazione  
  
 | = OR bit per bit e assegnazione  
  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *cursor_variable*  
 Nome di una variabile di cursore. Se in precedenza la variabile di cursore di destinazione faceva riferimento a un cursore diverso, il riferimento precedente viene rimosso.  
  
 *cursor_name*  
 Nome di un cursore dichiarato tramite l'istruzione DECLARE CURSOR.  
  
 CURSOR  
 Specifica che l'istruzione SET contiene una dichiarazione di cursore.  
  
 SCROLL  
 Specifica che il cursore supporta tutte le opzioni di recupero, ovvero FIRST, LAST, NEXT, PRIOR, RELATIVE e ABSOLUTE. L'opzione SCROLL non può essere utilizzata quando viene specificata l'opzione FAST_FORWARD.  
  
 FORWARD_ONLY  
 Specifica che il cursore supporta solo l'opzione di recupero FETCH NEXT. È possibile recuperare il cursore solo in una direzione, ovvero dalla prima riga all'ultima. Se si specifica l'opzione FORWARD_ONLY senza la parola chiave STATIC, KEYSET o DYNAMIC, il cursore viene implementato come DYNAMIC. Se vengono omesse sia l'opzione FORWARD_ONLY che l'opzione SCROLL, per impostazione predefinita viene utilizzata l'opzione FORWARD_ONLY, a meno che non sia stata specificata la parola chiave STATIC, KEYSET o DYNAMIC. Per i cursori di tipo STATIC, KEYSET e DYNAMIC, l'opzione predefinita è SCROLL.  
  
 STATIC  
 Definisce un cursore che crea una copia temporanea dei dati utilizzati dal cursore. Le richieste inviate al cursore vengono soddisfatte tramite questa tabella temporanea di tempdb. Le modifiche apportate alle tabelle di base non vengono pertanto riportate nei dati restituiti dalle operazioni di recupero eseguite in questo cursore, che non supporta operazioni di modifica.  
  
 KEYSET  
 Specifica che all'apertura del cursore l'appartenenza e l'ordine delle righe nel cursore sono fissi. Il set di chiavi che identifica in modo univoco le righe viene compilato in keysettable in tempdb. Le modifiche di valori non chiave delle tabelle di base che sono state apportate dal proprietario del cursore o di cui è stato eseguito il commit da altri utenti sono visibili quando il proprietario scorre il cursore. Gli inserimenti eseguiti da altri utenti non sono visibili e non è possibile eseguire inserimenti tramite un cursore [!INCLUDE[tsql](../../includes/tsql-md.md)] del server.  
  
 Se viene eliminata una riga, un tentativo di recupero della riga restituisce un @@FETCH_STATUS -2. Le operazioni di aggiornamento di valori di chiave dall'esterno del cursore sono simili a un'operazione di eliminazione della riga precedente seguita da un'operazione di inserimento della nuova riga. La riga con i nuovi valori non è visibile e tenta di recuperare la riga con i vecchi valori restituisce un @@FETCH_STATUS -2. I nuovi valori sono visibili se l'aggiornamento viene eseguito tramite il cursore con l'aggiunta della clausola WHERE CURRENT OF.  
  
 DYNAMIC  
 Definisce un cursore che visualizza nel set di risultati tutte le modifiche apportate ai dati delle righe quando il proprietario scorre il cursore. I valori dei dati, l'ordine e l'appartenenza delle righe possono cambiare a ogni operazione di recupero. I cursori dinamici non supportano le opzioni di recupero assoluto e relativo.  
  
 FAST_FORWARD  
 Specifica un cursore FORWARD_ONLY e READ_ONLY con le ottimizzazioni abilitate. L'opzione FAST_FORWARD non può essere utilizzata quando viene specificata l'opzione SCROLL.  
  
 READ_ONLY  
 Impedisce l'esecuzione di aggiornamenti tramite il cursore. Non è possibile fare riferimento al cursore in una clausola WHERE CURRENT OF di un'istruzione UPDATE o DELETE. Questa opzione è prioritaria rispetto alla funzionalità di aggiornamento predefinita di un cursore.  
  
 SCROLL LOCKS  
 Specifica che gli aggiornamenti o le eliminazioni posizionate eseguite tramite il cursore avranno esito positivo. Durante la lettura nel cursore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] blocca le righe in modo che siano disponibili per modifiche successive. L'opzione SCROLL_LOCKS non può essere utilizzata quando viene specificata l'opzione FAST_FORWARD.  
  
 OPTIMISTIC  
 Specifica che gli aggiornamenti o le eliminazioni posizionate eseguite tramite il cursore non avranno esito positivo se la riga ha subito un aggiornamento dopo la lettura nel cursore. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non blocca le righe man mano che vengono lette nel cursore. Per determinare se la riga è stata modificata dopo la lettura nel cursore, vengono utilizzati confronti tra i valori della colonna di tipo timestamp oppure un valore di checksum se la tabella non include una colonna di tipo timestamp. Se la riga è stata modificata, i tentativi di eseguire un aggiornamento o un'eliminazione posizionata hanno esito negativo. L'opzione OPTIMISTIC non può essere utilizzata quando viene specificata l'opzione FAST_FORWARD.  
  
 TYPE_WARNING  
 Specifica che deve essere inviato un messaggio di avviso al client quando il cursore viene convertito in modo implicito dal tipo richiesto in un altro tipo.  
  
 PER *select_statement*  
 Istruzione SELECT standard che definisce il set di risultati del cursore. Le parole chiave FOR BROWSE e INTO non sono consentite all'interno di *select_statement* di una dichiarazione di cursore.  
  
 Se vengono utilizzati DISTINCT, UNION, GROUP BY o HAVING, o un'espressione di aggregazione è incluso nel *select_list*, il cursore verrà creato come STATIC.  
  
 Se nessuna tabella sottostante include un indice univoco e viene richiesto un cursore ISO SCROLL o un cursore KEYSET [!INCLUDE[tsql](../../includes/tsql-md.md)], il cursore sarà sempre di tipo STATIC.  
  
 Se *select_statement* contiene una clausola ORDER BY in cui le colonne non sono identificatori di riga univoco, un cursore dinamico viene convertito in un cursore KEYSET, o in un cursore statico se non è possibile aprire un cursore KEYSET. Questa conversione ha luogo anche per i cursori definiti con la sintassi ISO ma senza la parola chiave STATIC.  
  
 READ ONLY  
 Impedisce l'esecuzione di aggiornamenti tramite il cursore. Non è possibile fare riferimento al cursore in una clausola WHERE CURRENT OF di un'istruzione UPDATE o DELETE. Questa opzione è prioritaria rispetto alla funzionalità di aggiornamento predefinita di un cursore. Questa parola chiave si differenzia dalla parola chiave READ_ONLY descritta in precedenza in quanto tra READ e ONLY esiste uno spazio anziché un carattere di sottolineatura.  
  
 AGGIORNAMENTO [OF *column_name*[ **,**... *n* ] ]  
 Definisce le colonne aggiornabili nel cursore. Se viene specificato OF *column_name* [**,**...  *n* ] viene fornito, solo le colonne elencate è possibile apportare modifiche. Se non viene specificata alcuna colonna, è possibile aggiornare tutte le colonne, a meno che il cursore non sia stato definito come READ_ONLY.  
  
## <a name="remarks"></a>Osservazioni  
 Dopo la dichiarazione, le variabili vengono inizializzate sul valore NULL. Per assegnare un valore diverso da NULL a una variabile dichiarata, utilizzare l'istruzione SET. L'istruzione SET che assegna un valore alla variabile restituisce un solo valore. Per inizializzare più variabili, utilizzare un'istruzione SET separata per ogni variabile locale.  
  
 Le variabili possono essere utilizzate solo nelle espressioni e non in sostituzione di parole chiave o nomi di oggetto. Per creare istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] dinamiche, utilizzare EXECUTE.  
  
 Le regole di sintassi per SET  **@**  *cursor_variable* non includono le parole chiave LOCAL e GLOBAL. Quando il SET di  **@**  *cursor_variable* = CURSOR... viene utilizzata la sintassi, viene creato un cursore GLOBAL o LOCAL a seconda dell'impostazione del valore predefinito per l'opzione di database locale di cursore.  
  
 Le variabili di cursore sono sempre locali, anche quando fanno riferimento a un cursore globale. Quando una variabile di cursore fa riferimento a un cursore globale, esistono sia un riferimento al cursore locale che un riferimento al cursore globale. Per ulteriori informazioni, vedere l'esempio C.  
  
 Per ulteriori informazioni, vedere [DECLARE CURSOR &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-cursor-transact-sql.md).  
  
 L'operatore di assegnazione composto può essere utilizzato in tutti i casi in cui è presente un'assegnazione con un'espressione a destra dell'operatore, incluse variabili e un'istruzione SET in un'istruzione UPDATE, SELECT o RECEIVE.  
  
 Non utilizzare una variabile in un'istruzione SELECT per concatenare valori, ovvero per elaborare valori aggregati. Si potrebbero verificare risultati di query imprevisti. Ciò è dovuto al fatto che non è garantito che tutte le espressioni nell'elenco SELECT, incluse le assegnazioni, siano eseguite esattamente una volta per ciascuna riga di output. Per ulteriori informazioni, vedere [questo articolo della Knowledge Base](http://support.microsoft.com/kb/287515).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public. Tutti gli utenti possono utilizzare SET  **@**  *local_variable*.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-printing-the-value-of-a-variable-initialized-by-using-set"></a>A. Visualizzazione del valore di una variabile inizializzata tramite l'istruzione SET  
 Nell'esempio seguente viene creata la `@myvar` variabile, inserito un valore stringa nella variabile e stampato il valore della `@myvar` variabile.  
  
```  
DECLARE @myvar char(20);  
SET @myvar = 'This is a test';  
SELECT @myvar;  
GO  
```  
  
### <a name="b-using-a-local-variable-assigned-a-value-by-using-set-in-a-select-statement"></a>B. Utilizzo in un'istruzione SELECT di una variabile locale a cui viene assegnato un valore tramite l'istruzione SET  
 Nell'esempio seguente viene creata una variabile locale denominata `@state` che viene quindi utilizzata in un'istruzione `SELECT` per individuare i nomi e i cognomi di tutti i dipendenti che risiedono nello stato dell'`Oregon`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @state char(25);  
SET @state = N'Oregon';  
SELECT RTRIM(FirstName) + ' ' + RTRIM(LastName) AS Name, City  
FROM HumanResources.vEmployee  
WHERE StateProvinceName = @state;  
```  
  
### <a name="c-using-a-compound-assignment-for-a-local-variable"></a>C. Utilizzo di un'assegnazione composta per una variabile locale  
 I due esempi seguenti consentono di ottenere lo stesso risultato. Tramite gli esempi viene creata una variabile locale denominata `@NewBalance`, quindi la variabile viene moltiplicata per 10 e il nuovo valore della variabile locale viene visualizzato in un'istruzione `SELECT`. Nel secondo esempio viene utilizzato un operatore di assegnazione composto.  
  
```  
/* Example one */  
DECLARE  @NewBalance  int ;  
SET  @NewBalance  =  10;  
SET  @NewBalance  =  @NewBalance  *  10;  
SELECT  @NewBalance;  
  
/* Example Two */  
DECLARE @NewBalance int = 10;  
SET @NewBalance *= 10;  
SELECT @NewBalance;  
```  
  
### <a name="d-using-set-with-a-global-cursor"></a>D. Utilizzo dell'istruzione SET con un cursore globale  
 Nell'esempio seguente viene creata una variabile locale e quindi viene impostata la variabile di cursore sul nome del cursore globale.  
  
```  
DECLARE my_cursor CURSOR GLOBAL   
FOR SELECT * FROM Purchasing.ShipMethod  
DECLARE @my_variable CURSOR ;  
SET @my_variable = my_cursor ;   
--There is a GLOBAL cursor declared(my_cursor) and a LOCAL variable  
--(@my_variable) set to the my_cursor cursor.  
DEALLOCATE my_cursor;   
--There is now only a LOCAL variable reference  
--(@my_variable) to the my_cursor cursor.  
```  
  
### <a name="e-defining-a-cursor-by-using-set"></a>E. Definizione di un cursore tramite l'istruzione SET  
 Nell'esempio seguente viene utilizzata l'istruzione `SET` per definire un cursore.  
  
```  
DECLARE @CursorVar CURSOR;  
  
SET @CursorVar = CURSOR SCROLL DYNAMIC  
FOR  
SELECT LastName, FirstName  
FROM AdventureWorks2012.HumanResources.vEmployee  
WHERE LastName like 'B%';  
  
OPEN @CursorVar;  
  
FETCH NEXT FROM @CursorVar;  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    FETCH NEXT FROM @CursorVar  
END;  
  
CLOSE @CursorVar;  
DEALLOCATE @CursorVar;  
```  
  
### <a name="f-assigning-a-value-from-a-query"></a>F. Assegnazione di un valore tramite una query  
 Nell'esempio seguente viene utilizzata una query per assegnare un valore a una variabile.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @rows int;  
SET @rows = (SELECT COUNT(*) FROM Sales.Customer);  
SELECT @rows;  
```  
  
### <a name="g-assigning-a-value-to-a-user-defined-type-variable-by-modifying-a-property-of-the-type"></a>G. Assegnazione di un valore a una variabile con tipo definito dall'utente tramite la modifica di una proprietà del tipo  
 Nell'esempio seguente viene impostato un valore per il tipo definito dall'utente `Point` tramite la modifica del valore della proprietà `X` del tipo.  
  
```  
DECLARE @p Point;  
SET @p.X = @p.X + 1.1;  
SELECT @p;  
GO  
```  
  
### <a name="h-assigning-a-value-to-a-user-defined-type-variable-by-invoking-a-method-of-the-type"></a>H. Assegnazione di un valore a una variabile con tipo definito dall'utente tramite la chiamata di un metodo del tipo  
 Nell'esempio seguente imposta un valore per tipo definito dall'utente **punto** tramite la chiamata di metodo `SetXY` del tipo.  
  
```  
DECLARE @p Point;  
SET @p=point.SetXY(23.5, 23.5);  
```  
  
### <a name="i-creating-a-variable-for-a-clr-type-and-calling-a-mutator-method"></a>I. Creazione di una variabile per un tipo CLR e chiamata di un metodo mutatore  
 Nell'esempio seguente viene creata una variabile per il tipo `Point`, quindi viene eseguito un metodo mutatore in `Point`.  
  
```  
CREATE ASSEMBLY mytest from 'c:\test.dll' WITH PERMISSION_SET = SAFE  
CREATE TYPE Point EXTERNAL NAME mytest.Point  
GO  
DECLARE @p Point = CONVERT(Point, '')  
SET @p.SetXY(22, 23);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="j-printing-the-value-of-a-variable-initialized-by-using-set"></a>J. Visualizzazione del valore di una variabile inizializzata tramite l'istruzione SET  
 Nell'esempio seguente viene creata la `@myvar` variabile, inserito un valore stringa nella variabile e stampato il valore della `@myvar` variabile.  
  
```  
DECLARE @myvar char(20);  
SET @myvar = 'This is a test';  
SELECT top 1 @myvar FROM sys.databases;  
  
```  
  
### <a name="k-using-a-local-variable-assigned-a-value-by-using-set-in-a-select-statement"></a>K. Utilizzo in un'istruzione SELECT di una variabile locale a cui viene assegnato un valore tramite l'istruzione SET  
 L'esempio seguente crea una variabile locale denominata `@dept` e utilizza questa variabile locale in un `SELECT` istruzione per trovare i nomi e il cognome di tutti i dipendenti che lavorano nel `Marketing` reparto.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @dept char(25);  
SET @dept = N'Marketing';  
SELECT RTRIM(FirstName) + ' ' + RTRIM(LastName) AS Name  
FROM DimEmployee   
WHERE DepartmentName = @dept;  
```  
  
### <a name="l-using-a-compound-assignment-for-a-local-variable"></a>L. Utilizzo di un'assegnazione composta per una variabile locale  
 I due esempi seguenti consentono di ottenere lo stesso risultato. In questi esempi viene creata una variabile locale denominata `@NewBalance`, quindi la variabile viene moltiplicata per `10` e il nuovo valore della variabile locale viene visualizzato in un'istruzione `SELECT`. Nel secondo esempio viene utilizzato un operatore di assegnazione composto.  
  
```  
/* Example one */  
DECLARE  @NewBalance  int ;  
SET  @NewBalance  =  10;  
SET  @NewBalance  =  @NewBalance  *  10;  
SELECT  TOP 1 @NewBalance FROM sys.tables;  
  
/* Example Two */  
DECLARE @NewBalance int = 10;  
SET @NewBalance *= 10;  
SELECT TOP 1 @NewBalance FROM sys.tables;  
```  
  
### <a name="m-assigning-a-value-from-a-query"></a>M. Assegnazione di un valore tramite una query  
 Nell'esempio seguente viene utilizzata una query per assegnare un valore a una variabile.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @rows int;  
SET @rows = (SELECT COUNT(*) FROM dbo.DimCustomer);  
SELECT TOP 1 @rows FROM sys.tables;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

