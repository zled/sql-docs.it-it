---
title: ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER DATABASE SCOPED CREDENTIAL
- ALTER_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], ALTER DATABASE SCOPED CREDENTIAL statement
ms.assetid: 966b75b5-ca87-4203-8bf9-95c4e00cb0b5
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 91224c6e96fb3ee3962331ec6f378ea9aad1a5b5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-scoped-credential-transact-sql"></a>ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Credenziali con ambito di modifica delle proprietà di un database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *credential_name*  
 Specifica il nome delle credenziali con ambito database che viene modificata.  
  
 IDENTITÀ **='***identity_name***'**  
 Specifica il nome dell'account da utilizzare per la connessione all'esterno del server. Per importare un file dall'archiviazione Blob di Azure, è necessario essere il nome dell'identità `SHARED ACCESS SIGNATURE`.  Per ulteriori informazioni sulle firme di accesso condiviso, vedere [utilizzando di firme di accesso condiviso (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).  
    
  
 SEGRETO **='***secret***'**  
 Specifica il segreto richiesto per l'autenticazione in uscita. *segreto* per importare un file dall'archiviazione Blob di Azure è necessaria. *segreto* può essere facoltativo per altri scopi.   
>  [!WARNING]
>  Il valore della chiave di firma di accesso condiviso potrebbe iniziare con un '?' (punto interrogativo). Quando si usa la chiave di firma di accesso condiviso, è necessario rimuovere il carattere '?'. In caso contrario potrebbero essere bloccate le attività.    
  
## <a name="remarks"></a>Osservazioni  
 Quando un database con ambito delle credenziali viene modificato, i valori della proprietà *identity_name* e *secret* vengono reimpostate. Se l'argomento facoltativo SECRET viene omesso, il valore del segreto archiviato verrà impostato su NULL.  
  
 Il segreto viene crittografato tramite la chiave master del servizio. Se la chiave master del servizio viene rigenerata, il segreto verrà crittografato nuovamente tramite la nuova chiave master del servizio.  
  
 Informazioni sulle credenziali con ambito database sono visibili nella [database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) vista del catalogo.  
  
## <a name="permissions"></a>Permissions  
 È necessario `ALTER` l'autorizzazione per la credenziale.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-password-of-a-database-scoped-credential"></a>A. Credenziali con ambito di modifica della password di un database  
 Nell'esempio seguente viene modificato il segreto archiviato in una credenziale con ambito database chiamata `Saddles`. Le credenziali con ambito database contengono l'account di accesso di Windows `RettigB` e la relativa password. La nuova password viene aggiunta alle credenziali con ambito database tramite la clausola SECRET.  
  
```  
ALTER DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>B. Rimozione della password da una credenziale  
 Nell'esempio seguente la password viene rimossa da una credenziale con ambito database denominata `Frames`. Le credenziali con ambito database contengono account di accesso Windows `Aboulrus8` e una password. Dopo l'istruzione viene eseguita, le credenziali con ambito database avrà una password NULL perché non è specificato l'opzione SECRET.  
  
```  
ALTER DATABASE SCOPED CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

