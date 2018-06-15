---
title: DROP EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/05/2018
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0b72dd7a41e4d7cca0988ac28efd0f9cb60ca739
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33066268"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Elimina una libreria di pacchetti esistente. Le librerie di pacchetti sono usate da runtime esterni supportati, ad esempio R o Python.

## <a name="syntax"></a>Sintassi

```sql
DROP EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ];
```

### <a name="arguments"></a>Argomenti

**library_name**

Specifica il nome di una libreria di pacchetti esistente.

Le librerie hanno un ambito di tipo utente. I nomi delle librerie devono essere univoci nel contesto di un utente o proprietario specifico.

**owner_name**

Specifica il nome dell'utente o del ruolo che è proprietario della libreria esterna.

I proprietari di database possono eliminare le librerie create da altri utenti.

## <a name="permissions"></a>Autorizzazioni

Per eliminare una libreria è necessario il privilegio ALTER ANY EXTERNAL LIBRARY. Per impostazione predefinita, anche un proprietario del database o il proprietario dell'oggetto può eliminare una libreria esterna.

### <a name="return-values"></a>Valori restituiti

Se l'istruzione ha esito positivo viene restituito un messaggio informativo.

## <a name="remarks"></a>Remarks

A differenza di altre istruzioni `DROP` in SQL Server, questa istruzione supporta la specifica di una clausola di autorizzazione facoltativa. In questo modo gli utenti **dbo** o gli utenti con ruolo **db_owner** possono eliminare una libreria di pacchetti caricata nel database da un utente comune.

## <a name="examples"></a>Esempi

Aggiungere il pacchetto R personalizzato, `customPackage`, a un database:

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM (CONTENT = 'C:\temp\customPackage_v1.1.zip')
WITH (LANGUAGE = 'R');
GO
```

Eliminare la libreria `customPackage`.

```sql
DROP EXTERNAL LIBRARY customPackage;
```

## <a name="see-also"></a>Vedere anche

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

