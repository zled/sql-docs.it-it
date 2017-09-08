---
title: rowversion (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- timestamp_TSQL
- timestamp
dev_langs:
- TSQL
helpviewer_keywords:
- rowversion data type
- size [SQL Server], rowversion
- row version-stamping [SQL Server]
- rowversion columns
- version-stamping table rows
- unique rowversion numbers
- unique timestamp numbers
- timestamp data type
- timestamp columns
- size [SQL Server], timestamp
ms.assetid: 65c9cf0e-3e8a-45f8-87b3-3460d96afb0b
caps.latest.revision: 57
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 47bcf3007657c1cf8f77c364aa21839cdd27d1ba
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="rowversion-transact-sql"></a>rowversion (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Tipo di dati che espone numeri binari univoci generati automaticamente all'interno di un database. **rowversion** viene in genere utilizzato come meccanismo per indicare la versione delle righe di tabella. Le dimensioni di archiviazione sono di 8 byte. Il **rowversion** tipo di dati è un numero incrementale e non mantiene una data o ora. Per registrare una data o ora, utilizzare un **datetime2** tipo di dati.
  
## <a name="remarks"></a>Osservazioni  
Ogni database dispone di un contatore che viene incrementato per ogni operazione di inserimento o l'operazione di aggiornamento che viene eseguita su una tabella che contiene un **rowversion** colonna all'interno del database. Questo contatore è il valore rowversion relativo al database che tiene traccia del tempo relativo all'interno di un database e non del tempo effettivo che può essere associato a un orologio. Una tabella può avere un solo **rowversion** colonna. Ogni volta che una riga con un **rowversion** colonna viene modificata o inserita, il valore rowversion incrementato database verrà inserito nel **rowversion** colonna. Questa proprietà è un **rowversion** colonna non adatta per le chiavi, soprattutto per le chiavi primarie. Gli aggiornamenti eseguiti sulla riga modificano il valore rowversion, con la conseguente modifica del valore della chiave. Se la colonna è una chiave primaria, il valore di chiave precedente non è più valido, come non sono più valide le chiavi esterne che fanno riferimento al valore precedente. Se un cursore dinamico include riferimenti alla tabella, tutti gli aggiornamenti modificano la posizione delle righe all'interno del cursore. Se la colonna è una chiave indice, tutti gli aggiornamenti alle righe di dati comportano l'aggiornamento dell'indice.  Il **rowversion** viene incrementato il valore con qualsiasi istruzione update, anche se i valori di riga non vengono modificati. (Ad esempio, se un valore di colonna è 5 e un'istruzione update imposta il valore su 5, questa azione viene considerata un aggiornamento anche se è presente alcuna modifica e **rowversion** viene incrementato.)
  
**timestamp** è sinonimo di **rowversion** tipo di dati e presenta il comportamento dei dati di sinonimi dei tipi. Nelle istruzioni DDL, utilizzare **rowversion** anziché **timestamp** laddove possibile. Per ulteriori informazioni, vedere [sinonimi dei tipi di dati &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
Il [!INCLUDE[tsql](../../includes/tsql-md.md)] **timestamp** è diverso dal tipo di dati di **timestamp** tipo di dati definito nello standard ISO.
  
> [!NOTE]  
>  Il **timestamp** sintassi è deprecata. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
In un'istruzione CREATE TABLE o ALTER TABLE, non è necessario specificare un nome di colonna per il **timestamp** tipo di dati, ad esempio:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, timestamp);  
```  
  
Se non si specifica un nome di colonna, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] genera il **timestamp** nome di colonna, tuttavia, il **rowversion** sinonimo non rispetta questo comportamento. Quando si utilizza **rowversion**, è necessario specificare un nome di colonna, ad esempio:
  
```sql
CREATE TABLE ExampleTable2 (PriKey int PRIMARY KEY, VerCol rowversion) ;  
```  
  
> [!NOTE]  
>  Duplicare **rowversion** valori possono essere generati utilizzando l'istruzione SELECT INTO in cui un **rowversion** colonna è nell'elenco di selezione. Non è consigliabile utilizzare **rowversion** in questo modo.  
  
Un non ammettono valori null **rowversion** colonna è semanticamente equivalente a un **Binary (8)** colonna. Un valore nullable **rowversion** colonna è semanticamente equivalente a un **varbinary (8)** colonna.
  
È possibile utilizzare il **rowversion** colonna di una riga per stabilire facilmente se la riga si è verificata un'istruzione update è stata eseguita su di essa dall'ultima volta che è stato letto. Se è stato eseguito in un'istruzione update sulla riga, il valore rowversion viene aggiornato. Se è stato eseguito alcun aggiornamento istruzioni sono contro la riga, il valore rowversion è lo stesso di quando è stata precedentemente letta. Per restituire il valore rowversion corrente per un database, utilizzare [@@DBTS](../../t-sql/functions/dbts-transact-sql.md).
  
È possibile aggiungere un **rowversion** colonna a una tabella per mantenere l'integrità del database quando più utenti aggiornano le righe contemporaneamente. Potrebbe essere necessario, inoltre, conoscere le righe aggiornate e il relativo numero senza eseguire nuovamente una query nella tabella.
  
Si supponga ad esempio di avere creato una tabella denominata `MyTest` Popolare i dati nella tabella eseguendo le operazioni seguenti [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni.
  
```sql
CREATE TABLE MyTest (myKey int PRIMARY KEY  
    ,myValue int, RV rowversion);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (2, 0);  
GO  
```  
  
È possibile utilizzare le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] di esempio seguenti per implementare il controllo della concorrenza ottimistico nella tabella `MyTest` durante l'aggiornamento.
  
```sql
DECLARE @t TABLE (myKey int);  
UPDATE MyTest  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND RV = myValue;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
`myValue`è il **rowversion** il valore di colonna per la riga che indica l'ora dell'ultima di leggere la riga. Questo valore deve essere sostituito da effettivi **rowversion** valore. Un esempio di effettivi **rowversion** valore è 0x00000000000007D3.
  
È possibile inoltre inserire le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] di esempio in una transazione. Eseguendo una query sulla variabile `@t` nell'ambito della transazione, è possibile recuperare la colonna aggiornata `myKey` della tabella senza rieseguire una query sulla tabella `MyTes`.
  
Di seguito è riportato lo stesso esempio con il **timestamp** sintassi:
  
```sql
CREATE TABLE MyTest2 (myKey int PRIMARY KEY  
    ,myValue int, TS timestamp);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (2, 0);  
GO  
DECLARE @t TABLE (myKey int);  
UPDATE MyTest2  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND TS = myValue;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
## <a name="see-also"></a>Vedere anche
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)  
[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40; Transact-SQL &#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)
  
  

