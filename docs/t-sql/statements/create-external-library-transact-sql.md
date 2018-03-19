---
title: CREATE EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 02/25/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL LIBRARY
- CREATE_EXTERNAL_LIBRARY_TSQL
- EXTERNAL LIBRARY
- EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: e28716314837225586cf4bd1f80a37c5c6b824ab
ms.sourcegitcommit: 6e819406554efbd17bbf84cf210d8ebeddcf772d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2018
---
# <a name="create-external-library-transact-sql"></a>CREATE EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]  

Carica pacchetti R in un database dal flusso di byte o dal percorso di file specificato.

Questa istruzione funge da meccanismo generico per l'amministratore del database per il caricamento degli elementi necessari per i runtime dei nuovi linguaggi esterni (R, Python, Java e così via) e per le piattaforme del sistema operativo supportate da [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]. 

Attualmente sono supportati solo il linguaggio R e la piattaforma Windows. Il supporto di Python e Linux è previsto per una versione successiva.

## <a name="syntax"></a>Sintassi

```text
CREATE EXTERNAL LIBRARY library_name  
    [ AUTHORIZATION owner_name ]  
FROM <file_spec> [,…2]  
WITH ( LANGUAGE = 'R' )  
[ ; ]  

<file_spec> ::=  
{  
(CONTENT = { <client_library_specifier> | <library_bits> }  
[, PLATFORM = WINDOWS ])  
}  

<client_library_specifier> :: =  
  '[\\computer_name\]share_name\[path\]manifest_file_name'  
| '[local_path\]manifest_file_name'  
| '<relative_path_in_external_data_source>'  

<library_bits> :: =  
{ varbinary_literal | varbinary_expression }  
```

### <a name="arguments"></a>Argomenti

**library_name**

Al database con ambito dell'utente vengono aggiunte librerie. In altri termini, i nomi delle librerie sono univoci nel contesto di un utente o proprietario specifico e devono essere univoci per utente. I due utenti **RUser1** e **RUser2**, ad esempio, possono entrambi caricare la libreria R `ggplot2` individualmente e separatamente.

I nomi delle librerie non possono essere assegnati in modo arbitrario. Il nome di una libreria deve corrispondere al nome necessario per caricare la libreria R da R.

**owner_name**

Specifica il nome dell'utente o del ruolo proprietario della libreria esterna. Se viene omesso, la proprietà viene assegnata all'utente corrente.

Le librerie di proprietà del proprietario del database sono considerate globali per il database e il runtime. In altre parole, i proprietari di database possono creare librerie contenenti un set comune di librerie o pacchetti condiviso da molti utenti. Quando viene creata una libreria esterna da un utente diverso dall'utente `dbo`, la libreria esterna è privata e disponibile solo per tale utente.

Quando l'utente **RUser1** esegue uno script R, il valore di `libPath` può contenere più percorsi. Il primo percorso è sempre il percorso della libreria condivisa creata dal proprietario del database. La seconda parte di `libPath` specifica il percorso che contiene i pacchetti caricati individualmente da **RUser1**.

**file_spec**

Specifica il contenuto del pacchetto per una piattaforma specifica. È supportato soltanto un elemento di tipo file per piattaforma.

Il file può essere specificato usando il percorso locale o il percorso di rete.

Facoltativamente, è possibile specificare una piattaforma del sistema operativo per il file. È consentito un solo elemento di tipo file o un contenuto per piattaforma del sistema operativo per un linguaggio o un runtime specifico.

**library_bits**

Specifica il contenuto del pacchetto come valore letterale esadecimale, analogamente agli assembly. 

Questa opzione è utile se è necessario creare una libreria o modificare una libreria esistente (e si hanno le autorizzazioni necessarie a tale scopo), ma il file system del server è soggetto a restrizioni e non è possibile copiare i file di libreria in un percorso a cui il server può accedere.

**PLATFORM = WINDOWS**

Specifica la piattaforma per il contenuto della libreria. Il valore predefinito corrisponde alla piattaforma host in cui è in esecuzione SQL Server. Per l'utente, quindi, non è necessario specificare questo valore. È necessario nel caso in cui siano supportate più piattaforme o l'utente debba specificare una piattaforma diversa. 

In SQL Server 2017, Windows è l'unica piattaforma supportata.

## <a name="remarks"></a>Remarks

Per il linguaggio R, quando si usa un file, è necessario preparare i pacchetti sotto forma di file di archivio compressi usando l'estensione zip di Windows. Attualmente, Windows è l'unica piattaforma supportata. 

L'istruzione `CREATE EXTERNAL LIBRARY` carica i bit della libreria nel database. La libreria viene installata quando un utente esegue uno script esterno tramite [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) e chiama il pacchetto o la libreria.

Le librerie caricate nell'istanza possono essere pubbliche o private. Se la libreria viene creata da un membro di `dbo`, la libreria è pubblica e può essere condivisa da tutti gli utenti. In caso contrario, la libreria è privata e disponibile solo per tale utente.

In SQL Server versione 2017 non è possibile usare oggetti BLOB come origini dati.

## <a name="permissions"></a>Autorizzazioni

È necessaria l'autorizzazione `CREATE ANY EXTERNAL LIBRARY`.

Per modificare una libreria è necessaria un'altra autorizzazione, `ALTER ANY EXTERNAL LIBRARY`.

## <a name="examples"></a>Esempi

### <a name="a-add-an-external-library-to-a-database"></a>A. Aggiungere una libreria esterna a un database  

L'esempio seguente aggiunge una libreria esterna denominata `customPackage` a un database.

```sql
CREATE EXTERNAL LIBRARY customPackage
FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip') WITH (LANGUAGE = 'R');
```  

Dopo il caricamento della libreria nell'istanza, l'utente esegue la procedura `sp_execute_external_script` per installare la libreria.

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'library(customPackage)'
```

### <a name="b-installing-packages-with-dependencies"></a>B. Installare pacchetti con dipendenze

Se il pacchetto che si vuole installare presenta dipendenze, è fondamentale analizzare le dipendenze sia di primo che di secondo livello e assicurarsi che tutti i pacchetti necessari siano disponibili _prima_ di tentare l'installazione del pacchetto di destinazione.

Si supponga ad esempio di voler installare un nuovo pacchetto, `packageA`:

+ `packageA` ha una dipendenza da `packageB`
+ `packageB` ha una dipendenza da `packageC`

Perché l'installazione di `packageA` sia possibile, è necessario creare librerie per `packageB` e `packageC` contemporaneamente all'aggiunta di `packageA` a SQL Server. Assicurarsi di controllare anche le versioni dei pacchetti richiesti.

In pratica, le dipendenze dei pacchetti dai pacchetti più diffusi sono in genere molto più complesse rispetto a questo semplice esempio. ggplot2, ad esempio, può richiedere oltre 30 pacchetti e questi ultimi possono richiedere pacchetti aggiuntivi non disponibili nel server. La mancanza o una versione non corretta di uno qualsiasi di questi pacchetti può causare la mancata riuscita dell'installazione.

Poiché può essere difficile determinare tutte le dipendenze semplicemente esaminando il manifesto del pacchetto, è consigliabile usare un pacchetto come [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) o [iGraph](http://igraph.org/redirect.html) per identificare tutti i pacchetti che possono essere necessari per eseguire l'installazione.

+ Caricare il pacchetto di destinazione e le sue dipendenze. Tutti i file devono essere in una cartella accessibile al server.

    ```sql
    CREATE EXTERNAL LIBRARY packageA 
    FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageA.zip') 
    WITH (LANGUAGE = 'R'); 
    GO

    CREATE EXTERNAL LIBRARY packageB FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageB.zip') 
    WITH (LANGUAGE = 'R');
    GO

    CREATE EXTERNAL LIBRARY packageC FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageC.zip') 
    WITH (LANGUAGE = 'R');
    GO
    ```

+ Installare per primi i pacchetti richiesti.

    Se un pacchetto richiesto è già stato caricato nell'istanza, non è necessario aggiungerlo nuovamente. È sufficiente assicurarsi che la versione del pacchetto esistente sia corretta. 
    
    I pacchetti richiesti `packageC` e `packageB` vengono installati, nell'ordine corretto, quando `sp_execute_external_script` viene eseguita per la prima volta per installare il pacchetto `packageA`.

    Se tuttavia un qualsiasi pacchetto richiesto non è disponibile, l'installazione del pacchetto di destinazione `packageA` non riesce.

    ```sql
    EXEC sp_execute_external_script 
    @language =N'R', 
    @script=N'
    # load the desired package packageA
    library(packageA)
    # call function from package
    OutputDataSet <- packageA.function()
    '
    with result sets (([result] int));    
    ```

### <a name="c-create-a-library-from-a-byte-stream"></a>C. Creare una libreria da un flusso di byte

Se non si ha la possibilità di salvare i file del pacchetto in un percorso nel server, è anche possibile passare il contenuto del pacchetto in una variabile. L'esempio seguente crea una libreria passando i bit come valori letterali esadecimali.

```SQL
CREATE EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

Qui i valori esadecimali sono stati troncati per migliorare la leggibilità.

### <a name="d-change-an-existing-package-library"></a>D. Modificare una libreria di pacchetti esistente

È possibile usare l'istruzione DDL `ALTER EXTERNAL LIBRARY` per aggiungere nuovo contenuto a una libreria o modificare il contenuto esistente della libreria stessa. Per modificare una libreria esistente è necessaria l'autorizzazione `ALTER ANY EXTERNAL LIBRARY`.

Per altre informazioni, vedere [ALTER EXTERNAL LIBRARY](alter-external-library-transact-sql.md).

### <a name="e-delete-a-package-library"></a>E. Per eliminare una libreria di pacchetti

Per eliminare una libreria di pacchetti dal database, eseguire l'istruzione seguente:

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

> [!NOTE]
> A differenza di altre istruzioni `DROP` in [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)], questa istruzione supporta un parametro facoltativo che specifica l'autorizzazione dell'utente. Questa opzione consente agli utenti con ruoli di proprietà di eliminare le librerie caricate dagli utenti normali.

## <a name="see-also"></a>Vedere anche

[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  
