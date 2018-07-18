---
title: Ripristinare un database protetto con TDE - Parallel Data Warehouse | Documenti Microsoft
description: Utilizzare la procedura seguente per ripristinare un database che verrà crittografato tramite transparent data encryption in Analitica piattaforma Parallel Data Warehouse di System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: a791d4110dc70c506025f8f11fb06b9ba2e5dcb3
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="restore-a-database-protected-by-tde-in-parallel-data-warehouse"></a>Ripristinare un database protetto con TDE in Parallel Data Warehouse
Utilizzare la procedura seguente per ripristinare un database crittografato con la crittografia dati trasparente.  
  
Il [tramite Transparent Data Encryption](transparent-data-encryption.md#using-tde) esempio include il codice per abilitare TDE nel `AdventureWorksPDW2012` database. Il codice seguente continua tale esempio, creando un backup del database sull'accessorio Analitica piattaforma di strumenti analitici originale e quindi ripristinare il certificato e il database in un dispositivo diverso.  
  
Il primo passaggio consiste nel creare un backup del database di origine.  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
Preparazione di SQL Server PDW nuovo TDE tramite la creazione di una chiave master, l'abilitazione della crittografia e la creazione di una credenziale di rete.  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
Gli ultimi due passaggi ricreare il certificato utilizzando la versione originale di SQL Server PDW dei backup. Utilizzare la password utilizzata per la creazione del backup del certificato.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert  
    FROM FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'   
    WITH PRIVATE KEY (FILE = '\\SECURE_SERVER\cert\MyServerCert.key',   
    DECRYPTION BY PASSWORD = '<password>');  
  
RESTORE DATABASE AdventureWorksPDW2012   
    FROM DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>Vedere anche  
[DATABASE DI BACKUP](../t-sql/statements/backup-database-parallel-data-warehouse.md)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md) 
[sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[CREAZIONE DI CERTIFICATI](../t-sql/statements/create-certificate-transact-sql.md)  
[RIPRISTINO DI DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
