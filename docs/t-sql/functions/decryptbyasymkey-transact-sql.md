---
title: DECRYPTBYASYMKEY (Transact-SQL) | Documenti Microsoft
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
- DECRYPTBYASYMKEY
- DECRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], DECRYPTBYASYMKEY function
- DECRYPTBYASYMKEY function
- decryption [SQL Server], asymmetric keys
ms.assetid: d9ebcd30-f01c-4cfe-b95e-ffe6ea13788b
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7196e7eedf5d1a808853df55259fcee1891c345
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbyasymkey-transact-sql"></a>DECRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Decrittografa i dati con una chiave asimmetrica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DecryptByAsymKey (Asym_Key_ID , { 'ciphertext' | @ciphertext }   
    [ , 'Asym_Key_Password' ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Asym_Key_ID*  
 ID di una chiave asimmetrica nel database. *Asym_Key_ID* è **int**.  
  
 *testo crittografato*  
 Stringa di dati che è stata crittografata con la chiave asimmetrica.  
  
 @ciphertext  
 È una variabile di tipo **varbinary** che contiene dati che sono stati crittografati con la chiave asimmetrica.  
  
 *Asym_Key_Password*  
 Password utilizzata per crittografare la chiave asimmetrica nel database.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary** con una dimensione massima di 8.000 byte.  
  
## <a name="remarks"></a>Osservazioni  
 La crittografia/decrittografia con chiave asimmetrica è molto costosa rispetto alla crittografia/decrittografia con chiave simmetrica. Non è consigliabile utilizzare una chiave asimmetrica quando si lavora con set di dati di grandi dimensioni, ad esempio i dati utente contenuti nelle tabelle.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per la chiave asimmetrica.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene decrittografato il testo crittografato con la chiave asimmetrica `JanainaAsymKey02`, archiviata in `AdventureWorks2012.ProtectedData04`. I dati restituiti vengono decrittografati tramite la chiave asimmetrica `JanainaAsymKey02`, che è stata a sua volta decrittografata con la password `pGFD4bb925DGvbd2439587y`. Il testo non crittografato verrà convertito nel tipo **nvarchar**.  
  
```  
SELECT CONVERT(nvarchar(max),  
    DecryptByAsymKey( AsymKey_Id('JanainaAsymKey02'),   
    ProtectedData, N'pGFD4bb925DGvbd2439587y' ))   
AS DecryptedData   
FROM [AdventureWorks2012].[Sales].[ProtectedData04]   
WHERE Description = N'encrypted by asym key''JanainaAsymKey02''';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ENCRYPTBYASYMKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

