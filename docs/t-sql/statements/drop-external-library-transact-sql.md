---
title: ELIMINARE una libreria esterna (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: ac2814f7c0b0d1bf6de60d52ea65e54caab0f72d
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="drop-external-library-transact-sql"></a>ELIMINARE una libreria esterna (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

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
[LIBRERIA esterna ALTER (Transact-SQL)](alter-external-library-transact-sql.md)  
[Sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[Sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  


