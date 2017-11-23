---
title: CREARE una sequenza (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SEQUENCE
- CREATE SEQUENCE
- SEQUENCE_TSQL
- CREATE_SEQUENCE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- CREATE SEQUENCE statement
- sequence number object, creating
- sequence object
- number, sequence
ms.assetid: 419f907b-8a72-4d6c-80cb-301df44c24c1
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: ab2f4258d60f1653a102f5f9cc51d4263fcafc93
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-sequence-transact-sql"></a>CREATE SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Crea un oggetto sequenza e ne specifica le proprietà. Una sequenza è un oggetto associato a schema definito dall'utente che genera una sequenza di valori numerici in base alla specifica con la quale è stata creata la sequenza. La sequenza di valori numerici viene generata in ordine crescente o decrescente a un intervallo definito e può essere configurata per riprendere dall'inizio (ciclo) quando è esaurita. Le sequenze, a differenza delle colonne Identity, non sono associate a tabelle specifiche. Le applicazioni fanno riferimento a un oggetto sequenza per recuperare il relativo valore successivo. La relazione tra sequenze e tabelle è controllata dall'applicazione. Le applicazioni utente possono fare riferimento a un oggetto sequenza e coordinare i valori di più righe e tabelle.  
  
 A differenza dei valori di colonne di identità che vengono generati quando si inseriscono righe, un'applicazione può ottenere il numero di sequenza successivo senza inserire la riga chiamando la [funzione NEXT VALUE FOR](../../t-sql/functions/next-value-for-transact-sql.md). Usare [sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md) per ottenere immediatamente più numeri di sequenza.  
  
 Per informazioni e scenari in cui vengono usate entrambe le funzioni **CREATE SEQUENCE** e **NEXT VALUE FOR** , vedere [Numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE SEQUENCE [schema_name . ] sequence_name  
    [ AS [ built_in_integer_type | user-defined_integer_type ] ]  
    [ START WITH <constant> ]  
    [ INCREMENT BY <constant> ]  
    [ { MINVALUE [ <constant> ] } | { NO MINVALUE } ]  
    [ { MAXVALUE [ <constant> ] } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ <constant> ] } | { NO CACHE } ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *sequence_name*  
 Specifica il nome univoco con il quale è nota la sequenza nel database. Il tipo è **sysname**.  
  
 [ built_in_integer_type | user-defined_integer_type  
 Una sequenza può essere definita come qualsiasi tipo Integer. I tipi seguenti sono consentiti.  
  
-   **tinyint** -intervallo da 0 a 255  
  
-   **smallint** -intervallo tra -32.768 e 32.767  
  
-   **int** -intervallo tra -2.147.483.648 a 2.147.483.647  
  
-   **bigint** -intervallo -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807  
  
-   **decimale** e **numerico** con una scala pari a 0.  
  
-   Qualsiasi tipo di dati definito dall'utente (tipo di alias) basato su uno dei tipi consentiti.  
  
 Se non viene specificato alcun tipo di dati, il **bigint** tipo di dati viene utilizzato come impostazione predefinita.  
  
 START WITH \<costante >  
 Primo valore restituito dall'oggetto sequenza. Il **avviare** valore deve essere un valore minore o uguale al valore massimo e maggiore o uguale al valore minimo dell'oggetto sequenza. Il valore iniziale predefinito per un nuovo oggetto sequenza è il valore minimo per un oggetto sequenza con ordine crescente e il valore massimo per un oggetto sequenza con ordine decrescente.  
  
 INCREMENT BY \<costante >  
 Valore utilizzato per incrementare (o diminuire se negativo) il valore dell'oggetto sequenza per ogni chiamata al **NEXT VALUE FOR** (funzione). Se l'incremento è un valore negativo, l'oggetto sequenza presenta un ordine decrescente. In caso contrario, l'ordine sarà crescente. L'incremento non può essere 0. L'incremento predefinito per un nuovo oggetto sequenza è 1.  
  
 [MINVALUE \<costante > | **Alcun valore MINVALUE** ]  
 Specifica i limiti per l'oggetto sequenza. Il valore minimo predefinito per un nuovo oggetto sequenza è il valore minimo del tipo di dati dell'oggetto sequenza. Tale valore è zero per il tipo di dati **tinyint** e un numero negativo per tutti gli altri tipi di dati.  
  
 [MAXVALUE \<costante > | **Alcun valore MAXVALUE**  
 Specifica i limiti per l'oggetto sequenza. Il valore massimo predefinito per un nuovo oggetto sequenza è il valore massimo del tipo di dati dell'oggetto sequenza.  
  
 [CICLO | **NO CYCLE** ]  
 Proprietà che specifica se l'oggetto sequenza deve riprendere dal valore minimo (o massimo per gli oggetti sequenza con ordine decrescente) o generare un'eccezione quando viene superato il relativo valore massimo o minimo. L'opzione predefinita che determina la ripresa dei nuovi oggetti sequenza è NO CYCLE.  
  
 Si noti che la sequenza riprende dal valore minimo o massimo, non dal valore iniziale.  
  
 [ **CACHE** [\<costante >] | NO CACHE]  
 Migliora le prestazioni per le applicazioni che utilizzano oggetti sequenza riducendo il numero di I/O del disco necessari per generare numeri di sequenza. Il valore predefinito è CACHE.  
  
 Ad esempio, se si sceglie una dimensione della cache pari a 50, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non mantiene memorizzati 50 singoli valori. ma solo il valore corrente e il numero di valori rimanenti nella cache. La quantità di memoria necessaria per l'archiviazione della cache è pertanto sempre corrispondente a due istanze del tipo di dati dell'oggetto sequenza.  
  
> [!NOTE]  
>  Se l'opzione cache viene abilitata senza specificare la dimensione, quest'ultima verrà selezionata dal Motore di database. È tuttavia consigliabile non basarsi sul fatto che la selezione sia coerente. [!INCLUDE[msCoName](../../includes/msconame-md.md)] potrebbe cambiare il metodo di calcolo della dimensione della cache senza preavviso.  
  
 Creazione con il **CACHE** opzione, un arresto imprevisto (ad esempio un'interruzione dell'alimentazione) potrebbe causare la perdita dei numeri di sequenza rimanenti nella cache.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 I numeri di sequenza vengono generati esternamente all'ambito della transazione corrente. Vengono utilizzati sia in caso di commit che di rollback della transazione che utilizza il numero di sequenza.  
  
### <a name="cache-management"></a>Gestione della cache  
 Per migliorare le prestazioni, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] preallocata il numero dei numeri di sequenza specificati per il **CACHE** argomento.  
  
 Si supponga, ad esempio, che una nuova sequenza venga creata con un valore iniziale pari a 1 e una dimensione della cache pari a 15. Quando viene richiesto il primo valore, i valori compresi tra 1 e 15 vengono resi disponibili dalla memoria. L'ultimo valore memorizzato nella cache (15) viene scritto nelle tabelle di sistema sul disco. Dopo che tutti e 15 i numeri sono stati utilizzati, la richiesta successiva (del numero 16) comporterà la riallocazione della cache. Il nuovo ultimo valore memorizzato nella cache (30) verrà scritto nelle tabelle di sistema.  
  
 Se il [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene arrestato dopo che sono stati utilizzati 22 numeri, il numero di sequenza desiderato successivo in memoria (23) viene scritto nelle tabelle di sistema, andando a sostituire il numero archiviato in precedenza.  
  
 Quando SQL Server viene riavviato e viene richiesto un numero di sequenza, il numero iniziale viene letto dalle tabelle di sistema (23). La quantità della cache di 15 numeri (23-38) viene allocata nella memoria e il numero non memorizzato nella cache successivo (39) viene scritto nelle tabelle di sistema.  
  
 Se il [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene arrestato in modo anomalo per un evento, ad esempio un'interruzione dell'alimentazione, la sequenza viene riavviata con il numero letto dalle tabelle di sistema (39). Qualsiasi sequenza di numeri allocati memoria (ma mai richiesto da un utente o applicazione) vengono persi. Questa funzionalità potrebbe lasciare dei vuoti, ma garantisce che lo stesso valore non venga mai generato due volte per un singolo oggetto sequenza a meno che non è definito come **ciclo** o venga riavviato manualmente.  
  
 La cache viene mantenuta nella memoria tenendo traccia del valore corrente (l'ultimo valore generato) e del numero di valori rimanenti nella cache. Pertanto, la quantità di memoria utilizzata dalla cache è sempre corrispondente a due istanze del tipo di dati dell'oggetto sequenza.  
  
 L'impostazione dell'argomento della cache su **NO CACHE** scrive il valore di sequenza corrente per le tabelle di sistema ogni volta che viene utilizzata una sequenza. Le prestazioni potrebbero diminuire in seguito all'aumento dell'accesso al disco, tuttavia diminuiscono anche le probabilità di vuoti indesiderati. Spazi vuoti possono comunque verificarsi se i numeri vengono richiesti utilizzando il **NEXT VALUE FOR** o **sp_sequence_get_range** funzioni, ma i numeri non vengono utilizzati o vengono utilizzati nelle transazioni.  
  
 Quando un oggetto sequenza viene utilizzato il **CACHE** opzione, se si riavvia l'oggetto sequenza o si modifica il **incremento**, **ciclo**, **MINVALUE**, **MAXVALUE**, o le proprietà di dimensioni della cache, verrà generata la cache in cui scrivere le tabelle di sistema prima che si verifichi la modifica. La cache verrà quindi ricaricata a partire dal valore corrente (non viene ignorato alcun numero). La modifica della dimensione della cache diventa effettiva immediatamente.  
  
 **Opzione CACHE quando sono disponibili valori memorizzati nella cache**  
  
 Il processo seguente si verifica ogni volta che viene richiesto un oggetto di sequenza per generare il valore successivo per il **CACHE** opzione se sono disponibili valori inutilizzati nella cache in memoria per l'oggetto sequenza.  
  
1.  Viene calcolato il valore successivo per l'oggetto sequenza.  
  
2.  Viene aggiornato in memoria il nuovo valore corrente per l'oggetto sequenza.  
  
3.  Il valore calcolato viene restituito all'istruzione di chiamata.  
  
 **Opzione CACHE quando la cache è esaurita**  
  
 Il processo seguente si verifica ogni volta che viene richiesto un oggetto di sequenza per generare il valore successivo per il **CACHE** opzione se la cache è stata esaurita:  
  
1.  Viene calcolato il valore successivo per l'oggetto sequenza.  
  
2.  Viene calcolato l'ultimo valore per la nuova cache.  
  
3.  Viene bloccata la riga della tabella di sistema per l'oggetto sequenza e il valore calcolato nel passaggio 2 (l'ultimo valore) viene scritto nella tabella di sistema. Viene generato un Xevent di cache esaurita per notificare all'utente il nuovo valore persistente.  
  
 **Opzione NO CACHE**  
  
 Il processo seguente si verifica ogni volta che viene richiesto un oggetto di sequenza per generare il valore successivo per il **NO CACHE** opzione:  
  
1.  Viene calcolato il valore successivo per l'oggetto sequenza.  
  
2.  Il nuovo valore corrente per l'oggetto sequenza viene scritto nella tabella di sistema.  
  
3.  Il valore calcolato viene restituito all'istruzione di chiamata.  
  
## <a name="metadata"></a>Metadati  
 Per informazioni sulle sequenze, eseguire una query su [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md).  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione **CREATE SEQUENCE**, **ALTER**o **CONTROL** per l'oggetto SCHEMA.  
  
-   I membri dei ruoli predefiniti del database db_ddladmin e db_owner possono creare, modificare ed eliminare gli oggetti sequenza.  
  
-   I membri di db_owner e db_datawriter ruoli predefiniti del database è possono aggiornare gli oggetti sequenza comportando generare numeri.  
  
 Nell'esempio seguente viene concessa l'autorizzazione AdventureWorks\Larry per creare sequenze nello schema di Test.  
  
```  
GRANT CREATE SEQUENCE ON SCHEMA::Test TO [AdventureWorks\Larry]  
```  
  
 Proprietà di un oggetto sequenza può essere trasferita tramite il **ALTER AUTHORIZATION** istruzione.  
  
 Se una sequenza utilizza un tipo di dati definito dall'utente, l'autore della sequenza deve disporre dell'autorizzazione REFERENCES per il tipo.  
  
### <a name="audit"></a>Controllo  
 Per controllare **CREATE SEQUENCE**, monitoraggio di **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Esempi  
 Per esempi di sequenze di creazione e utilizzo di **NEXT VALUE FOR** funzione per generare numeri di sequenza, vedere [numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 La maggior parte degli esempi seguenti creare gli oggetti sequenza in uno schema denominato Test.  
  
 Per creare lo schema del Test, eseguire l'istruzione seguente.  
  
```  
CREATE SCHEMA Test ;  
GO  
```  
  
### <a name="a-creating-a-sequence-that-increases-by-1"></a>A. Creazione di una sequenza che aumenta di 1  
 Nell'esempio seguente Thierry crea una sequenza denominata CountBy1 che aumenta di uno ogni volta che viene utilizzata.  
  
```  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="b-creating-a-sequence-that-decreases-by-1"></a>B. Creazione di una sequenza che diminuisce di 1  
 Nell'esempio seguente la sequenza inizia da 0 e aumenta di un numero negativo ogni volta che viene utilizzata.  
  
```  
CREATE SEQUENCE Test.CountByNeg1  
    START WITH 0  
    INCREMENT BY -1 ;  
GO  
```  
  
### <a name="c-creating-a-sequence-that-increases-by-5"></a>C. Creazione di una sequenza che aumenta di 5  
 Nell'esempio seguente viene creata una sequenza che aumenta di 5 ogni volta che viene utilizzata.  
  
```  
CREATE SEQUENCE Test.CountBy1  
    START WITH 5  
    INCREMENT BY 5 ;  
GO  
```  
  
### <a name="d-creating-a-sequence-that-starts-with-a-designated-number"></a>D. Creazione di una sequenza che inizia con un numero definito  
 Dopo avere importato una tabella, Thierry nota che il numero ID più elevato utilizzato è 24.328. Thierry necessita di una sequenza che genererà numeri che iniziano da 24.329. Nel codice seguente viene creata una sequenza che inizia da 24.329 e aumenta di 1.  
  
```  
CREATE SEQUENCE Test.ID_Seq  
    START WITH 24329  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="e-creating-a-sequence-using-default-values"></a>E. Creazione di una sequenza utilizzando valori predefiniti  
 Nell'esempio seguente viene creata una sequenza utilizzando i valori predefiniti.  
  
```  
CREATE SEQUENCE Test.TestSequence ;  
```  
  
 Eseguire l'istruzione seguente per visualizzare le proprietà della sequenza.  
  
```  
SELECT * FROM sys.sequences WHERE name = 'TestSequence' ;  
```  
  
 Un elenco parziale dell'output dimostra i valori predefiniti.  
  
|||  
|-|-|  
|`start_value`|`-9223372036854775808`|  
|`increment`|`1`|  
|`mimimum_value`|`-9223372036854775808`|  
|`maximum_value`|`9223372036854775807`|  
|`is_cycling`|`0`|  
|`is_cached`|`1`|  
|`current_value`|`-9223372036854775808`|  
  
### <a name="f-creating-a-sequence-with-a-specific-data-type"></a>F. Creazione di una sequenza con un tipo di dati specifico  
 Nell'esempio seguente viene creata una sequenza utilizzando il **smallint** il tipo di dati, con un intervallo compreso tra -32.768 e 32.767.  
  
```  
CREATE SEQUENCE SmallSeq  
    AS smallint ;  
```  
  
### <a name="g-creating-a-sequence-using-all-arguments"></a>G. Creazione di una sequenza utilizzando tutti gli argomenti  
 Nell'esempio seguente viene creata una sequenza denominata DecSeq utilizzando il **decimale** tipo di dati, con un intervallo compreso tra 0 e 255. La sequenza inizia con 125 e aumenta di 25 ogni volta che viene generato un numero. Poiché la sequenza è configurata per riprendere quando il valore supera il valore massimo di 200, la sequenza riprende dal valore minimo di 100.  
  
```  
CREATE SEQUENCE Test.DecSeq  
    AS decimal(3,0)   
    START WITH 125  
    INCREMENT BY 25  
    MINVALUE 100  
    MAXVALUE 200  
    CYCLE  
    CACHE 3  
;  
```  
  
 Eseguire l'istruzione seguente per visualizzare il primo valore; l'opzione `START WITH` di 125.  
  
```  
SELECT NEXT VALUE FOR Test.DecSeq;  
```  
  
 Eseguire l'istruzione altre tre volte affinché vengano restituiti i numeri 150, 175 e 200.  
  
 Eseguire nuovamente l'istruzione per vedere come il valore iniziale torna nuovamente all'opzione `MINVALUE` con valore 100.  
  
 Eseguire il codice seguente per confermare la dimensione della cache e vedere il valore corrente.  
  
```  
SELECT cache_size, current_value   
FROM sys.sequences  
WHERE name = 'DecSeq' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [VALORE successivo per &#40; Transact-SQL &#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
