---
title: FILE_IDEX (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FILE_IDEX
- FILE_IDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILE_IDEX function
- IDs [SQL Server], files
- file IDs [SQL Server]
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_IDEX
ms.assetid: 7532fea5-ee5e-4edd-b98b-111a7ba56c8e
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 54224c2b6f977f21764553ceddfb7e7be5fd10c7
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37788362"
---
# <a name="fileidex-transact-sql"></a>FILE_IDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Restituisce il numero di identificazione (ID) di file per il nome di file logico specificato del file di dati, file di log o file full-text nel database corrente.  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
FILE_IDEX ( file_name )  
```  
  
## <a name="arguments"></a>Argomenti  
 *file_name*  
 Espressione di tipo **sysname** che rappresenta il nome del file per il quale restituire l'ID file.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
 **NULL** in caso di errore  
  
## <a name="remarks"></a>Remarks  
 *file_name* corrisponde al nome file logico visualizzato nella colonna **name** della vista del catalogo [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md) o [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).  
  
 È possibile utilizzare FILE_IDEX in un elenco di selezione, una clausola WHERE o in tutti i casi in cui è consentita un'espressione. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-retrieving-the-file-id-of-a-specified-file"></a>A. Recupero dell'ID file di un file specificato  
Nell'esempio seguente viene restituito l'ID file per il file `AdventureWorks_Data`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX('AdventureWorks2012_Data') AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
### <a name="b-retrieving-the-file-id-when-the-file-name-is-not-known"></a>B. Recupero dell'ID file di un nome file non noto  
Nell'esempio seguente viene restituito l'ID file del file di log `AdventureWorks` mediante la selezione del nome file logico dalla vista del catalogo `sys.database_files`, dove il tipo di file è uguale a `1` (log).  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX((SELECT TOP (1) name FROM sys.database_files WHERE type = 1)) AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
2  
```  
  
### <a name="c-retrieving-the-file-id-of-a-full-text-catalog-file"></a>C. Recupero dell'ID file di un file del catalogo full-text  
Nell'esempio seguente viene restituito l'ID di un file full-text mediante la selezione del nome file logico dalla vista del catalogo `sys.database_files`, dove il tipo di file è uguale a `4` (full-text). Se non esiste un catalogo full-text, nell'esempio verrà restituito NULL.  
  
```sql  
SELECT FILE_IDEX((SELECT name FROM sys.master_files WHERE type = 4))  
AS 'File_ID';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni per i metadati &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
