---
title: BACKUP CERTIFICATE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DUMP_CERTIFICATE_TSQL
- BACKUP CERTIFICATE
- sql13.swb.exportcertificate.f1
- DUMP CERTIFICATE
- BACKUP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], certificates
- decryption [SQL Server], certificates
- exporting certificates
- certificates [SQL Server], exporting
- BACKUP CERTIFICATE statement
- backing up certificates [SQL Server]
- decryption [SQL Server]
- cryptography [SQL Server], certificates
ms.assetid: 509b9462-819b-4c45-baae-3d2d90d14a1c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1abdb1b1a64f637d1457cec014cf6fbf000f2efc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="backup-certificate-transact-sql"></a>BACKUP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Esporta un certificato in un file.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
BACKUP CERTIFICATE certname TO FILE = 'path_to_file'  
    [ WITH PRIVATE KEY   
      (   
        FILE = 'path_to_private_key_file' ,  
        ENCRYPTION BY PASSWORD = 'encryption_password'   
        [ , DECRYPTION BY PASSWORD = 'decryption_password' ]   
      )   
    ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
BACKUP CERTIFICATE certname TO FILE ='path_to_file'  
      WITH PRIVATE KEY   
      (   
        FILE ='path_to_private_key_file',  
        ENCRYPTION BY PASSWORD ='encryption_password'   
      )   
```  
  
## <a name="arguments"></a>Argomenti  
 *path_to_file*  
 Specifica il percorso completo, nome di file incluso, del file in cui verrà salvato il certificato. Questo parametro può essere un percorso locale o un percorso UNC di rete. L'impostazione predefinita è rappresentata dal percorso della cartella DATA di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *path_to_private_key_file*  
 Specifica il percorso completo, nome di file incluso, del file in cui verrà salvata la chiave privata. Questo parametro può essere un percorso locale o un percorso UNC di rete. L'impostazione predefinita è rappresentata dal percorso della cartella DATA di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *encryption_password*  
 Password utilizzata per crittografare la chiave privata prima di scriverla nel file di backup. Questa password è soggetta ai controlli di complessità delle password.  
  
 *decryption_password*  
 Password utilizzata per decrittografare la chiave privata prima di eseguire il backup della chiave.  
  
## <a name="remarks"></a>Remarks  
 Se la chiave privata è crittografata con una password nel database, è necessario specificare la password di decrittografia.  
  
 Quando si esegue il backup della chiave privata in un file, la crittografia è obbligatoria. La password utilizzata per proteggere il certificato sottoposto a backup non corrisponde alla password utilizzata per crittografare la chiave privata del certificato.  
  
 Per ripristinare un certificato da un backup, usare l'istruzione [CREATE CERTIFICATE](../../t-sql/statements/create-certificate-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL per il certificato ed è necessario conoscere la password utilizzata per crittografare la chiave privata. Se si esegue il backup della sola parte pubblica del certificato, sono richieste alcune autorizzazioni per il certificato ed è necessario che al chiamante non sia stata negata l'autorizzazione VIEW per il certificato.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-exporting-a-certificate-to-a-file"></a>A. Esportazione di un certificato in un file  
 Nell'esempio seguente un certificato viene esportato in un file.  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert';  
GO  
```  
  
### <a name="b-exporting-a-certificate-and-a-private-key"></a>B. Esportazione di un certificato e di una chiave privata  
 Nell'esempio seguente la chiave privata del certificato di cui si esegue il backup verrà crittografata con la password `997jkhUbhk$w4ez0876hKHJH5gh`.  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert'  
    WITH PRIVATE KEY ( FILE = 'c:\storedkeys\sales05key' ,   
    ENCRYPTION BY PASSWORD = '997jkhUbhk$w4ez0876hKHJH5gh' );  
GO  
```  
  
### <a name="c-exporting-a-certificate-that-has-an-encrypted-private-key"></a>C. Esportazione di un certificato con una chiave privata crittografata  
 Nell'esempio seguente la chiave privata del certificato è crittografata nel database ed è necessario decrittografarla con la password `9875t6#6rfid7vble7r`. Quando il certificato viene archiviato nel file di backup, la chiave privata verrà crittografata con la password `9n34khUbhk$w4ecJH5gh`.  
  
```  
BACKUP CERTIFICATE sales09 TO FILE = 'c:\storedcerts\sales09cert'   
    WITH PRIVATE KEY ( DECRYPTION BY PASSWORD = '9875t6#6rfid7vble7r' ,  
    FILE = 'c:\storedkeys\sales09key' ,   
    ENCRYPTION BY PASSWORD = '9n34khUbhk$w4ecJH5gh' );  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)  
  
  

