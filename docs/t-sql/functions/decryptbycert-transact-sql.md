---
title: DECRYPTBYCERT (Transact-SQL) | Documenti Microsoft
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
- DecryptByCert_TSQL
- DECRYPTBYCERT
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], decryption
- decryption [SQL Server], certificates
- DECRYPTBYCERT function
ms.assetid: 4950d787-40fa-4e26-bce8-2cb2ceca12fb
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ebdc328e49635af823cd64e8539ee5b7cfa95c76
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbycert-transact-sql"></a>DECRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Decrittografa dati tramite la chiave privata di un certificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DecryptByCert ( certificate_ID , { 'ciphertext' | @ciphertext }   
    [ , { 'cert_password' | @cert_password } ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *certificate_ID*  
 ID di un certificato nel database. *certificato*ID è **int**.  
  
 *testo crittografato*  
 Stringa di dati crittografata tramite la chiave pubblica del certificato.  
  
 @ciphertext  
 È una variabile di tipo **varbinary** che contiene dati che sono stati crittografati con il certificato.  
  
 *cert_password*  
 Password usata per crittografare la chiave privata del certificato. Deve essere Unicode.  
  
 @cert_password  
 È una variabile di tipo **nchar** o **nvarchar** che contiene la password utilizzata per crittografare la chiave privata del certificato. Deve essere Unicode.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary** con una dimensione massima di 8.000 byte.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione decrittografa dati tramite la chiave privata di un certificato. Le trasformazioni di crittografia tramite chiavi asimmetriche richiedono una quantità elevata di risorse. Di conseguenza, EncryptByCert e DecryptByCert non sono adatte per le normali procedure di crittografia di dati utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per il certificato.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono selezionate le righe presenti in `[AdventureWorks2012].[ProtectedData04]` contrassegnate come `data encrypted by certificate JanainaCert02` e viene decrittografato il testo crittografato tramite la chiave privata del certificato `JanainaCert02`, di cui viene prima eseguita la decrittografia tramite la password `pGFD4bb925DGvbd2439587y` del certificato. I dati decrittografati vengono convertiti da **varbinary** a **nvarchar**.  
  
```  
SELECT convert(nvarchar(max), DecryptByCert(Cert_Id('JanainaCert02'),  
    ProtectedData, N'pGFD4bb925DGvbd2439587y'))  
FROM [AdventureWorks2012].[ProtectedData04]   
WHERE Description   
    = N'data encrypted by certificate '' JanainaCert02''';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ENCRYPTBYCERT &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [Istruzione ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

