---
title: DECRYPTBYPASSPHRASE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECRYPTBYPASSPHRASE
- DECRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], DECRYPTBYPASSPHRASE function
- DECRYPTBYPASSPHRASE function
ms.assetid: ca34b5cd-07b3-4dca-b66a-ed8c6a826c95
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0af2f19acced57d722427c8f341db62dbdb34198
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esegue la decrittografia dei dati crittografati con una passphrase.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *passphrase*  
 Passphrase che sarà usata per generare la chiave per la decrittografia.  
  
 @passphrase  
 È una variabile di tipo **nvarchar**, **char**, **varchar**, o **nchar** che contiene la passphrase che verrà utilizzata per generare la chiave per decrittografia.  
  
 '*testo crittografato*'  
 Testo crittografato da decrittografare.  
  
 @ciphertext  
 È una variabile di tipo **varbinary** che contiene il testo crittografato. Le dimensioni massime sono pari a 8.000 byte.  
  
 *add_authenticator*  
 Indica se un autenticatore è stato crittografato insieme al testo normale. Il valore è 1 se è stato usato un autenticatore. **int**.  
  
 @add_authenticator  
 Indica se un autenticatore è stato crittografato insieme al testo normale. Il valore è 1 se è stato usato un autenticatore. **int**.  
  
 *autenticatore*  
 Dati relativi all'autenticatore. **sysname**.  
  
 @authenticator  
 Variabile contenente i dati da cui derivare un autenticatore.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary** con una dimensione massima di 8.000 byte.  
  
## <a name="remarks"></a>Osservazioni  
 Non sono necessarie autorizzazioni per eseguire questa funzione.  
  
 Restituisce NULL se viene usata una passphrase non corretta o informazioni errate sull'autenticatore.  
  
 La passphrase viene usata per generare una chiave di decrittografia, che non sarà persistente.  
  
 Se è stato incluso un autenticatore al momento della crittografia del testo non crittografato, l'autenticatore deve essere incluso anche in fase di decrittografia. Se il valore dell'autenticatore fornito in fase di decrittografia non corrisponde al valore dell'autenticatore crittografato con i dati, non sarà possibile completare la decrittografia.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene decrittografato il record aggiornato [EncryptByPassPhrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
-- Get the pass phrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
= 'A little learning is a dangerous thing!';  
  
-- Decrypt the encrypted record.  
SELECT CardNumber, CardNumber_EncryptedbyPassphrase   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByPassphrase(@PassphraseEnteredByUser, CardNumber_EncryptedbyPassphrase, 1   
    , CONVERT(varbinary, CreditCardID)))  
    AS 'Decrypted card number' FROM Sales.CreditCard   
    WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  
