---
title: KEY_ID (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Key_ID
- Key_ID_TSQL
dev_langs: TSQL
helpviewer_keywords:
- identification numbers [SQL Server], symmetric keys
- KEY_ID function
- symmetric keys [SQL Server], IDs
- IDs [SQL Server], symmetric keys
ms.assetid: d7309542-dbbe-41dc-b42e-5d9a1c8b4838
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fb01508366558f7d5f755db50efb4a5a5b0d937d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="keyid-transact-sql"></a>KEY_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce l'ID di una chiave simmetrica nel database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Key_ID ( 'Key_Name' )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *Key_Name* **'**  
 Nome di una chiave simmetrica nel database.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 Il nome di una chiave temporanea deve iniziare con un simbolo di cancelletto (#).  
  
## <a name="permissions"></a>Permissions  
 Dal momento che le chiavi temporanee sono disponibili solo nella sessione in cui vengono create, per accedervi non sono necessarie autorizzazioni. Per accedere a una chiave non temporanea, è necessario che il chiamante disponga di un'autorizzazione per la chiave e che non gli sia stata negata l'autorizzazione VIEW per la chiave.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-id-of-a-symmetric-key"></a>A. Restituzione dell'ID di una chiave simmetrica  
 Nell'esempio seguente viene restituito l'ID di una chiave denominata `ABerglundKey1`.  
  
```  
SELECT KEY_ID('ABerglundKey1');  
```  
  
### <a name="b-returning-the-id-of-a-temporary-symmetric-key"></a>B. Restituzione dell'ID di una chiave simmetrica temporanea  
 Nell'esempio seguente viene restituito l'ID di una chiave simmetrica temporanea. Si noti che il nome della chiave è preceduto dal simbolo di cancelletto `#`.  
  
```  
SELECT KEY_ID('#ABerglundKey2');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [KEY_GUID &#40; Transact-SQL &#41;](../../t-sql/functions/key-guid-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.key_encryptions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
