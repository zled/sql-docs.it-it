---
title: ELIMINARE una libreria esterna (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: 8c45da28bf795fca50454fde21eb7d2c3c798296
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="drop-external-library-transact-sql"></a>ELIMINARE una libreria esterna (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Elimina una raccolta di pacchetto esistente.

## <a name="syntax"></a>Sintassi  

```
DROP EXTERNAL LIBRARY library_name  
[ AUTHORIZATION owner_name ];  
```

### <a name="arguments"></a>Argomenti

**library_name**

Specifica il nome di una libreria di pacchetto esistente.

Le librerie sono limitate all'utente. I nomi delle librerie, sono considerati univoci all'interno del contesto di un utente specifico o un proprietario.

**owner_name**

Specifica il nome dell'utente o del ruolo che possiede la libreria esterna.

I proprietari del database possono eliminare le raccolte create da altri utenti.

### <a name="return-values"></a>Valori restituiti

Se l'istruzione ha esito positivo, viene restituito un messaggio informativo.

## <a name="remarks"></a>Osservazioni

A differenza degli altri `DROP` istruzioni in SQL Server, questa istruzione supporta la specifica di una clausola authorization facoltativo. In questo modo **dbo** o gli utenti di **db_owner** ruolo per eliminare una raccolta di pacchetti caricati da un utente normale nel database.

## <a name="examples"></a>Esempi

Aggiungere un pacchetto R personalizzato, denominato `customPackage`, a un database:

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 'C:\Users\Username\CustomPackages\customPackage.zip';
```

Eliminare il `customPackage` libreria.

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

## <a name="see-also"></a>Vedere anche  
[CREARE una libreria esterna (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

