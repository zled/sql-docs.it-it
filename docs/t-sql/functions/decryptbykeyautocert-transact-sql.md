---
title: DECRYPTBYKEYAUTOCERT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/09/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0842000cd08e3ca82dab181f32ae96f4a0280d5d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# DECRYPTBYKEYAUTOCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue la decrittografia tramite una chiave simmetrica decrittografata automaticamente con un certificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Sintassi  
  
```  
  
DecryptByKeyAutoCert ( cert_ID , cert_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
## Argomenti  
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
  
## Tipi restituiti  
 **varbinary** con una dimensione massima di 8.000 byte.  
  
## Osservazioni  
 DecryptByKeyAutoCert include le funzionalità di OPEN SYMMETRIC KEY e DecryptByKey. In un'unica operazione consente di decrittografare una chiave simmetrica e di usarla per la decrittografia del testo.  
  
## Permissions  
 È richiesta l'autorizzazione VIEW DEFINITION per la chiave simmetrica e l'autorizzazione CONTROL per il certificato.  
  
## Esempi  
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
  
## Vedere anche  
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

