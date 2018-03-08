---
title: SEQUENZA di ALTER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SEQUENCE_TSQL
- ALTER SEQUENCE
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, altering
- ALTER SEQUENCE statement
ms.assetid: decc0760-029e-4baf-96c9-4a64073df1c2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 66960ed0ae27cb7ecbe2d39d0e30d1ec12dcc3cb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-sequence-transact-sql"></a>ALTER SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Modifica gli argomenti di un oggetto sequenza esistente. Se la sequenza è stata creata con la **CACHE** opzione, la sequenza di modifica implica la ricreazione della cache.  
  
 Gli oggetti sequenza vengono creati utilizzando il [CREATE SEQUENCE](../../t-sql/statements/create-sequence-transact-sql.md) istruzione. Le sequenze sono valori interi e possono essere di qualsiasi tipo di dati in grado di restituire un intero. Non è possibile modificare il tipo di dati tramite l'istruzione ALTER SEQUENCE. Per modificare il tipo di dati, eliminare e ricreare l'oggetto sequenza.  
  
 Una sequenza è un oggetto associato a schema definito dall'utente che genera una sequenza di valori numerici in base a una specifica. Si generano nuovi valori da una sequenza chiamando la funzione NEXT VALUE FOR. Usare **sp_sequence_get_range** per ottenere immediatamente più numeri di sequenza. Per informazioni e scenari che utilizzano entrambi CREATE SEQUENCE, **sp_sequence_get_range**e la funzione NEXT VALUE FOR, vedere [numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER SEQUENCE [schema_name. ] sequence_name  
    [ RESTART [ WITH <constant> ] ]  
    [ INCREMENT BY <constant> ]  
    [ { MINVALUE <constant> } | { NO MINVALUE } ]  
    [ { MAXVALUE <constant> } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ <constant> ] } | { NO CACHE } ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *sequence_name*  
 Specifica il nome univoco con il quale è nota la sequenza nel database. Il tipo è **sysname**.  
  
 RIAVVIARE [WITH \<costante >]  
 Valore successivo che verrà restituito dall'oggetto sequenza. Se specificato, il valore RESTART WITH deve essere un numero intero minore o uguale al valore massimo e maggiore o uguale al valore minimo dell'oggetto sequenza. Se il valore WITH viene omesso, la numerazione della sequenza ricomincia in base alle opzioni CREATE SEQUENCE originali.  
  
 INCREMENT BY \<costante >  
 Valore utilizzato per incrementare (o diminuire, in caso di valore negativo) il valore di base dell'oggetto sequenza per ogni chiamata alla funzione NEXT VALUE FOR. Se l'incremento è un valore negativo, l'oggetto sequenza ha un ordine decrescente, in caso contrario avrà un ordine crescente. L'incremento non può essere 0.  
  
 [MINVALUE \<costante > | NESSUN MINVALUE]  
 Specifica i limiti per l'oggetto sequenza. Se viene specificato NO MINVALUE, viene utilizzato il valore possibile minimo del tipo di dati della sequenza.  
  
 [MAXVALUE \<costante > | NESSUN MAXVALUE  
 Specifica i limiti per l'oggetto sequenza. Se viene specificato NO MAXVALUE, viene utilizzato il valore possibile massimo del tipo di dati della sequenza.  
  
 [ CYCLE | NO CYCLE ]  
 Questa proprietà specifica se l'oggetto sequenza deve riprendere dal valore minimo (o massimo per gli oggetti sequenza con ordine decrescente) o generare un'eccezione quando viene superato il valore massimo o minimo.  
  
> [!NOTE]  
>  Dopo la ripresa del ciclo, il valore successivo sarà il valore minimo o massimo, non il valore START VALUE della sequenza.  
  
 [CACHE [\<costante >] | NO CACHE]  
 Migliora le prestazioni delle applicazioni che utilizzano gli oggetti sequenza riducendo il numero di I/O necessari per rendere persistenti i valori generati nelle tabelle di sistema.  
  
 Per ulteriori informazioni sul comportamento della cache, vedere [CREATE SEQUENCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-sequence-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 Per informazioni sulla creazione delle sequenze e come viene gestita la cache della sequenza di, vedere [CREATE SEQUENCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-sequence-transact-sql.md).  
  
 Non è possibile modificare MINVALUE per le sequenze con ordine crescente e MAXVALUE per le sequenze con ordine decrescente in un valore che non consente il valore START WITH della sequenza. Per modificare MINVALUE per una sequenza con ordine crescente in un numero maggiore del valore START WITH o per modificare MAXVALUE di una sequenza con ordine decrescente in un numero più piccolo del valore START WITH, includere l'argomento RESTART WITH per riprendere la sequenza in un punto desiderato compreso nell'intervallo minimo e massimo.  
  
## <a name="metadata"></a>Metadati  
 Per informazioni sulle sequenze, eseguire una query su [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md).  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
 Richiede **ALTER** l'autorizzazione per la sequenza o **ALTER** autorizzazione per lo schema. Per concedere **ALTER** l'autorizzazione per la sequenza, utilizzare **ALTER ON OBJECT** nel formato seguente:  
  
```  
GRANT ALTER ON OBJECT::Test.TinySeq TO [AdventureWorks\Larry]  
```  
  
 La proprietà di un oggetto sequenza può essere trasferita tramite il **ALTER AUTHORIZATION** istruzione.  
  
### <a name="audit"></a>Controllo  
 Per controllare **ALTER SEQUENCE**, monitoraggio di **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Esempi  
 Per esempi di creazione di sequenze e utilizzando il **NEXT VALUE FOR** funzione per generare numeri di sequenza, vedere [numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
### <a name="a-altering-a-sequence"></a>A. Alterazione di una sequenza  
 Nell'esempio seguente viene creato uno schema denominato Test e una sequenza denominata TestSeq utilizzando il **int** tipo di dati, con un intervallo compreso tra 0 e 255. La sequenza inizia con 125 e aumenta di 25 ogni volta che viene generato un numero. Poiché la sequenza è configurata per la ripresa del ciclo quando il valore supera il valore massimo di 200, la sequenza riprende dal valore minimo di 100.  
  
```  
CREATE SCHEMA Test ;  
GO  
  
CREATE SEQUENCE Test.TestSeq  
    AS int   
    START WITH 125  
    INCREMENT BY 25  
    MINVALUE 100  
    MAXVALUE 200  
    CYCLE  
    CACHE 3  
;  
GO  
```  
  
 L'esempio seguente modifica la sequenza TestSeq per avere un intervallo compreso tra 0 e 255. La sequenza riavvia la serie di numerazione con 100 e aumenta di 50 ogni volta che viene generato un numero.  
  
```  
ALTER SEQUENCE Test. TestSeq  
    RESTART WITH 100  
    INCREMENT BY 50  
    MINVALUE 50  
    MAXVALUE 200  
    NO CYCLE  
    NO CACHE  
;  
GO  
```  
  
 Poiché la sequenza non viene ripresa, il **NEXT VALUE FOR** funzione genereranno un errore durante la sequenza supera 200.  
  
### <a name="b-restarting-a-sequence"></a>B. Riavvio di una sequenza  
 Nell'esempio seguente viene creata una sequenza denominata CountBy1. La sequenza utilizza i valori predefiniti.  
  
```  
CREATE SEQUENCE Test.CountBy1 ;  
```  
  
 Per generare un valore di sequenza, il proprietario esegue l'istruzione seguente:  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1  
```  
  
 Il valore restituito-9.223.372.036.854.775.808 è il valore minimo per il **bigint** tipo di dati. Il proprietario è consapevole del fatto che la sequenza inizi con 1, ma non indica la **START WITH** clausola quando ha creato la sequenza. Per risolvere l'errore, il proprietario esegue l'istruzione seguente.  
  
```  
ALTER SEQUENCE Test.CountBy1 RESTART WITH 1 ;  
```  
  
 Il proprietario riesegue quindi l'istruzione seguente per generare un numero di sequenza.  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1;  
```  
  
 Il numero è ora 1, come previsto.  
  
 La sequenza CountBy1 è stata creata utilizzando il valore predefinito di NO CYCLE, pertanto arresterà dopo avere generato il numero 9.223.372.036.854.775.807. Le chiamate successive all'oggetto sequenza restituiranno l'errore 11728. Nell'istruzione seguente viene modificato l'oggetto sequenza in modo che venga ripreso il ciclo e viene impostata una cache di 20.  
  
```  
ALTER SEQUENCE Test.CountBy1  
    CYCLE  
    CACHE 20 ;  
  
```  
  
 Quando l'oggetto sequenza raggiunge 9.223.372.036.854.775.807 il ciclo viene ripreso e il numero successivo dopo la ripresa del ciclo sarà il minimo del tipo di dati, ovvero -9.223.372.036.854.775.808.  
  
 Il proprietario si rende conto che la **bigint** tipo di dati utilizza 8 byte ogni volta che viene utilizzato. Il **int** tipo di dati che utilizza 4 byte è sufficiente. Non è tuttavia possibile modificare il tipo di dati di un oggetto sequenza. Per modificare un **int** del tipo di dati, il proprietario deve eliminare l'oggetto sequenza e ricreare l'oggetto con tipo di dati corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [VALORE successivo per &#40; Transact-SQL &#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md)   
 [sp_sequence_get_range &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md)  
  
  
