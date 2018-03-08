---
title: CREARE una chiave di crittografia del DATABASE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.prod_service: pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_ENCRYPTION_KEY_TSQL
- ENCRYPTION_KEY_TSQL
- sql13.swb.dbencryptionkeyo.f1
- ENCRYPTION KEY
- DATABASE ENCRYPTION KEY
- CREATE_DATABASE_ENCRYPTION_KEY_TSQL
- CREATE DATABASE ENCRYPTION KEY
- sql13.swb.dbencryptionkeyg.f1
- CREATE DATABASE ENCRYPTION
- CREATE_DATABASE_ENCRYPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key
- CREATE DATABASE ENCRYPTION KEY statement
- database encryption key, create
ms.assetid: 2ee95a32-5140-41bd-9ab3-a947b9990688
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b108a5cddba7052d177760374d8c5047b28fb25c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-database-encryption-key-transact-sql"></a>CREATE DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

 Crea una chiave di crittografia usata per crittografare in modo trasparente un database. Per ulteriori informazioni sulla crittografia trasparente del database, vedere [Transparent Data Encryption &#40; Transparent Data Encryption &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY  }  
Specifica l'algoritmo di crittografia utilizzato per la chiave di crittografia.   
>  [!NOTE]
>    A partire da SQL Server 2016, tutti gli algoritmi diversi da AES_128, AES_192 e AES_256 sono deprecati. Per usare algoritmi meno recenti (sconsigliato), è necessario impostare il database sul livello di compatibilità del database 120 o su uno inferiore.  
  
CRITTOGRAFIA nome_componente_crittografia certificato SERVER  
Specifica il nome del componente di crittografia utilizzato per crittografare la chiave di crittografia del database.  
  
ENCRYPTION BY SERVER ASYMMETRIC KEY nome_componente_crittografia  
Specifica il nome della chiave asimmetrica utilizzata per crittografare la chiave di crittografia del database. Per crittografare la chiave di crittografia del database con una chiave asimmetrica, è necessario che quest'ultima risieda in un provider EKM (Extensible Key Management).  
  
## <a name="remarks"></a>Osservazioni  
È necessaria una chiave di crittografia del database, prima di un database può essere crittografato utilizzando *crittografia trasparente del Database* (TDE). Crittografandolo in modo trasparente, l'intero database viene crittografato a livello di file, in assenza di qualunque modifica particolare del codice. La chiave asimmetrica o il certificato utilizzato per crittografare la chiave di crittografia del database deve essere archiviata nel database di sistema master.  
  
Le istruzioni sulla crittografia del database sono consentite solo sui database utente.  
  
Non è possibile esportare dal database la relativa chiave di crittografia. È disponibile solo per il sistema, per gli utenti con autorizzazioni di debug per il server e per gli utenti che hanno accesso ai certificati utilizzati per crittografare e decrittografare la chiave di crittografia del database.  
  
Non è necessario rigenerare la chiave di crittografia del database in caso di modifica del proprietario del database (dbo).  
  
Una chiave di crittografia del database viene creata automaticamente un [!INCLUDE[ssSDS](../../includes/sssds-md.md)] database. Non è necessario creare una chiave utilizzando l'istruzione CREATE DATABASE ENCRYPTION KEY.  
  
## <a name="permissions"></a>Permissions  
Sono necessarie l'autorizzazione CONTROL per il database e l'autorizzazione VIEW DEFINITION per la chiave asimmetrica o il certificato utilizzato per crittografare la chiave di crittografia del database.  
  
## <a name="examples"></a>Esempi  
Per ulteriori esempi sull'utilizzo di Transparent Data Encryption, vedere [Transparent Data Encryption &#40; Transparent Data Encryption &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md), [Abilitare TDE in SQL Server con EKM](../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md), e [Extensible Key Management con l'insieme di credenziali chiave di Azure &#40; SQL Server &#41; ](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
Nell'esempio seguente viene creata una chiave di crittografia del database tramite l'algoritmo `AES_256` e tale chiave viene quindi protetta con un certificato denominato `MyServerCert`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
[Crittografia di SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
[Chiavi di crittografia del database e di SQL Server &#40;Motore di database&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
[Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
[Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
[ALTER DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
[DROP DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
[sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
    
