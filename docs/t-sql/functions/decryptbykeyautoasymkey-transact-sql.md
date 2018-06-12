---
title: DECRYPTBYKEYAUTOASYMKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2015
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOASYMKEY_TSQL
- DECRYPTBYKEYAUTOASYMKEY
dev_langs:
- TSQL
helpviewer_keywords:
- DECRYPTBYKEYAUTOASYMSKEY function
ms.assetid: 5521d4cf-740c-4ede-98b6-4ba90b84e32d
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 05ab6a324d1193c301539780b55bdbd5494c3524
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779547"
---
# <a name="decryptbykeyautoasymkey-transact-sql"></a>DECRYPTBYKEYAUTOASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Questa funzione decrittografa i dati crittografati. A tale scopo, per prima cosa decrittografa una chiave simmetrica con una chiave asimmetrica separata e quindi decrittografa i dati crittografati con la chiave simmetrica estratta nel primo "passaggio".  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DecryptByKeyAutoAsymKey ( akey_ID , akey_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *akey_ID*  
ID della chiave asimmetrica usata per crittografare la chiave simmetrica. *akey_ID* ha un tipo di dati **int**.  
  
 *akey_password*  
Password che protegge la chiave asimmetrica. *akey_password* può avere un valore NULL se la chiave master del database protegge la chiave privata asimmetrica. *akey_password* ha un tipo di dati **nvarchar**.  
  
 '*ciphertext*'  
Dati crittografati con la chiave. *ciphertext* ha un tipo dati **varbinary**.  
  
 @ciphertext  
Variabile di tipo **varbinary** contenente dati crittografati con la chiave simmetrica.  
  
 *add_authenticator*  
Indica se il processo di crittografia originale includeva e crittografava un autenticatore insieme al testo non crittografato. Deve corrispondere al valore passato a [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) durante il processo di crittografia dei dati. *add_authenticator* ha un valore pari a 1 se il processo di crittografia ha usato un autenticatore. *add_authenticator* ha un tipo di dati **int**.  
  
 @add_authenticator  
Variabile che indica se il processo di crittografia originale includeva e crittografava un autenticatore insieme al testo non crittografato. Deve corrispondere al valore passato a [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) durante il processo di crittografia dei dati. *@add_authenticator* ha un tipo di dati **int**.
  
 *authenticator*  
Dati usati come base per la generazione dell'autenticatore. Deve corrispondere al valore specificato per [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *authenticator* ha un tipo di dati **sysname**.  
  
 @authenticator  
Variabile contenente i dati dai quali derivare un autenticatore. Deve corrispondere al valore specificato per [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *@authenticator* ha un tipo di dati **sysname**.  
  
## <a name="return-types"></a>Tipi restituiti  
**varbinary** con un valore massimo di 8.000 byte.  
  
## <a name="remarks"></a>Remarks  
`DECRYPTBYKEYAUTOASYMKEY` include le funzionalità di OPEN SYMMETRIC KEY e DecryptByKey. In un'unica operazione consente di decrittografare una chiave simmetrica e di usarla per la decrittografia del testo.  
  
## <a name="permissions"></a>Autorizzazioni  
È richiesta l'autorizzazione `VIEW DEFINITION` per la chiave simmetrica e l'autorizzazione `CONTROL` per la chiave asimmetrica.  
  
## <a name="examples"></a>Esempi  
In questo esempio viene illustrato l'uso di `DECRYPTBYKEYAUTOASYMKEY` per semplificare il codice di decrittografia. Questo codice deve essere eseguito in un database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] per cui non è già presente una chiave master.  
  
```  
--Create the keys and certificate.  
USE AdventureWorks2012;  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'mzkvdMlk979438teag$$ds987yghn)(*&4fdg^';  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'mzkvdMlk979438teag$$ds987yghn)(*&4fdg^';  
CREATE ASYMMETRIC KEY SSN_AKey   
    WITH ALGORITHM = RSA_2048 ;   
GO  
CREATE SYMMETRIC KEY SSN_Key_02 WITH ALGORITHM = DES  
    ENCRYPTION BY ASYMMETRIC KEY SSN_AKey;  
GO  
--  
--Add a column of encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber2 varbinary(128);   
OPEN SYMMETRIC KEY SSN_Key_02  
   DECRYPTION BY ASYMMETRIC KEY SSN_AKey;  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber2  
    = EncryptByKey(Key_GUID('SSN_Key_02'), NationalIDNumber);  
GO  
--Close the key used to encrypt the data.  
CLOSE SYMMETRIC KEY SSN_Key_02;  
--  
--There are two ways to decrypt the stored data.  
--  
--OPTION ONE, using DecryptByKey()  
--1. Open the symmetric key.  
--2. Decrypt the data.  
--3. Close the symmetric key.  
OPEN SYMMETRIC KEY SSN_Key_02  
   DECRYPTION BY ASYMMETRIC KEY SSN_AKey;  
SELECT NationalIDNumber, EncryptedNationalIDNumber2    
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber2))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
CLOSE SYMMETRIC KEY SSN_Key_02;  
--  
--OPTION TWO, using DecryptByKeyAutoAsymKey()  
SELECT NationalIDNumber, EncryptedNationalIDNumber2   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKeyAutoAsymKey ( AsymKey_ID('SSN_AKey') , NULL ,EncryptedNationalIDNumber2))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
