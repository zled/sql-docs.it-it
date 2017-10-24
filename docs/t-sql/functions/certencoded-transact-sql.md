---
title: CERTENCODED (Transact-SQL) | Documenti Microsoft
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
- CERTENCODED
- CERTENCODED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTENCODED
ms.assetid: 677a0719-7b9a-4f0b-bc61-41634563f924
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7596187fc97c0afd1df49f9de1e7ed168de5bcb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="certencoded-transact-sql"></a>CERTENCODED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce la parte pubblica di un certificato in formato binario. Questa funzione accetta un ID certificato e restituisce il certificato codificato. Il risultato binario può essere passato a **CREATE CERTIFICATE... CON binario** per creare un nuovo certificato.
  
## <a name="syntax"></a>Sintassi  
  
```sql
CERTENCODED ( cert_id )  
```  
  
## <a name="arguments"></a>Argomenti  
*cert_id*  
È il **certificate_id** del certificato. Questa opzione è disponibile da Sys. Certificates o utilizzando il [CERT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) (funzione). *cert_id* è di tipo **int**
  
## <a name="return-types"></a>Tipi restituiti
**varbinary**
  
## <a name="remarks"></a>Osservazioni  
**CERTENCODED** e **CERTPRIVATEKEY** vengono utilizzate insieme per restituire parti diverse di un certificato in formato binario.
  
## <a name="permissions"></a>Permissions  
**CERTENCODED** è disponibile al pubblico.
  
## <a name="examples"></a>Esempi  
  
### <a name="simple-example"></a>Esempio semplice  
Nell'esempio seguente viene creato un certificato denominato `Shipping04` e quindi utilizza il **CERTENCODED** funzione per restituire la codifica binaria del certificato.
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE CERTIFICATE Shipping04   
ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20161031';  
GO  
SELECT CERTENCODED(CERT_ID('Shipping04'));  
  
```  
  
### <a name="b-copying-a-certificate-to-another-database"></a>B. Copia di un certificato in un altro database  
Nell'esempio più complesso seguente vengono creati due database `SOURCE_DB` e `TARGET_DB`. L'obiettivo consiste nel creare un certificato in `SOURCE_DB` e nel copiarlo in `TARGET_DB` e quindi nel dimostrare che è possibile decrittografare i dati crittografati in `SOURCE_DB` in `TARGET_DB` utilizzando la copia del certificato.
  
Per creare l'ambiente di esempio, creare i database `SOURCE_DB` e `TARGET_DB` e una chiave master in ognuno. Creare quindi un certificato in `SOURCE_DB`.
  
```sql
USE master;  
GO  
CREATE DATABASE SOURCE_DB;  
GO  
USE SOURCE_DB;  
GO  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0URCE_DB KEY Pa$$W0rd';  
GO  
CREATE DATABASE TARGET_DB;  
GO  
USE TARGET_DB  
GO  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Pa$$W0rd in TARGET_DB';  
GO  
  
-- Create a certificate in SOURCE_DB  
USE SOURCE_DB;  
GO  
CREATE CERTIFICATE SOURCE_CERT WITH SUBJECT = 'SOURCE_CERTIFICATE';  
GO  
```  
  
Estrarre ora la descrizione binaria del certificato.
  
```sql
DECLARE @CERTENC VARBINARY(MAX);  
DECLARE @CERTPVK VARBINARY(MAX);  
SELECT @CERTENC = CERTENCODED(CERT_ID('SOURCE_CERT'));  
SELECT @CERTPVK = CERTPRIVATEKEY(CERT_ID('SOURCE_CERT'),  
       'CertEncryptionPa$$word');  
SELECT @CERTENC AS BinaryCertificate;  
SELECT @CERTPVK AS EncryptedBinaryCertificate;  
GO  
```  
  
Creare il certificato duplicato nel database `TARGET_DB`. È necessario modificare il codice seguente, inserendo i due valori binari restituiti nel passaggio precedente.
  
```sql
-- Create the duplicate certificate in the TARGET_DB database  
USE TARGET_DB  
GO  
CREATE CERTIFICATE TARGET_CERT  
FROM BINARY = <insert the binary value of the @CERTENC variable>  
WITH PRIVATE KEY (  
BINARY = <insert the binary value of the @CERTPVK variable>  
, DECRYPTION BY PASSWORD = 'CertEncryptionPa$$word');  
-- Compare the certificates in the two databases  
-- The two certificates should be the same   
-- except for name and (possibly) the certificate_id  
SELECT * FROM SOURCE_DB.sys.certificates  
UNION  
SELECT * FROM TARGET_DB.sys.certificates;  
```  
  
Il codice seguente eseguito come singolo batch dimostra che è possibile decrittografare i dati crittografati in `SOURCE_DB` in `TARGET_DB`.
  
```sql
USE SOURCE_DB;  
  
DECLARE @CLEARTEXT nvarchar(100);  
DECLARE @CIPHERTEXT varbinary(8000);  
DECLARE @UNCIPHEREDTEXT_Source nvarchar(100);  
SET @CLEARTEXT = N'Hello World';  
SET @CIPHERTEXT = ENCRYPTBYCERT(CERT_ID('SOURCE_CERT'), @CLEARTEXT);  
SET @UNCIPHEREDTEXT_Source =   
    DECRYPTBYCERT(CERT_ID('SOURCE_CERT'), @CIPHERTEXT)  
-- Encryption and decryption result in SOURCE_DB  
SELECT @CLEARTEXT AS SourceClearText, @CIPHERTEXT AS SourceCipherText,   
       @UNCIPHEREDTEXT_Source AS SourceDecryptedText;  
  
-- SWITCH DATABASE  
USE TARGET_DB;  
  
DECLARE @UNCIPHEREDTEXT_Target nvarchar(100);  
SET @UNCIPHEREDTEXT_Target = DECRYPTBYCERT(CERT_ID('TARGET_CERT'), @CIPHERTEXT);  
-- Encryption and decryption result in TARGET_DB  
SELECT @CLEARTEXT AS ClearTextInTarget, @CIPHERTEXT AS CipherTextInTarget, @UNCIPHEREDTEXT_Target AS DecriptedTextInTarget;   
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[CERTPRIVATEKEY &#40; Transact-SQL &#41;](../../t-sql/functions/certprivatekey-transact-sql.md)  
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  

