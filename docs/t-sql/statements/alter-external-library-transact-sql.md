---
title: ALTER libreria esterna (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 541419770828e01cca82fb33ead1b22170f8e4f3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-external-library-transact-sql"></a>LIBRERIA esterna ALTER (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

Modifica il contenuto di libreria esistente.  

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

**PIATTAFORMA = WINDOWS**

Specifica la piattaforma per il contenuto della libreria. Questo valore è obbligatorio quando si modifica una raccolta esistente per aggiungere una piattaforma diversa. Windows è l'unica piattaforma supportata.

## <a name="remarks"></a>Osservazioni

Per il linguaggio R, è necessario preparare i pacchetti sotto forma di file di archivio compresso con il. Estensione ZIP per Windows. Attualmente è supportata solo la piattaforma Windows.  
Il `ALTER EXTERNAL LIBRARY` istruzione consente di caricare solo i bit di libreria per il database. La libreria modificata non è installata effettivamente fino a quando un utente esegue uno script esterno in un secondo momento, eseguendo [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

## <a name="permissions"></a>Permissions
Richiede il `ALTER ANY EXTERNAL LIBRARY` autorizzazione. Gli utenti che ha creato una libreria esterna, è possibile modificare tale libreria esterna.

## <a name="examples"></a>Esempi

L'esempio seguente modifica una libreria esterna denominata customPackage.

```sql  
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  
Eseguire quindi il `sp_execute_external_script` procedura per installare la libreria.

```sql   
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)

# call customPackageFunc
OutputDataSet <- customPackageFunc()
'
with result sets (([result] int));    
```


## <a name="see-also"></a>Vedere anche  
[CREARE una libreria esterna (Transact-SQL)](create-external-library-transact-sql.md)
[DROP libreria esterna (Transact-SQL)](drop-external-library-transact-sql.md)  
[Sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[Sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

