---
title: KEY_NAME (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KEY_NAME_TSQL
- KEY_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- KEY_NAME function
ms.assetid: 7b693e5d-2325-4bf9-9b45-ad6a23374b41
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c248e100d97150c7613ec8db7f0e7c97180ee817
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="keyname-transact-sql"></a>KEY_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il nome della chiave simmetrica dal GUID di una chiave simmetrica o da un testo crittografato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
KEY_NAME ( ciphertext | key_guid )   
```  
  
## <a name="arguments"></a>Argomenti  
 *testo crittografato*  
 Testo crittografato dalla chiave simmetrica. *messaggio cifrato* è di tipo **varbinary (8000)**.  
  
 *key_guid*  
 GUID della chiave simmetrica. *key_guid* è di tipo **uniqueidentifier**.  
  
## <a name="returned-types"></a>Tipi restituiti  
 **varchar (128)**  
  
## <a name="permissions"></a>Permissions  
 A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] la visibilità dei metadati è limitata alle entità a sicurezza diretta di cui l'utente è proprietario o per le quali dispone di autorizzazioni. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-the-name-of-a-symmetric-key-using-the-keyguid"></a>A. Visualizzazione del nome di una chiave simmetrica mediante key_guid  
 Il **master** database contiene una chiave simmetrica denominata # # MS_ServiceMasterKey # #. Nell'esempio seguente il GUID di tale chiave viene recuperato dalla vista a gestione dinamica sys.symmetric_keys e viene assegnato a una variabile che viene quindi passata alla funzione KEY_NAME per illustrare come restituire il nome corrispondente al GUID.  
  
```  
USE master;  
GO  
DECLARE @guid uniqueidentifier ;  
SELECT @guid = key_guid FROM sys.symmetric_keys  
WHERE name = '##MS_ServiceMasterKey##' ;  
-- Demonstration of passing a GUID to KEY_NAME to receive a name  
SELECT KEY_NAME(@guid) AS [Name of Key];  
```  
  
### <a name="b-displaying-the-name-of-a-symmetric-key-using-the-cipher-text"></a>B. Visualizzazione del nome di una chiave simmetrica mediante il testo crittografato  
 Nell'esempio seguente viene illustrato l'intero processo di creazione di una chiave simmetrica e popolamento di una tabella con i dati. Nell'esempio viene quindi mostrata la restituzione del nome della chiave da KEY_NAME quando viene passato il testo crittografato.  
  
```  
-- Create a symmetric key  
CREATE SYMMETRIC KEY TestSymKey   
   WITH ALGORITHM = AES_128,  
   KEY_SOURCE = 'The square of the hypotenuse is equal to the sum of the squares of the sides',  
   IDENTITY_VALUE = 'Pythagoras'  
   ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y' ;  
GO  
-- Create a table for the demonstration  
CREATE TABLE DemoKey  
(IDCol int IDENTITY PRIMARY KEY,  
SecretCol varbinary(256) NOT NULL)  
GO  
-- Open the symmetric key if not already open  
OPEN SYMMETRIC KEY TestSymKey   
    DECRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y';  
GO  
-- Insert a row into the DemoKey table  
DECLARE @key_GUID uniqueidentifier;  
SELECT @key_GUID = key_guid FROM sys.symmetric_keys  
WHERE name LIKE 'TestSymKey' ;  
INSERT INTO DemoKey(SecretCol)  
VALUES ( ENCRYPTBYKEY (@key_GUID, 'EncryptedText'))  
GO  
-- Verify the DemoKey data  
SELECT * FROM DemoKey;  
GO  
-- Decrypt the data  
DECLARE @ciphertext varbinary(256);  
SELECT @ciphertext = SecretCol  
FROM DemoKey WHERE IDCol = 1 ;  
SELECT CAST (  
DECRYPTBYKEY( @ciphertext)  
AS varchar(100) ) AS SecretText ;  
-- Use KEY_NAME to view the name of the key  
SELECT KEY_NAME(@ciphertext) AS [Name of Key] ;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [ENCRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEYAUTOASYMKEY &#40; Transact-SQL &#41;](../../t-sql/functions/decryptbykeyautoasymkey-transact-sql.md)  
  
  

