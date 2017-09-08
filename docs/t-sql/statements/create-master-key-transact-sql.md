---
title: CREARE la chiave MASTER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MASTER_KEY_TSQL
- MASTER_KEY_TSQL
- MASTER KEY
- CREATE MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], Database Master Key
- database master key [SQL Server]
- CREATE MASTER KEY statement
- cryptography [SQL Server], Database Master Key
- database master key [SQL Server], creating
ms.assetid: 1710a305-1a4f-48ec-836c-11ffd0356d76
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e051e59ebae464942068521a95a1d5b06389304e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-master-key-transact-sql"></a>CREATE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Crea una chiave master del database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Parallel Data Warehouse  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password'  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse  
  
CREATE MASTER KEY [ ENCRYPTION BY PASSWORD ='password' ]
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 PASSWORD ='*password*'  
 Password utilizzata per crittografare la chiave master nel database. *password* deve soddisfare i requisiti dei criteri password Windows del computer in cui è in esecuzione l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *password* è facoltativo in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] e [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].  
  
## <a name="remarks"></a>Osservazioni  
 La chiave master del database è una chiave simmetrica utilizzata per proteggere le chiavi private dei certificati e le chiavi asimmetriche presenti nel database. Al momento della creazione, la chiave master viene crittografata con l'algoritmoAES_256 e una password specificata dall'utente. In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] viene utilizzato l'algoritmo Triple DES. Per consentire la decrittografia automatica della chiave master, una copia della chiave viene crittografata con la chiave master del servizio e archiviata sia nel database che nel database master. La copia archiviata nel database master viene generalmente aggiornata in modo automatico in seguito a ogni modifica della chiave master. Questa impostazione predefinita può essere modificata utilizzando l'opzione DROP ENCRYPTION BY SERVICE MASTER KEY di [ALTER MASTER KEY](../../t-sql/statements/alter-master-key-transact-sql.md). Per aprire una chiave master non crittografata dalla chiave master del servizio, è necessario utilizzare il [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md) istruzione e una password.  
  
 La colonna is_master_key_encrypted_by_server della vista del catalogo sys.databases nel database master indica se la chiave master del database è crittografata con la chiave master del servizio.  
  
 Le informazioni sulla chiave master del database sono visibili nella vista del catalogo sys.symmetric_keys.  

Per SQL Server e Parallel Data Warehouse, la chiave Master in genere è protetto dalla chiave Master del servizio e la password di almeno uno. In caso di database viene fisicamente spostato in un server diverso (log shipping, il ripristino di backup e così via), il database conterrà una copia della chiave master crittografata dalla chiave Master del servizio server originale (a meno che la crittografia è stato rimosso in modo esplicito utilizzando ALTER MASTER KEY DDL) e una copia crittografata per ogni password specificata durante le operazioni successive ALTER MASTER KEY DDL o CREATE MASTER KEY. Per ripristinare la chiave Master e tutti i dati crittografati con la chiave Master come radice della gerarchia chiave dopo lo spostamento di database, l'utente deve utilizzare istruzione OPEN MASTER KEY utilizzando uno della password utilizzata per proteggere la chiave Master , ripristinare un backup della chiave Master o ripristinare un backup dell'originale chiave Master del servizio nel nuovo server. 

Per [!INCLUDE[ssSDS](../../includes/sssds-md.md)] e [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)], la protezione con password non viene considerata come un meccanismo di sicurezza per evitare uno scenario di perdita di dati in situazioni in cui potrebbe spostare il database da un server a un'altra, come la chiave Master del servizio di protezione per la chiave Master gestito da piattaforma Microsoft Azure. Pertanto, la password della chiave Maser è facoltativa in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] e [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].
  
> [!IMPORTANT]  
>  È consigliabile eseguire il backup della chiave master utilizzando [BACKUP MASTER KEY](../../t-sql/statements/backup-master-key-transact-sql.md) e archiviare il backup in una posizione esterna sicura.  
  
 Le chiavi master del servizio e del database vengono protette mediante l'algoritmo AES-256.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per il database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente crea una chiave master del database per il database corrente. La chiave viene crittografata con la password `23987hxJ#KL95234nl0zBe`.  
  
```  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
GO  
```  

  
## <a name="see-also"></a>Vedere anche  
 [symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [Aprire la chiave MASTER &#40; Transact-SQL &#41;](../../t-sql/statements/open-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [DROP MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-master-key-transact-sql.md)   
 [CLOSE MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/close-master-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  



