---
title: SYMKEYPROPERTY (Transact-SQL) | Documenti Microsoft
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
- SYMKEYPROPERTY_TSQL
- SYMKEYPROPERTY
dev_langs: TSQL
helpviewer_keywords: SYMKEYPROPERTY
ms.assetid: 3d1f7075-3a3c-4660-8cd0-ed938b86fecd
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 12f285530db5557acb4b1317656bc53abbe59df0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="symkeyproperty-transact-sql"></a>SYMKEYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce l'algoritmo di una chiave simmetrica creato da un modulo EKM.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SYMKEYPROPERTY ( Key_ID , 'algorithm_desc' | 'string_sid' | 'sid' )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Key_ID*  
 Key_ID di una chiave simmetrica nel database. Per trovare il Key_ID quando si conosce solo il nome della chiave, utilizzare SYMKEY_ID. *Key_ID* è di tipo di dati **int**.  
  
 **'**algorithm_desc**'**  
 Specifica che l'output restituisce la descrizione dell'algoritmo della chiave simmetrica. Disponibile solo per le chiavi simmetriche create da un modulo EKM.  
  
## <a name="return-types"></a>Tipi restituiti  
 **sql_variant**  
  
## <a name="permissions"></a>Permissions  
 Sono richieste alcune autorizzazioni relative alla chiave simmetrica ed è necessario che al chiamante non sia stata negata l'autorizzazione VIEW per la chiave simmetrica.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito l'algoritmo della chiave simmetrica con Key_ID 256.  
  
```  
SELECT SYMKEYPROPERTY(256, 'algorithm_desc') AS Algorithm ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ASYMKEY_ID &#40; Transact-SQL &#41;](../../t-sql/functions/asymkey-id-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [KEY_ID &#40; Transact-SQL &#41;](../../t-sql/functions/key-id-transact-sql.md)   
 [ASYMKEYPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/asymkeyproperty-transact-sql.md)  
  
  
