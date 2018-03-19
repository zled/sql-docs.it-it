---
title: ALTER EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
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
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: 0581957db73b82b9486f938d17b4c8938e20258d
ms.sourcegitcommit: 6e819406554efbd17bbf84cf210d8ebeddcf772d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2018
---
# <a name="alter-external-library-transact-sql"></a>ALTER EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Modifica il contenuto di una libreria di pacchetti esterna esistente.

## <a name="syntax"></a>Sintassi

```text
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

Specifica il nome di una libreria di pacchetti esistente. Le librerie hanno un ambito di tipo utente. In altri termini i nomi delle librerie sono univoci nel contesto di un utente o proprietario specifico.

Il nome della libreria non può essere assegnato in modo arbitrario. È quindi necessario usare il nome previsto dal runtime di chiamata quando viene caricato il pacchetto.

**owner_name**

Specifica il nome dell'utente o del ruolo che è proprietario della libreria esterna.

**file_spec**

Specifica il contenuto del pacchetto per una piattaforma specifica. È supportato soltanto un elemento di tipo file per piattaforma.

Il file può essere specificato usando il percorso locale o il percorso di rete. Se l'opzione dell'origine dati è specificata, il nome del file può essere un percorso relativo che riguarda il contenitore a cui si fa riferimento in `EXTERNAL DATA SOURCE`.

Facoltativamente, è possibile specificare una piattaforma del sistema operativo per il file. È consentito un solo elemento di tipo file o un contenuto per piattaforma del sistema operativo per un linguaggio o un runtime specifico.

**DATA_SOURCE = external_data_source_name**

Specifica il nome dell'origine dati esterna che contiene il percorso del file di libreria. Questo percorso deve fare riferimento a un percorso di archiviazione BLOB di Azure. Per creare un'origine dati esterna, usare [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](create-external-data-source-transact-sql.md).

> [!IMPORTANT] 
> Attualmente, i BLOB non sono supportati come origine dati nella versione SQL Server 2017.

**library_bits**

Specifica il contenuto del pacchetto come valore letterale esadecimale, analogamente agli assembly. 

Questa opzione è utile quando si ha l'autorizzazione necessaria a modificare una libreria, ma l'accesso ai file nel server è limitato e non è possibile salvare il contenuto in un percorso accessibile al server.

In alternativa, è possibile passare il contenuto dei pacchetti come variabile in un formato binario.

**PLATFORM = WINDOWS**

Specifica la piattaforma per il contenuto della libreria. Si tratta di un valore obbligatorio quando si modifica una libreria esistente per poter aggiungere una piattaforma diversa. Windows è l'unica piattaforma supportata.

## <a name="remarks"></a>Remarks

Per il linguaggio R, è necessario preparare i pacchetti sotto forma di file di archivio compressi usando l'estensione zip di Windows. Attualmente, Windows è l'unica piattaforma supportata.  

L'istruzione `ALTER EXTERNAL LIBRARY` carica solo i bit della libreria nel database. La libreria modificata viene installata quando un utente esegue il codice [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) che chiama la libreria.

## <a name="permissions"></a>Autorizzazioni

È necessaria l'autorizzazione `ALTER ANY EXTERNAL LIBRARY`. Possono modificare la libreria esterna gli utenti che hanno creato una libreria esterna.

## <a name="examples"></a>Esempi

Nell'esempio seguente viene modificata una libreria esterna denominata `customPackage`.

### <a name="a-replace-the-contents-of-a-library-using-a-file"></a>A. Sostituire il contenuto di una libreria usando un file

Nell'esempio seguente viene modificata una libreria esterna denominata `customPackage`, usando un file compresso che contiene i bit aggiornati.

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
@script=N'library(customPackage)'
;
```

### <a name="b-alter-an-existing-library-using-a-byte-stream"></a>B. Modificare una libreria esistente usando un flusso di byte

Nell'esempio seguente viene modificata la libreria esistente passando i nuovi bit come valore letterale esadecimale.

```SQL
ALTER EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

In questo esempio di codice il contenuto della variabile viene troncato per facilitarne la lettura.

## <a name="see-also"></a>Vedere anche

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md) 
