---
title: "Funzionalit&#224; supportate per i moduli T-SQL compilati in modo nativo | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
caps.latest.revision: 44
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 44
---
# Funzionalit&#224; supportate per i moduli T-SQL compilati in modo nativo
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


  Questo argomento contiene un elenco delle superfici di attacco e delle funzionalità supportate di T-SQL nei moduli di T-SQL compilati in modo nativo, ad esempio stored procedure ([CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)), funzioni scalari definite dall'utente, funzioni inline con valori di tabella e trigger.  

 Per le funzionalità supportate relative alla definizione dei moduli nativi, vedere [Supported DDL for Natively Compiled T-SQL modules](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md)(DDL supportate per moduli T-SQL compilati in modo nativo).  

-   [Superficie di attacco delle query nei moduli nativi](#qsancsp)  

-   [Modifica dei dati](#dml)  

-   [Elementi del linguaggio per il controllo di flusso](#cof)  

-   [Operatori supportati](#so)  

-   [Funzioni integrate nei moduli compilati in modo nativo](#bfncsp)  

-   [Controllo](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#auditing)  

-   [Hint di tabella e per la query](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#tqh)  

-   [Limitazioni relative all'ordinamento](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#los)  

 Per informazioni complete sui costrutti non supportati e per informazioni su come sopperire ad alcune funzionalità non supportate nei moduli compilati in modo nativo, vedere [Migration Issues for Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md). Per altre informazioni su funzionalità non supportate, vedere [Costrutti Transact-SQL non supportati da OLTP in memoria](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  

##  <a name="a-nameqsancspa-query-surface-area-in-native-modules"></a><a name="qsancsp"></a> Superficie di attacco delle query nei moduli nativi  

Sono supportati i costrutti delle query indicati di seguito:  

Clausola SELECT:  

-   Alias di nomi e colonne (usando la sintassi AS o =).  

-   Sottoquery scalari  

-   TOP*  

-   SELECT DISTINCT  

              DISTINCT aggregates are not supported.  

-   UNION e UNION ALL

-   Assegnazioni di variabili  

Clausola FROM:  

-   FROM \<tabella o variabile di tabella ottimizzata per la memoria>  

-   FROM \<funzione con valori di tabella inline compilata in modo nativo>  

-   LEFT OUTER JOIN, RIGHT OUTER JOIN, CROSS JOIN e INNER JOIN.  

-   Sottoquery `[AS] table_alias`. Per altre informazioni, vedere [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  

Clausola WHERE:  

-   Predicato del filtro IS [NOT] NULL  

-   AND, OR, NOT, IN, EXISTS, BETWEEN  


Clausola[GROUP BY](../Topic/GROUP%20BY%20%28Transact-SQL%29.md) :

- Funzioni di aggregazione AVG, COUNT, COUNT_BIG, MIN, MAX e SUM.  

- MIN e MAX non sono supportate per i tipi nvarchar, char, varchar, varchar, varbinary e binary.  

Clausola[ORDER BY](../Topic/ORDER%20BY%20Clause%20%28Transact-SQL%29.md) :


- **DISTINCT** non è supportato nella clausola **ORDER BY** .


- Supportata con [GROUP BY &#40;Transact-SQL&#41;](../Topic/GROUP%20BY%20\(Transact-SQL\).md) se un'espressione nell'elenco ORDER BY appare in modo identico nell'elenco GROUP BY.
  - Ad esempio, l'espressione GROUP BY a + b ORDER BY a + b è supportata, ma GROUP BY a, b ORDER BY a + b non lo è.  


Clausola HAVING:

- Soggetta alle stesse limitazioni delle espressioni della clausola WHERE.


#### <a name="order-by-and-top-are-supported-in-natively-compiled-modules-with-some-restrictions"></a>ORDER BY e TOP sono supportati nei moduli compilati in modo nativo con alcune limitazioni


- **WITH TIES** o **PERCENT** non è supportata nella clausola **TOP** .


- **DISTINCT** non è supportato nella clausola **ORDER BY** .  


- **TOP** in combinazione con **ORDER BY** non supporta un valore superiore a 8.192 quando si utilizza una costante nella clausola **TOP** .
  - Questo limite può risultare più basso nel caso in cui la query contenga funzioni di aggregazione o dei join. Ad esempio, con un join (due tabelle) il limite scende a 4.096 righe. Con due join (tre tabelle) il limite è 2.730 righe.  
  - È possibile che si ottengano risultati maggiori di 8.192 archiviando il numero di righe in una variabile:  

```tsql
DECLARE @v INT = 9000;
SELECT TOP (@v) … FROM … ORDER BY …
```

Tuttavia, una costante nella clausola **TOP** assicura prestazioni migliori rispetto a una variabile.  

Queste limitazioni di [!INCLUDE[tsql](../../includes/tsql-md.md)] non si applicano all'accesso [!INCLUDE[tsql](../../includes/tsql-md.md)] interpretato nelle tabelle con ottimizzazione per la memoria.  


##  <a name="a-namedmla-data-modification"></a><a name="dml"></a> Modifica dei dati  

Sono supportate le istruzioni DML seguenti.  

-   INSERT VALUES (una riga per istruzione) e INSERT ... SELECT  

-   UPDATE  

-   DELETE  

-   La clausola WHERE è supportata con le istruzioni UPDATE e DELETE.  

##  <a name="a-namecofa-control-of-flow-language"></a><a name="cof"></a> Elementi del linguaggio per il controllo di flusso  
 Sono supportati i seguenti costrutti degli elementi del linguaggio per il controllo di flusso.  

-   [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)  

-   [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  

-   [RETURN &#40;Transact-SQL&#41;](../../t-sql/language-elements/return-transact-sql.md)  

-   [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md) può usare tutti i [tipi di dati supportati per OLTP in memoria](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md), nonché i tipi di tabella con ottimizzazione per la memoria. Le variabili possono essere dichiarate NULL o NOT NULL.  

-   [SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  

-   [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)  

               To achieve optimal performance, use a single TRY/CATCH block for an entire natively compiled T-SQL module.  

-   [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)  

-   BEGIN ATOMIC (al livello esterno della stored procedure). Per altri dettagli, vedere [Atomic Blocks](../../relational-databases/in-memory-oltp/blocchi-atomici-nelle-procedure-native.md).  

##  <a name="a-namesoa-supported-operators"></a><a name="so"></a> Operatori supportati  
 Di seguito vengono elencati gli operatori supportati.  

-   [Operatori di confronto &#40;Transact-SQL&#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md) (ad esempio >, \<, >= e <=)  

-   Operatori unari (+, -).  

-   Operatori binari (*, /, +, -, % (modulo)).  

               The plus operator (+) is supported on both numbers and strings.  

-   Operatori logici (AND, OR, NOT).  

-   Operatori bit per bit ~, &, | e ^  

-   APPLY - operatore
    - **Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, l'operatore APPLY è supportato nei moduli compilati in modo nativo.

##  <a name="a-namebfncspa-built-in-functions-in-natively-compiled-modules"></a><a name="bfncsp"></a> Funzioni integrate nei moduli compilati in modo nativo  
 Le seguenti funzioni sono supportate nei vincoli nelle tabelle con ottimizzazione per la memoria e nei moduli T-SQL compilati in modo nativo.  

-   Tutte le [funzioni matematiche &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  

-   Funzioni di data: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME e YEAR.  

-   Funzioni stringa: LEN, LTRIM, RTRIM e SUBSTRING.  
    - **Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, sono supportate anche le funzioni integrate seguenti: TRIM, TRANSLATE e CONCAT_WS.  

-   Funzione di identità: SCOPE_IDENTITY  

-   Funzioni NULL: ISNULL  

-   Funzioni di identificazione univoca: NEWID e NEWSEQUENTIALID  

-   Funzioni JSON  
    - **Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, le funzioni JSON sono supportate nei moduli compilati in modo nativo.

-   Funzioni di errore: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY e ERROR_STATE  

-   Funzioni di sistema: @@rowcount. Le istruzioni all'interno di stored procedure compilate in modo nativo aggiornano @@rowcount ed è possibile usare @@rowcount in una stored procedure compilata in modo nativo per determinare il numero di righe interessate dall'ultima istruzione eseguita all'interno di tale stored procedure. Tuttavia, @@rowcount viene reimpostato su 0 all'inizio e alla fine dell'esecuzione di una stored procedure compilata in modo nativo.  

-   Funzioni di sicurezza: IS_MEMBER({'group' | 'role'}), IS_ROLEMEMBER ('role' [, 'database_principal']), IS_SRVROLEMEMBER ('role' [, 'login']), ORIGINAL_LOGIN(), SESSION_USER, CURRENT_USER, SUSER_ID(['login']), SUSER_SID(['login'] [, Param2]), SUSER_SNAME([server_user_sid]), SYSTEM_USER, SUSER_NAME, USER, USER_ID(['user']), USER_NAME([id]), CONTEXT_INFO().

-   Le esecuzioni dei moduli nativi possono essere annidate.

##  <a name="a-nameauditinga-auditing"></a><a name="auditing"></a> Controllo  
 Il controllo a livello di routine è supportato nelle stored procedure compilate in modo nativo.  

 Per ulteriori informazioni sul controllo, vedere [Create a Server Audit and Database Audit Specification](../../relational-databases/security/auditing/create-a-server-audit-and-database-audit-specification.md).  

##  <a name="a-nametqha-table-and-query-hints"></a><a name="tqh"></a> Hint di tabella e per la query  
 Sono supportati gli elementi seguenti:  

-   Gli hint INDEX, FORCESCAN e FORCESEEK, nella sintassi di hint di tabella o nella [clausola OPTION &#40;Transact-SQL&#41;](../../t-sql/queries/option-clause-transact-sql.md) della query. Per altre informazioni, vedere [Hint di tabella &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md).  

-   FORCE ORDER  

-   Hint LOOP JOIN  

-   OPTIMIZE FOR  

 Per altre informazioni, vedere [Hint per la query &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md).  

##  <a name="a-namelosa-limitations-on-sorting"></a><a name="los"></a> Limitazioni relative all'ordinamento  
 È possibile ordinare più di 8.000 righe in una query che usa [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) e una clausola [ORDER BY Clause &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md). Tuttavia, senza la [ clausola ORDER BY &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md), [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) può ordinare fino a 8.000 righe, meno se sono presenti join.  

 Se la query usa sia l'operatore [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) che una [clausola ORDER BY &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md), è possibile specificare fino a 8192 righe per l'operatore TOP. Se si specificano più di 8192 righe viene visualizzato il messaggio di errore **Messaggio 41398, livello 16, stato 1, procedura *<nomeProcedura>\>*, riga *<numeroRiga>\>*. L'operatore TOP può restituire un massimo di 8192 righe. *\<numero>***.  

 Se non si dispone di una clausola TOP, è possibile ordinare qualsiasi numero di righe con ORDER BY.  

 Se non si utilizza una clausola ORDER BY, è possibile utilizzare qualsiasi valore intero con l'operatore TOP.  

 Esempio con TOP N = 8192: compila  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 Esempio con TOP N > 8192: non riesce a compilare.  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 Il limite di 8192 righe si applica solo a `TOP N``N` dove  è una costante, come negli esempi precedenti.  Se è necessario un valore `N` maggiore di 8192 è possibile assegnare il valore a una variabile e utilizzare tale variabile con `TOP`.  

 Esempio di utilizzo di una variabile: compila  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 **Limitazioni per le righe restituite.** In due casi è possibile che il numero di righe che possono essere restituite dall'operatore TOP venga ridotto:  

-   Utilizzando JOIN nella query.  L'influenza di JOIN sulla limitazione dipende dal piano di query.  

-   Utilizzando funzioni di aggregazione o riferimenti a funzioni di aggregazione nella clausola ORDER BY.  

 La formula per calcolare un valore N massimo supportato nel caso peggiore in TOP N è: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  

## <a name="see-also"></a>Vedere anche  
 [Stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)   
 [Problemi di migrazione relativi alle stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  

