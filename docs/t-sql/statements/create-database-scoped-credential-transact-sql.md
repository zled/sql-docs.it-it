---
title: CREARE le CREDENZIALI nell'ambito del DATABASE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE SCOPED CREDENTIAL
- DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_TSQL
- CREATE_DATABASE_SCOPED_CREDENTIAL
- CREATE_DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL
helpviewer_keywords:
- DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], DATABASE SCOPED CREDENTIAL statement
ms.assetid: fe830577-11ca-44e5-953b-2d589d54d045
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4dff68e0c4e50a755ec058602bd61208ccd9b7de
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-database-scoped-credential-transact-sql"></a>CREARE le CREDENZIALI nell'ambito del DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Crea una credenziale di database. Credenziali del database non sono mappata a un utente di account di accesso o database di server. Le credenziali viene utilizzata dal database per accedere al percorso esterno ogni volta che il database viene eseguita un'operazione che richiede l'accesso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
 
CREATE DATABASE SCOPED CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *credential_name*  
 Specifica il nome delle credenziali con ambito database da creare. *credential_name* non può iniziare con il simbolo di cancelletto (#). perché tale simbolo viene utilizzato per le credenziali di sistema.  
  
 IDENTITÀ **='***identity_name***'**  
 Specifica il nome dell'account da utilizzare per la connessione all'esterno del server. Per importare un file dall'archiviazione Blob di Azure, è necessario essere il nome dell'identità `SHARED ACCESS SIGNATURE`.  Per ulteriori informazioni sulle firme di accesso condiviso, vedere [utilizzando di firme di accesso condiviso (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).  
  
 SEGRETO **='***secret***'**  
 Specifica il segreto richiesto per l'autenticazione in uscita. `SECRET`è necessario importare un file dall'archiviazione Blob di Azure.   
>  [!WARNING]
>  Il valore della chiave di firma di accesso condiviso potrebbe iniziare con un '?' (punto interrogativo). Quando si usa la chiave di firma di accesso condiviso, è necessario rimuovere il carattere '?'. In caso contrario potrebbero essere bloccate le attività.  
  
## <a name="remarks"></a>Osservazioni  
 Una credenziale con ambito database è un record contenente le informazioni di autenticazione necessarie per connettersi a una risorsa all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La maggior parte delle credenziali include un utente e una password di Windows.  
  
 Prima di creare un database di credenziali con ambito, il database deve avere una chiave master per proteggere le credenziali. Per altre informazioni, vedere [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md).  
  
 Se IDENTITY è un utente di Windows, il segreto può essere la password. Il segreto viene crittografato con la chiave master del servizio. Se la chiave master del servizio viene rigenerata, il segreto viene ricrittografato con la nuova chiave master del servizio.  
   
 Informazioni sulle credenziali con ambito database sono visibili nella [database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) vista del catalogo.  
  
 
 Hereare credenziali con ambito di alcune applicazioni di database:  
  
- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]utilizza una credenziale con ambito database per accedere a cluster Hadoop protetto con Kerberos con PolyBase o archiviazione blob di Azure non è pubblica. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).  

- [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]utilizza una credenziale di database con ambito di accesso non pubblica archiviazione blob di Azure con PolyBase. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]utilizza le credenziali con ambito per la funzionalità di query globale del database. Questa è la possibilità di eseguire query tra più partizioni di database.  
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]Usa le credenziali con ambito database per scrivere file di eventi estesi in archiviazione blob di Azure.  
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]Usa le credenziali con ambito per il pool elastico di database. Per ulteriori informazioni, vedere [offre la crescita esponenziale con i database elastici](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)  

- [L'istruzione BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) e [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) con ambito di database di utilizzare le credenziali per accedere ai dati dall'archiviazione blob di Azure. Per ulteriori informazioni, vedere [esempi di massa di accesso ai dati nell'archiviazione Blob di Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md). 
  
## <a name="permissions"></a>Permissions  
 Richiede **controllo** autorizzazione per il database.  
  
## <a name="examples"></a>Esempi  
### <a name="a-creating-a-database-scoped-credential-for-your-application"></a>A. Creazione di un database con l'ambito delle credenziali per l'applicazione.
 L'esempio seguente crea le credenziali con ambito database chiamata `AppCred`. Le credenziali con ambito database contengono l'utente di Windows `Mary5` e una password.  
  
```tsql  
-- Create a db master key if one does not already exist, using your own password.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD='<EnterStrongPasswordHere>';  
  
-- Create a database scoped credential.  
CREATE DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  

### <a name="b-creating-a-database-scoped-credential-for-a-shared-access-signature"></a>B. Creazione di un database con l'ambito delle credenziali per una firma di accesso condiviso.   
L'esempio seguente crea una credenziale con ambito database che può essere utilizzata per creare un [origine dati esterna](../../t-sql/statements/create-external-data-source-transact-sql.md), che è possibile effettuare delle operazioni bulk, ad esempio [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) e [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). Firme di accesso condiviso non può essere utilizzate con PolyBase in SQL Server, i punti di accesso o data Warehouse di SQL.
```tsql
CREATE DATABASE SCOPED CREDENTIAL MyCredentials  
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'QLYMgmSXMklt%2FI1U6DcVrQixnlU5Sgbtk1qDRakUBGs%3D';
```
  
### <a name="c-creating-a-database-scoped-credential-for-polybase-connectivity-to-azure-data-lake-store"></a>C. Creazione di un database con l'ambito delle credenziali per la connettività di PolyBase per archivio Azure Data Lake.  
L'esempio seguente crea una credenziale con ambito database che può essere utilizzata per creare un [origine dati esterna](../../t-sql/statements/create-external-data-source-transact-sql.md), che può essere usato da PolyBase in Azure SQL Data Warehouse.

Archivio Azure Data Lake utilizza un'applicazione di Azure Active Directory per l'autenticazione al servizio.
. [Creare un'applicazione AAD](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory) e documentare la client_id, OAuth_2.0_Token_EndPoint e la chiave prima di provare a creare le credenziali con ambito database.

```tsql
CREATE DATABASE SCOPED CREDENTIAL ADL_User
WITH
    IDENTITY = '<client_id>@\<OAuth_2.0_Token_EndPoint>'
    SECRET = '<key>'
;
```  
  
  
  
## <a name="more-information"></a>Ulteriori informazioni  
 [Credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [ALTER DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
