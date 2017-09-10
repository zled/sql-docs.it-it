---
title: ALTER DATABASE ENCRYPTION KEY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_ENCRYPTION_KEY_TSQL
- ALTER DATABASE ENCRYPTION
- ALTER_DATABASE_ENCRYPTION_TSQL
- ALTER DATABASE ENCRYPTION KEY
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key, alter
- ALTER DATABASE ENCRYPTION KEY
ms.assetid: f88dac4b-efe0-47ed-9808-972a4381377e
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 006862850eebb2db1d3f256ca5556016cdb02ab2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-encryption-key-transact-sql"></a>ALTER DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Modifica una chiave di crittografia e ne certifica l'utilizzo per crittografare in modo trasparente un database. Per ulteriori informazioni sulla crittografia trasparente del database, vedere [Transparent Data Encryption &#40; Transparent Data Encryption &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
ALTER DATABASE ENCRYPTION KEY  
      REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   |  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER DATABASE ENCRYPTION KEY  
    {  
      {  
        REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
        [ ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name ]  
      }  
      |  
      ENCRYPTION BY SERVER   CERTIFICATE Encryptor_Name    
    }  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
 Specifica l'algoritmo di crittografia utilizzato per la chiave di crittografia.  
  
 CRITTOGRAFIA del certificato del SERVER *nome_componente_crittografia*  
 Specifica il nome del certificato utilizzato per crittografare la chiave di crittografia del database.  
  
 ENCRYPTION BY SERVER ASYMMETRIC KEY nome_componente_crittografia  
 Specifica il nome della chiave asimmetrica utilizzata per crittografare la chiave di crittografia del database.  
  
## <a name="remarks"></a>Osservazioni  
 La chiave asimmetrica o il certificato utilizzato per crittografare la chiave di crittografia del database deve essere archiviata nel database di sistema master.  
  
 Non è necessario rigenerare la chiave di crittografia del database in caso di modifica del proprietario del database (dbo).  
  
 Dopo che una chiave di crittografia del database è stata modificata due volte, è necessario eseguire un backup del log prima che sia possibile modificare nuovamente la chiave di crittografia del database.  
  
## <a name="permissions"></a>Permissions  
 Sono necessarie l'autorizzazione CONTROL per il database e l'autorizzazione VIEW DEFINITION per la chiave asimmetrica o il certificato utilizzato per crittografare la chiave di crittografia del database.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente illustra come modificare la chiave di crittografia del database per utilizzare l'algoritmo `AES_256`.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER DATABASE ENCRYPTION KEY  
REGENERATE WITH ALGORITHM = AES_256;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'esempio seguente illustra come modificare la chiave di crittografia del database per utilizzare l'algoritmo `AES_256`.  
  
```  
-- Uses AdventureWorks  
  
ALTER DATABASE ENCRYPTION KEY  
REGENERATE WITH ALGORITHM = AES_256;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Crittografia di SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Chiavi di crittografia del database e di SQL Server &#40;Motore di database&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREARE una chiave di crittografia del DATABASE &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
 [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
  
  


