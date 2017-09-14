---
title: ENCRYPTBYKEY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYKEY_TSQL
- ENCRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- authenticators [SQL Server]
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], ENCRYPTBYKEY function
- ENCRYPTBYKEY function
ms.assetid: 0e11f8c5-f79d-46c1-ab11-b68ef05d6787
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17b9b4aea4916cfb74efbead6d06c830698a4167
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="encryptbykey-transact-sql"></a>ENCRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crittografa dati tramite una chiave simmetrica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EncryptByKey ( key_GUID , { 'cleartext' | @cleartext }  
    [, { add_authenticator | @add_authenticator }  
     , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *key_GUID*  
 È il GUID della chiave da utilizzare per crittografare il *come testo non crittografato*. **uniqueidentifier**.  
  
 '*come testo non crittografato*'  
 Dati da crittografare tramite la chiave.  
  
 @cleartext  
 È una variabile di tipo **nvarchar**, **char**, **varchar**, **binario**, **varbinary**, o **nchar** che contiene i dati che deve essere crittografata con la chiave.  
  
 *add_authenticator*  
 Indica se un autenticatore verrà crittografato con la *come testo non crittografato*. Deve essere 1 se si usa un autenticatore. **int**.  
  
 @add_authenticator  
 Indica se un autenticatore verrà crittografato con la *come testo non crittografato*. Deve essere 1 se si usa un autenticatore. **int**.  
  
 *autenticatore*  
 Dati da cui derivare un autenticatore. **sysname**.  
  
 @authenticator  
 Variabile contenente i dati da cui derivare un autenticatore.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary** con una dimensione massima di 8.000 byte.  
  
 Restituisce NULL se la chiave non è aperta, non esiste o se è una chiave RC4 deprecata e il database non è nel livello di compatibilità 110 o superiore.  
  
## <a name="remarks"></a>Osservazioni  
 EncryptByKey usa una chiave simmetrica. Tale chiave deve essere aperta. Se la chiave simmetrica è già aperta nella sessione corrente, non è necessario aprirla nuovamente nel contesto della query.  
  
 L'autenticatore consente di ridurre la sostituzione di valori interi dei campi crittografati. Si consideri, ad esempio, la tabella seguente contenente dati relativi alle retribuzioni.  
  
|Employee_ID|Standard_Title|Base_Pay|  
|------------------|---------------------|---------------|  
|345|Copy Room Assistant|Fskj%7^edhn00|  
|697|Chief Financial Officer|M0x8900f56543|  
|694|Data Entry Supervisor|Cvc97824%^34f|  
  
 Senza violare la crittografia, un utente malintenzionato è in grado di dedurre informazioni significative dal contesto in cui è archiviato il testo crittografato. Poiché la retribuzione del ruolo Chief Financial Officer è maggiore di quella del ruolo Copy Room Assistant, è necessario che il valore crittografato come M0x8900f56543 sia maggiore di quello crittografato come Fskj%7^edhn00. In questo caso, qualsiasi utente che disponga dell'autorizzazione ALTER per la tabella è in grado di aumentare la retribuzione del ruolo Copy Room Assistant sostituendo i dati nel campo Base_Pay corrispondente con una copia dei dati archiviati nel campo Base_Pay relativo al ruolo Chief Financial Officer. Questo attacco di sostituzione dell'intero valore è quindi in grado di agire nonostante la crittografia.  
  
 Gli attacchi basati sulla sostituzione dell'intero valore possono essere ostacolati tramite l'aggiunta di informazioni contestuali al testo normale prima di procedere alla sua crittografia. Tali informazioni sono usate per verificare che i dati in formato testo normale non siano stati spostati.  
  
 Se per la crittografia dei dati è specificato un parametro di autenticazione, è necessario usare lo stesso autenticatore per decrittografare i dati tramite DecryptByKey. Al momento dell'esecuzione della crittografia, un hash dell'autenticatore viene crittografato insieme al testo normale. Durante la fase di decrittografia, è necessario passare lo stesso autenticatore a DecryptByKey. Se gli autenticatori non corrispondono, la decrittografia non è possibile. Questo indica che il valore è stato spostato successivamente all'esecuzione della crittografia. È consigliabile usare una colonna contenente un valore univoco e non modificabile come autenticatore. Se il valore dell'autenticatore viene modificato, si può perdere l'accesso ai dati.  
  
 La crittografia e decrittografia simmetriche sono operazioni relativamente veloci, ideali per operazioni basate su quantità elevate di dati.  
  
> [!IMPORTANT]  
>  L'uso delle funzioni di crittografia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'impostazione ANSI_PADDING OFF può provocare la perdita di dati a causa delle conversioni implicite. Per ulteriori informazioni relative ad ANSI_PADDING, vedere [SET ANSI_PADDING &#40; Transact-SQL &#41; ](../../t-sql/statements/set-ansi-padding-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 La funzionalità illustrata negli esempi seguenti si basa sulle chiavi e certificati creati in [procedura: crittografare una colonna di dati](../../relational-databases/security/encryption/encrypt-a-column-of-data.md).  
  
### <a name="a-encrypting-a-string-with-a-symmetric-key"></a>A. Crittografia di una stringa tramite una chiave simmetrica  
 Nell'esempio seguente viene aggiunta una colonna alla tabella `Employee`, quindi viene crittografato il valore del numero di previdenza sociale archiviato nella colonna `NationalIDNumber`.  
  
```  
USE AdventureWorks2012;  
GO  
  
-- Create a column in which to store the encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber varbinary(128);   
GO  
  
-- Open the symmetric key with which to encrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
  
-- Encrypt the value in column NationalIDNumber with symmetric key  
-- SSN_Key_01. Save the result in column EncryptedNationalIDNumber.  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber  
    = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
GO  
```  
  
### <a name="b-encrypting-a-record-together-with-an-authentication-value"></a>B. Crittografia di un record assieme a un valore di autenticazione  
  
```  
USE AdventureWorks2012;  
  
-- Create a column in which to store the encrypted data.  
ALTER TABLE Sales.CreditCard.   
    ADD CardNumber_Encrypted varbinary(128);   
GO  
  
-- Open the symmetric key with which to encrypt the data.  
OPEN SYMMETRIC KEY CreditCards_Key11  
    DECRYPTION BY CERTIFICATE Sales09;  
  
-- Encrypt the value in column CardNumber with symmetric   
-- key CreditCards_Key11.  
-- Save the result in column CardNumber_Encrypted.    
UPDATE Sales.CreditCard  
SET CardNumber_Encrypted = EncryptByKey(Key_GUID('CreditCards_Key11'),   
    CardNumber, 1, CONVERT( varbinary, CreditCardID) );  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DECRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [HASHBYTES &#40; Transact-SQL &#41;](../../t-sql/functions/hashbytes-transact-sql.md)  
  
  