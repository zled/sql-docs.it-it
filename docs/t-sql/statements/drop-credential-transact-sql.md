---
title: DROP CREDENTIAL (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/19/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP CREDENTIAL
- DROP_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing credentials
- DROP CREDENTIAL statement
- credentials [SQL Server], DROP CREDENTIAL statement
- authentication [SQL Server], credentials
- deleting credentials
- dropping credentials
ms.assetid: df22c826-317d-45a6-b078-186acb65f71e
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 99526bd72839ff483d39f0e78634ea27039388ae
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-credential-transact-sql"></a>DROP CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove una credenziale dal server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP CREDENTIAL credential_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *credential_name*  
 Nome della credenziale da rimuovere dal server.  
  
## <a name="remarks"></a>Osservazioni  
 Per eliminare la chiave privata associata a una credenziale senza rimuovere la credenziale stessa, utilizzare [ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md).  
  
 Informazioni sulle credenziali sono visibili nella **credentials** vista del catalogo.  
  
> [!WARNING]  
>  I proxy sono associati a credenziali. Se si eliminano le credenziali usate da un proxy, il proxy associato rimane in uno stato inutilizzabile. Quando si elimina una credenziale utilizzata da un proxy, eliminare il proxy (tramite [sp_delete_proxy &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md) e ricreare il proxy associato mediante [sp_add_proxy &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY CREDENTIAL. Per la rimozione di una credenziale di sistema è richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimossa la credenziale denominata `Saddles`.  
  
```  
DROP CREDENTIAL Saddles;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [Istruzione ALTER CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

