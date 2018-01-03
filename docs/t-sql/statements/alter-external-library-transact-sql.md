---
title: ALTER libreria esterna (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs: TSQL
helpviewer_keywords: ALTER EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 28a62f00b479506e919faf2cbdbf1202045192eb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="alter-external-library-transact-sql"></a>LIBRERIA esterna ALTER (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Modifica il contenuto di una libreria pacchetto esterno esistente.

## <a name="syntax"></a>Sintassi

```
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = 'R' )
[ ; ]

<file_spec> ::=
{
(CONTENT = { <client_library_specifier> | <library_bits> | NONE}
[, PLATFORM = WINDOWS )
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

Specifica il nome di una libreria di pacchetto esistente. Le librerie sono limitate all'utente. I nomi delle librerie, sono considerati univoci all'interno del contesto di un utente specifico o un proprietario.

**owner_name**

Specifica il nome dell'utente o del ruolo che possiede la libreria esterna.

**file_spec**

Specifica il contenuto del pacchetto per una piattaforma specifica. Elemento di un solo file per ogni piattaforma è supportato.

Il file può essere specificato sotto forma di un percorso locale o un percorso di rete. Se l'opzione di origine dati è specificato, il nome del file può essere un percorso relativo rispetto al contenitore a cui fa riferimento il `EXTERNAL DATA SOURCE`.

Facoltativamente, è possibile specificare la piattaforma del sistema operativo per il file. Elemento di un solo file o il contenuto è consentito per ogni piattaforma del sistema operativo per una lingua specifica o di runtime.

**DATA_SOURCE = external_data_source_name**

Specifica il nome dell'origine dati esterna che contiene il percorso del file della libreria. Questo percorso deve fare riferimento a un percorso di archiviazione blob di Azure. Per creare un'origine dati esterna, utilizzare [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](create-external-data-source-transact-sql.md).

> [!IMPORTANT] 
> Attualmente, i BLOB non sono supportati come origine dati nella versione SQL Server 2017.

**library_bits**

Specifica il contenuto del pacchetto come valore letterale esadecimale, simile agli assembly. Questa opzione consente agli utenti di creare una libreria per modificare la raccolta se dispone dell'autorizzazione richiesta, ma non hanno accesso al percorso del file in qualsiasi cartella che il server può accedere.

**PIATTAFORMA = WINDOWS**

Specifica la piattaforma per il contenuto della libreria. Questo valore è obbligatorio quando si modifica una raccolta esistente per aggiungere una piattaforma diversa. Windows è l'unica piattaforma supportata.

## <a name="remarks"></a>Osservazioni

Per il linguaggio R, è necessario preparare i pacchetti sotto forma di file di archivio compresso con il. Estensione ZIP per Windows. Attualmente è supportata solo la piattaforma Windows.  

Il `ALTER EXTERNAL LIBRARY` istruzione consente di caricare solo i bit di libreria per il database. La libreria modificata non è installata effettivamente fino a quando un utente esegue uno script esterno in un secondo momento, eseguendo [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

## <a name="permissions"></a>Autorizzazioni

Richiede il `ALTER ANY EXTERNAL LIBRARY` autorizzazione. Gli utenti che ha creato una libreria esterna, è possibile modificare tale libreria esterna.

## <a name="examples"></a>Esempi

Nell'esempio seguente modifica una libreria esterna denominata customPackage.

### <a name="a-replace-the-contents-of-a-library-using-a-file"></a>A. Sostituire il contenuto di una libreria tramite un file

L'esempio seguente modifica una libreria esterna denominata customPackage, utilizzando un file compresso contenente i bit aggiornati.

```sql
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  

Per installare la libreria aggiornata, eseguire la stored procedure `sp_execute_external_script`.

```sql   
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)
# call customPackageFunc
OutputDataSet <- customPackageFunc()
'
WITH RESULT SETS (([result] int));
```

### <a name="b-alter-an-existing-library-using-a-byte-stream"></a>B. Modificare una raccolta esistente utilizzando un flusso di byte

L'esempio seguente modifica la raccolta esistente passando i nuovi bit come un esadecimale letterale.

```SQL
ALTER EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

## <a name="see-also"></a>Vedere anche  

[CREARE una libreria esterna (Transact-SQL)](create-external-library-transact-sql.md)
[DROP libreria esterna (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  
