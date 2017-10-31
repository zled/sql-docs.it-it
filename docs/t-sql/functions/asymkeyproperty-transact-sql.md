---
title: ASYMKEYPROPERTY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASYMKEYPROPERTY_TSQL
- ASYMKEYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASYMKEYPROPERTY
ms.assetid: a30581f2-e1b1-4996-93e6-527ff96b7c42
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62ed19d07264d971045582c093a4c5ccdf6d8926
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="asymkeyproperty-transact-sql"></a>ASYMKEYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce le proprietà di una chiave asimmetrica.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
ASYMKEYPROPERTY (Key_ID , 'algorithm_desc' | 'string_sid' | 'sid')  
```  
  
## <a name="arguments"></a>Argomenti  
*Key_ID*  
Key_ID di una chiave asimmetrica nel database. Per trovare il Key_ID quando si conosce solo il nome della chiave, utilizzare ASYMKEY_ID. *Key_ID* è di tipo di dati **int**.
  
**'**algorithm_desc**'**  
Specifica che l'output restituisce la descrizione dell'algoritmo della chiave asimmetrica. Disponibile solo per le chiavi asimmetriche create da un modulo EKM.
  
**'**string_sid**'**  
Specifica che l'output restituisce il SID della chiave asimmetrica in **nvarchar()** formato.
  
**'**sid**'**  
Specifica che l'output restituisce il SID della chiave asimmetrica in formato binario.
  
## <a name="return-types"></a>Tipi restituiti  
**sql_variant**
  
## <a name="permissions"></a>Permissions  
Sono richieste le autorizzazioni relative alla chiave asimmetrica ed è necessario che al chiamante non sia stata negata l'autorizzazione VIEW per la chiave asimmetrica.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente vengono restituite le proprietà della chiave asimmetrica con Key_ID 256.
  
```sql
SELECT   
ASYMKEYPROPERTY(256, 'algorithm_desc') AS Algorithm,  
ASYMKEYPROPERTY(256, 'string_sid') AS String_SID,  
ASYMKEYPROPERTY(256, 'sid') AS SID ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
[ALTER ASYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)  
[DROP ASYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)  
[SIGNBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/signbyasymkey-transact-sql.md)  
[VERIFYSIGNEDBYASYMKEY &#40; Transact-SQL &#41;](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)  
[Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
[asymmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)  
[Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
[ASYMKEY_ID &#40; Transact-SQL &#41;](../../t-sql/functions/asymkey-id-transact-sql.md)  
[SYMKEYPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/symkeyproperty-transact-sql.md)
  
  

