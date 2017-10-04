---
title: DROP DATABASE ENCRYPTION KEY (Transact-SQL) | Documenti Microsoft
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
- DROP DATABASE ENCRYPTION KEY
- DROP_DATABASE_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key, drop
- DROP DATABASE ENCRYPTION KEY statement
ms.assetid: 9231bd89-75e1-45c4-b4c8-13f08695af68
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7ccfe5c20c56006a62cd7aee8cc14d9d2d58011d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-database-encryption-key-transact-sql"></a>DROP DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Elimina una chiave di crittografia del database utilizzata per la crittografia trasparente del database. Per ulteriori informazioni sulla crittografia trasparente del database, vedere [Transparent Data Encryption &#40; Transparent Data Encryption &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
> [!IMPORTANT]  
>  Il backup del certificato che protegge la chiave di crittografia del database deve essere conservato anche se la crittografia non è più abilitata in un database. Anche se il database non viene più crittografato, è possibile che parti del log delle transazioni restino comunque protette e che il certificato sia necessario per alcune operazioni per l'esecuzione del backup completo del database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DROP DATABASE ENCRYPTION KEY  
```  
  
## <a name="remarks"></a>Osservazioni  
 Se il database è crittografato, è necessario innanzitutto rimuovere la crittografia dal database utilizzando l'istruzione ALTER DATABASE. Attendere il completamento della decrittografia prima di rimuovere la chiave di crittografia del database. Per ulteriori informazioni sull'istruzione ALTER DATABASE, vedere [opzioni ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md). Per visualizzare lo stato del database, utilizzare il [Sys.dm database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) vista a gestione dinamica.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per il database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimossa la crittografia del database e viene eliminata la relativa chiave di crittografia.  
  
```  
ALTER DATABASE AdventureWorks2012  
SET ENCRYPTION OFF;  
GO  
/* Wait for decryption operation to complete, look for a   
value of  1 in the query below. */  
SELECT encryption_state  
FROM sys.dm_database_encryption_keys;  
GO  
USE AdventureWorks2012;  
GO  
DROP DATABASE ENCRYPTION KEY;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente rimuove la crittografia TDE e quindi inserisce la chiave di crittografia del database.  
  
```  
ALTER DATABASE AdventureWorksPDW2012  
    SET ENCRYPTION OFF;  
GO  
/* Wait for decryption operation to complete, look for a   
value of  1 in the query below. */  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
           ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM  dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;   
GO  
USE AdventureWorksPDW2012;  
GO  
DROP DATABASE ENCRYPTION KEY;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Crittografia di SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Chiavi di crittografia del database e di SQL Server &#40;Motore di database&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREARE una chiave di crittografia del DATABASE &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
  
  


