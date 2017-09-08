---
title: FILEGROUPPROPERTY (Transact-SQL) | Documenti Microsoft
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
- FILEGROUPPROPERTY_TSQL
- FILEGROUPPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], property values
- FILEGROUPPROPERTY function
- viewing filegroup properties
- displaying filegroup properties
ms.assetid: b3a930e6-df05-4034-929c-f681f5f6fc6e
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 050ec0b7c3fdc9146a25b1b1f372ee4928d80c09
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore di una proprietà di un filegroup quando vengono indicati il nome di un filegroup e il nome di una proprietà.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FILEGROUPPROPERTY ( filegroup_name , property )  
```  
  
## <a name="arguments"></a>Argomenti  
 *filegroup_name*  
 È un'espressione di tipo **sysname** che rappresenta il nome del filegroup per il quale restituire le informazioni sulle proprietà denominate.  
  
 *proprietà*  
 È un'espressione di tipo **varchar (128)** contiene il nome della proprietà del filegroup da restituire. *proprietà* può essere uno dei valori seguenti.  
  
|Valore|Description|Valore restituito|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Filegroup di sola lettura.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
|**IsUserDefinedFG**|Filegroup definito dall'utente.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
|**La proprietà IsDefault**|Filegroup predefinito.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 *filegroup_name* corrisponde alla **nome** colonna il **Sys. FileGroups** vista del catalogo.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene restituita l'impostazione della proprietà `IsDefault` per il filegroup primario nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT FILEGROUPPROPERTY('PRIMARY', 'IsDefault') AS 'Default Filegroup';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Default Filegroup   
---------------------   
1  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Filegroup_id &#40; Transact-SQL &#41;](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Sys. FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
