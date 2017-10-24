---
title: CERTPRIVATEKEY (Transact-SQL) | Documenti Microsoft
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
- CERTPRIVATEKEY
- CERTPRIVATEKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTPRIVATEKEY
ms.assetid: 33e0f01e-39ac-46da-94ff-fe53b1116df4
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11a44f9203f9242a8f90ce3ca667bc1fea479dc2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="certprivatekey-transact-sql"></a>CERTPRIVATEKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce la chiave privata di un certificato in formato binario. Questa funzione accetta tre argomenti.
-   ID certificato.  
-   Password di crittografia utilizzata per crittografare i bit delle chiavi private quando vengono restituiti dalla funzione, in modo che le chiavi non vengano esposte in testo non crittografato agli utenti.  
-   Password di decrittografia facoltativa. Se viene specificata una password di decrittografia, viene utilizzata per decrittografare la chiave privata del certificato, in caso contrario viene utilizzata la chiave master del database.  
  
Solo gli utenti che dispongono dell'accesso alla chiave privata del certificato saranno in grado di utilizzare questa funzione. Questa funzione restituisce la chiave privata nel formato PVK.
  
## <a name="syntax"></a>Sintassi  
  
```sql
CERTPRIVATEKEY   
    (  
          cert_ID   
        , ' encryption_password '   
      [ , ' decryption_password ' ]  
    )  
```  
  
## <a name="arguments"></a>Argomenti  
*certificate_ID*  
È il **certificate_id** del certificato. Questa opzione è disponibile da Sys. Certificates o utilizzando il [CERT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) (funzione). *cert_id* è di tipo **int**
  
*encryption_password*  
Password utilizzata per crittografare il valore binario restituito.
  
*decryption_password*  
Password utilizzata per decrittografare il valore binario restituito.
  
## <a name="return-types"></a>Tipi restituiti
**varbinary**
  
## <a name="remarks"></a>Osservazioni  
**CERTENCODED** e **CERTPRIVATEKEY** vengono utilizzate insieme per restituire parti diverse di un certificato in formato binario.
  
## <a name="permissions"></a>Permissions  
**CERTPRIVATEKEY** è disponibile al pubblico.
  
## <a name="examples"></a>Esempi  
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Use 5tr0ng P^55Words'  
GO  
CREATE CERTIFICATE Shipping04   
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20141031';  
GO  
SELECT CERTPRIVATEKEY(CERT_ID('Shipping04'), 'jklalkaa/; uia3dd');  
```  
  
Per un esempio più complesso che utilizza **CERTPRIVATEKEY** e **CERTENCODED** per copiare un certificato a un altro database, vedere l'esempio B nell'argomento [CERTENCODED &#40; Transact-SQL &#41; ](../../t-sql/functions/certencoded-transact-sql.md).
  
## <a name="see-also"></a>Vedere anche
[Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CREATE CERTIFICATE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-certificate-transact-sql.md) 
 [Funzioni di sicurezza &#40; Transact-SQL &#41; ](../../t-sql/functions/security-functions-transact-sql.md) 
 [Sys. Certificates &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  

