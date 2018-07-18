---
title: FILEGROUPPROPERTY (Transact-SQL) | Microsoft Docs
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: afc112a5e07197ed8b0056a7daeddb55c0c418c9
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790148"
---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore di una proprietà di un filegroup quando vengono indicati il nome di un filegroup e il nome di una proprietà.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FILEGROUPPROPERTY ( filegroup_name , property )  
```  
  
## <a name="arguments"></a>Argomenti  
 *filegroup_name*  
 Espressione di tipo **sysname** che rappresenta il nome del filegroup per il quale restituire le informazioni della proprietà specificata.  
  
 *property*  
 Espressione di tipo **varchar(128)** contenente il nome della proprietà del filegroup da restituire. *property* può avere uno dei valori seguenti.  
  
|valore|Descrizione|Valore restituito|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Filegroup di sola lettura.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
|**IsUserDefinedFG**|Filegroup definito dall'utente.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
|**IsDefault**|Filegroup predefinito.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Remarks  
 *filegroup_name* corrisponde alla colonna **name** nella vista del catalogo **sys.filegroups**.  
  
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
 [FILEGROUP_ID &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Funzioni per i metadati &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
