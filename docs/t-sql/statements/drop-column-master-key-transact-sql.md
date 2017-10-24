---
title: CHIAVE MASTER della colonna (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 04/20/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP COLUMN MASTER KEY
- DROP_COLUMN_MASTER_KEY_TSQL
- DROP COLUMN MASTER
- DROP_COLUMN_MASTER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_keys catalog view
ms.assetid: fd5e77c8-a3ae-4795-bb46-b322c0500041
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d49d880d78982aa55bbaefc1fadc561e62a26dce
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-column-master-key-transact-sql"></a>DROP COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Elimina una chiave master della colonna da un database. Si tratta di un'operazione di metadati.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP COLUMN MASTER KEY key_name;  
```  
  
## <a name="arguments"></a>Argomenti  
 *key_name*  
 Il nome della chiave master della colonna.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile eliminare la chiave master della colonna solo se sono non presenti valori di chiave crittografati con la chiave master della colonna crittografia di colonna. Per eliminare i valori di chiavi di crittografia di colonna, utilizzare il [DROP COLUMN ENCRYPTION KEY](../../t-sql/statements/drop-column-encryption-key-transact-sql.md) istruzione.  
  
## <a name="permissions"></a>Permissions  
 Richiede **ALTER ANY COLUMN MASTER KEY** autorizzazione per il database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-column-master-key"></a>A. Eliminazione di una chiave master della colonna  
 Nell'esempio seguente elimina una chiave master di colonna denominata `MyCMK`.  
  
```  
DROP COLUMN MASTER KEY MyCMK;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)  
  
  

