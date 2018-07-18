---
title: FILEGROUP_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FILEGROUP_ID_TSQL
- FILEGROUP_ID
dev_langs:
- TSQL
helpviewer_keywords:
- FILEGROUP_ID function
- identification numbers [SQL Server], filegroups
- filegroups [SQL Server], IDs
- IDs [SQL Server], filegroups
- names [SQL Server], filegroups
ms.assetid: 852a76d8-9e61-4a31-84ee-c7edb84a061c
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 872d45d523869d1260e2d69ec62b99434439020e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33052668"
---
# <a name="filegroupid-transact-sql"></a>FILEGROUP_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero di identificazione (ID) di filegroup corrispondente al nome di filegroup specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FILEGROUP_ID ( 'filegroup_name' )   
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *filegroup_name* **'**  
 Espressione di tipo **sysname** che rappresenta il nome del filegroup per il quale si vuole restituire l'ID di filegroup.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Remarks  
 *filegroup_name* corrisponde alla colonna **name** nella vista del catalogo **sys.filegroups**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito l'ID di filegroup corrispondente al filegroup denominato `PRIMARY` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT FILEGROUP_ID('PRIMARY') AS [Filegroup ID];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
Filegroup ID  
------------  
1  

(1 row(s) affected)
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [FILEGROUP_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Funzioni per i metadati &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
