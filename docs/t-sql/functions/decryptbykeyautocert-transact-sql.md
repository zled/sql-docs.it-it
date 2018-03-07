---
title: DECRYPTBYKEYAUTOCERT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/09/2015
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOCERT
- DECRYPTBYKEYAUTOCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DECRYPTBYKEYAUTOCERT function
ms.assetid: 6b45fa2e-ffaa-46f7-86ff-5624596eda4a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9aca90f988ae2d12d9a7c26f01673530b1a07f4b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="decryptbykeyautocert-transact-sql"></a>DECRYPTBYKEYAUTOCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue la decrittografia tramite una chiave simmetrica decrittografata automaticamente con un certificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DecryptByKeyAutoCert ( cert_ID , cert_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *cert_ID*  
 ID del certificato usato per proteggere la chiave simmetrica. *cert_ID* è **int**.  
  
 *cert_password*  
 Password che protegge la chiave privata del certificato. Può essere NULL se la chiave privata è protetta dalla chiave master del database. *cert_password* è **nvarchar**.  
  
 '*testo crittografato*'  
 Dati crittografati con la chiave. *testo crittografato* è **varbinary**.  
  
 @ciphertext  
 È una variabile di tipo **varbinary** che contiene dati che è stati crittografati con la chiave.  
  
 *add_authenticator*  
 Indica se un autenticatore è stato crittografato insieme al testo normale. Deve essere lo stesso valore passato a EncryptByKey durante la crittografia dei dati. È **1** se è stato utilizzato un autenticatore. *add_authenticator* è **int**.  
  
 @add_authenticator  
 Indica se un autenticatore è stato crittografato insieme al testo normale. Deve corrispondere al valore passato a EncryptByKey durante la crittografia dei dati.  
  
 *autenticatore*  
 Dati da cui generare un autenticatore. Deve corrispondere al valore specificato per EncryptByKey. *autenticatore* è **sysname**.  
  
 @authenticator  
 Variabile contenente i dati da cui generare un autenticatore. Deve corrispondere al valore specificato per EncryptByKey.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary** con una dimensione massima di 8.000 byte.  
  
## <a name="remarks"></a>Osservazioni  
 DecryptByKeyAutoCert include le funzionalità di OPEN SYMMETRIC KEY e DecryptByKey. In un'unica operazione consente di decrittografare una chiave simmetrica e di usarla per la decrittografia del testo.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW DEFINITION per la chiave simmetrica e l'autorizzazione CONTROL per il certificato.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come usare `DecryptByKeyAutoCert` per semplificare il codice che esegue la decrittografia. Questo codice deve essere eseguito in un database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] per cui non è presente già una chiave master.  
  
```  
--Create the keys and certificate.  
USE AdventureWorks2012;  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
CREATE CERTIFICATE HumanResources037   
   WITH SUBJECT = 'Sammamish HR',   
   EXPIRY_DATE = '10/31/2009';  
CREATE SYMMETRIC KEY SSN_Key_01 WITH ALGORITHM = DES  
    ENCRYPTION BY CERTIFICATE HumanResources037;  
GO  
----Add a column of encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber varbinary(128);   
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037 ;  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber  
    = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
GO  
--  
--Close the key used to encrypt the data.  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--There are two ways to decrypt the stored data.  
--  
--OPTION ONE, using DecryptByKey()  
--1. Open the symmetric key  
--2. Decrypt the data  
--3. Close the symmetric key  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
SELECT NationalIDNumber, EncryptedNationalIDNumber    
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--OPTION TWO, using DecryptByKeyAutoCert()  
SELECT NationalIDNumber, EncryptedNationalIDNumber   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKeyAutoCert ( cert_ID('HumanResources037') , NULL ,EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
