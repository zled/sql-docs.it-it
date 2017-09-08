---
title: File_id (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILE_ID
- FILE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], files
- file IDs [SQL Server]
- FILE_ID function
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_ID
ms.assetid: 6a7382cf-a360-4d62-b9d2-5d747f56f076
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2544da5cb252b27f42a82e1fa400d7c28f503f20
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="fileid-transact-sql"></a>FILE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero di identificazione (ID) del file per il nome di file logico specificato del database corrente.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FILE_ID ( file_name )  
```  
  
## <a name="arguments"></a>Argomenti  
 *file_name*  
 È un'espressione di tipo **sysname** che rappresenta il nome del file per cui restituire l'ID del file.  
  
## <a name="return-types"></a>Tipi restituiti  
 **smallint**  
  
## <a name="remarks"></a>Osservazioni  
 *file_name* corrisponde al nome di file logico visualizzato nella colonna nome nelle viste del catalogo sys. master_files o Sys. database_files.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il numero di identificazione di file assegnato ai cataloghi full-text è maggiore di 32767. Poiché il tipo restituito della funzione FILE_ID è **smallint**, questa funzione non può essere utilizzata per i file full-text. Utilizzare [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) invece.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito l'ID file per il file `AdventureWorks_Data`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT FILE_ID('AdventureWorks2012_Data')AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del motore di database deprecate in SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [File_name &#40; Transact-SQL &#41;](../../t-sql/functions/file-name-transact-sql.md)   
 [Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
