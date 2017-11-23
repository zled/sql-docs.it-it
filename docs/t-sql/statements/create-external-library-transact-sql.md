---
title: CREARE una libreria esterna (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: 
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL LIBRARY
- CREATE_EXTERNAL_LIBRARY_TSQL
- EXTERNAL LIBRARY
- EXTERNAL_LIBRARY_TSQL
dev_langs: TSQL
helpviewer_keywords: CREATE EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 8d0f700ba30b77e892b37e98c43996d6e654e7ea
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="create-external-library-transact-sql"></a>CREARE una libreria esterna (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

Carica i pacchetti R in un database dal percorso di file o flusso di byte specificata.

Questa istruzione viene utilizzato come un meccanismo generico utilizzato per l'amministratore del database caricare gli artefatti necessari per i nuovi runtime language esterno (R, Python, Java e così via) e le piattaforme del sistema operativo supportate da [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]. Attualmente sono supportati solo il linguaggio R e la piattaforma Windows.

## <a name="syntax"></a>Sintassi

```
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

Per il database con ambito all'utente vengono aggiunte librerie. Ovvero i nomi delle librerie vengono considerati come univoci all'interno del contesto di un utente specifico o un proprietario e i nomi delle librerie deve essere univoci per ogni utente. Ad esempio, due utenti **RUser1** e **RUser2** entrambi individualmente e separatamente caricare la libreria R `ggplot2`.

**owner_name**

Specifica il nome dell'utente o del ruolo che possiede la libreria esterna. Se viene omesso, la proprietà viene assegnata all'utente corrente.

Le librerie di proprietario del database sono considerate globale per il database e il runtime. In altre parole, i proprietari del database è possono creare librerie che contengono un set comune di librerie o i pacchetti che vengono condivisi da molti utenti. Quando viene creata una libreria esterna da un utente diverso dal `dbo` utente, la libreria esterna è privata per solo tale utente.

Quando l'utente **RUser1** esegue uno script R, il valore di `libPath` può contenere più percorsi. Il primo percorso è sempre il percorso della libreria condivisa creata dal proprietario del database. La seconda parte `libPath` specifica il percorso che contiene i pacchetti caricati singolarmente **RUser1**.

**file_spec**

Specifica il contenuto del pacchetto per una piattaforma specifica. Elemento di un solo file per ogni piattaforma è supportato.

Il file può essere specificato sotto forma di un percorso locale o un percorso di rete.

Facoltativamente, è possibile specificare la piattaforma del sistema operativo per il file. Elemento di un solo file o il contenuto è consentito per ogni piattaforma del sistema operativo per una lingua specifica o di runtime.

**library_bits**

Specifica il contenuto del pacchetto come valore letterale esadecimale, simile agli assembly. Questa opzione consente agli utenti di creare una libreria per modificare la raccolta se dispone dell'autorizzazione richiesta, ma non hanno accesso al percorso del file in qualsiasi cartella che il server può accedere.

**PIATTAFORMA = WINDOWS**

Specifica la piattaforma per il contenuto della libreria. Il valore predefinito per la piattaforma host in cui è in esecuzione SQL Server. Pertanto, l'utente non è necessario specificare il valore. È necessario nel caso in cui sono supportate più piattaforme o l'utente deve specificare una piattaforma diversa. Windows è l'unica piattaforma supportata.

## <a name="remarks"></a>Osservazioni

Per il linguaggio R, quando si utilizza un file, è necessario preparare i pacchetti sotto forma di file di archivio compresso con il. Estensione ZIP per Windows. Attualmente è supportata solo la piattaforma di Windows

Il `CREATE EXTERNAL LIBRARY` istruzione consente di caricare solo i bit di libreria per il database. La libreria non è installata effettivamente fino a quando un utente esegue uno script esterno in un secondo momento, eseguendo [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  

Librerie di caricamento per l'istanza possono essere pubblici o privati. Se la creazione della raccolta da un membro del `dbo`, la libreria è pubblica e può essere condivisa con tutti gli utenti. In caso contrario, la libreria è privata per solo tale utente.

È possibile utilizzare i BLOB come origine dati nella versione SQL Server 2017.

## <a name="permissions"></a>Permissions

Richiede il `CREATE ANY EXTERNAL LIBRARY` autorizzazione.

Per modificare una raccolta richiede l'autorizzazione separato, `ALTER ANY EXTERNAL LIBRARY`.

## <a name="examples"></a>Esempi

### <a name="a-add-an-external-library-to-a-database"></a>A. Aggiungere una libreria esterna a un database  

L'esempio seguente aggiunge una libreria esterna denominata customPackage a un database.

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  

Dopo la raccolta è stata caricata correttamente per l'istanza, un utente esegue il `sp_execute_external_script` procedura per installare la libreria.

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)
'
```

### <a name="b-installing-packages-with-dependencies"></a>B. Installazione di pacchetti con dipendenze

Se `packageB` presenta una dipendenza `packageA`, seguire questi principi generali:

+ Caricare sia il pacchetto di destinazione e le relative dipendenze.

    Entrambi i pacchetti devono essere in una cartella accessibile al server.

    ```sql
    CREATE EXTERNAL LIBRARY packageA 
    FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageA.zip') 
    WITH (LANGUAGE = 'R'); 
    
    CREATE EXTERNAL LIBRARY packageB FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageB.zip') 
    WITH (LANGUAGE = 'R');
    ```

+ Le dipendenze siano installate prima.

    Se un pacchetto necessario `packageA` è già stato caricato per l'istanza, è necessario non è stato installato separatamente. Il pacchetto richiesto `packageA` verrà installato quando `sp_execute_external_script` alla prima esecuzione per installare il pacchetto `packageB`.

    Tuttavia, se il pacchetto richiesto `packageA`, non è disponibile, installare il pacchetto di destinazione `packageB` avrà esito negativo.

    ```sql
    EXEC sp_execute_external_script 
    @language =N'R', 
    @script=N'
    # load packageB
    library(packageB)
    # call customPackageBFunc
    OutputDataSet <- customPackageBFunc()
    '
    with result sets (([result] int));    
    ```

### <a name="c-create-a-library-from-a-byte-stream"></a>C. Crea una libreria da un flusso di byte

L'esempio seguente crea una libreria passando aggiornato bits come un valore letterale esadecimale.

```SQL
CREATE EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

### <a name="d-change-an-existing-package-library"></a>D. Modificare una raccolta di pacchetto esistente

Il `ALTER EXTERNAL LIBRARY` istruzione DDL può essere utilizzata per aggiungere il nuovo contenuto libreria o modificare il contenuto di libreria esistente. Per modificare una raccolta esistente, è necessario il `ALTER ANY EXTERNAL LIBRARY` autorizzazione.

Per ulteriori informazioni, vedere [ALTER libreria esterna](alter-external-library-transact-sql.md).

### <a name="e-delete-a-package-library"></a>E. Eliminare una raccolta di pacchetti

Per eliminare una libreria di pacchetto dal database, eseguire l'istruzione:

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

> [!NOTE]
> A differenza degli altri `DROP` istruzioni [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)], questa istruzione supporta un parametro facoltativo che specifica l'autorizzazione utente. Questa opzione consente agli utenti con ruoli di proprietà di eliminare le raccolte caricate dagli utenti normali.

## <a name="see-also"></a>Vedere anche

[LIBRERIA esterna ALTER (Transact-SQL)](alter-external-library-transact-sql.md)  
[ELIMINARE una libreria esterna (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  
