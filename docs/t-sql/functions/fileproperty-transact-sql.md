---
title: FILEPROPERTY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILEPROPERTY_TSQL
- FILEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file properties
- names [SQL Server], files
- displaying file properties
- file properties [SQL Server]
- FILEPROPERTY function
- file names [SQL Server], FILEPROPERTY
ms.assetid: b82244ed-d623-431f-aa06-8017349d847f
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7078fecb77bad44fd6aa4c3ce0baf9565f1d6d3f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore di una proprietà di un file quando vengono indicati il nome di un file nel database corrente e il nome di una proprietà. Restituisce NULL per i file che non sono nel database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>Argomenti  
 *file_name*  
 Espressione contenente il nome del file associato al database corrente per cui si desidera restituire le informazioni sulla proprietà. *file_name* è **nchar(128)**.  
  
 *proprietà*  
 Espressione contenente il nome della proprietà del file da restituire. *proprietà* è **varchar (128)**, e può essere uno dei valori seguenti.  
  
|Valore|Description|Valore restituito|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Filegroup di sola lettura.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
|**IsPrimaryFile**|File primario.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
|**IsLogFile**|File di log.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
|**SpaceUsed**|Quantità di spazio utilizzata dal file specificato.|Numero di pagine allocate nel file|  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 *file_name* corrisponde alla **nome** colonna il **Sys. master_files** o **Sys. database_files** vista del catalogo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita l'impostazione della proprietà `IsPrimaryFile` per il file `AdventureWorks_Data` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT FILEPROPERTY('AdventureWorks2012_Data', 'IsPrimaryFile')AS [Primary File];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Primary File   
-------------  
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [FILEGROUPPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

