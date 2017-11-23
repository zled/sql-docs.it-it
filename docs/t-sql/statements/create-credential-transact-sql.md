---
title: CREARE le CREDENZIALI (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREDENTIAL_TSQL
- SQL13.SWB.CREDENTIAL.GENERAL.F1
- CREATE CREDENTIAL
- CREATE_CREDENTIAL_TSQL
- CREDENTIAL
dev_langs: TSQL
helpviewer_keywords:
- SECRET clause
- authentication [SQL Server], credentials
- CREATE CREDENTIAL statement
- credentials [SQL Server], CREATE CREDENTIAL statement
ms.assetid: d5e9ae69-41d9-4e46-b13d-404b88a32d9d
caps.latest.revision: "51"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f0e46404d775da09f4aaeb7b9640dd2a35d3cfa2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-credential-transact-sql"></a>CREATE CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea una credenziale a livello di server. Una credenziale è un record contenente le informazioni di autenticazione necessarie per connettersi a una risorsa all'esterno di SQL Server. La maggior parte delle credenziali include un utente e una password di Windows. Salvataggio di un backup del database a una determinata posizione, ad esempio, potrebbe richiedere SQL Server per fornire le credenziali speciali per accedere al percorso. Per ulteriori informazioni, vedere [credenziali (motore di Database)](../../relational-databases/security/authentication-access/credentials-database-engine.md).
  
> [!NOTE]  
>  Per rendere le credenziali durante l'utilizzo a livello di database [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md). Usare una credenziale a livello di server quando è necessario utilizzare le stesse credenziali per più database nel server. Utilizzare le credenziali con ambito database per rendere portabile il database. Quando un database viene spostato in un nuovo server, le credenziali con ambito database verranno spostato automaticamente. Database di utilizzare credenziali con ambito in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
        [ FOR CRYPTOGRAPHIC PROVIDER cryptographic_provider_name ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *credential_name*  
 Viene specificato il nome delle credenziali create. *credential_name* non può iniziare con il simbolo di cancelletto (#). perché tale simbolo viene utilizzato per le credenziali di sistema.  Quando si utilizza una firma di accesso condiviso (SAS), questo nome deve corrispondere al percorso del contenitore, iniziare con https e non deve contenere una barra rovesciata. Vedere l'esempio D seguente.  
  
 IDENTITÀ **='***identity_name***'**  
 Specifica il nome dell'account da utilizzare per la connessione all'esterno del server. Quando la credenziale viene utilizzata per accedere a insieme di credenziali chiave di Azure, il **identità** è il nome dell'insieme di credenziali chiave. Vedere l'esempio C riportato di seguito. Quando si utilizza una firma di accesso condiviso (SAS), le credenziali di **identità** è *firma di accesso condiviso*. Vedere l'esempio D seguente.  
  
 SEGRETO **='***secret***'**  
 Specifica il segreto richiesto per l'autenticazione in uscita.  
  
 Quando la credenziale viene utilizzata per l'insieme di credenziali chiave di Azure di accedere il **SECRET** argomento di **CREATE CREDENTIAL** richiede il  *\<ID Client >* (senza trattini) e  *\<segreto >* di un **dell'entità servizio** in Azure Active Directory da passare insieme senza uno spazio tra di essi. Vedere l'esempio C riportato di seguito. Quando si utilizza una firma di accesso condiviso, le credenziali di **SECRET** è il token di firma di accesso condiviso. Vedere l'esempio D seguente.  Per informazioni sulla creazione di criteri di accesso archiviati e una firma di accesso condiviso in un contenitore di Azure, vedere [lezione 1: creare criteri di accesso archiviati e una firma di accesso condiviso in un contenitore di Azure](../../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md).  
  
 PER PROVIDER di crittografia *cryptographic_provider_name*  
 Specifica il nome di un *chiave Gestione Provider EKM (Enterprise)*. Per ulteriori informazioni sulla gestione delle chiavi, vedere [Extensible Key Management &#40; EKM &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Osservazioni  

 Se IDENTITY è un utente di Windows, il segreto può essere la password. Il segreto viene crittografato con la chiave master del servizio. Se la chiave master del servizio viene rigenerata, il segreto viene ricrittografato con la nuova chiave master del servizio.  
  
 Dopo aver creato una credenziale, è possibile eseguirne il mapping a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso tramite [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) o [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md). Oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso può essere mappata a una sola credenziale, ma è possibile eseguire il mapping di una singola credenziale a più [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli account di accesso. Per ulteriori informazioni, vedere [credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md). Una credenziale a livello di server può essere mappata solo a un account di accesso, non a un utente del database. 
  
 Informazioni sulle credenziali sono visibili nella [credentials](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md) vista del catalogo.  
  
 Se non sono presenti credenziali su cui viene eseguito il mapping a un account accesso per il provider, vengono utilizzate le credenziali sui cui viene eseguito il mapping all'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 A un account di accesso è possibile eseguire il mapping di più credenziali, a condizione che vengano utilizzate con provider distinti. È possibile eseguire il mapping di una sola credenziale per provider per ogni account di accesso. Sulla stessa credenziale è possibile eseguire il mapping ad altri account di accesso.  
  
## <a name="permissions"></a>Permissions  
 Richiede **ALTER ANY CREDENTIAL** autorizzazione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-basic-example"></a>A. Esempio di base  
 Nell'esempio seguente viene creata la credenziale denominata `AlterEgo`. Tale credenziale contiene l'utente di Windows `Mary5` e una password.  
  
```  
CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-credential-for-ekm"></a>B. Creazione di una credenziale per EKM  
 Nell'esempio seguente viene utilizzato un account creato in precedenza denominato `User1OnEKM` in un modulo EKM tramite gli strumenti di gestione di EKM, con un tipo di account di base e una password. Il **sysadmin** account sul server crea una credenziale che viene utilizzata per connettersi all'account EKM e assegna al `User1` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account:  
  
```  
CREATE CREDENTIAL CredentialForEKM  
    WITH IDENTITY='User1OnEKM', SECRET='<EnterStrongPasswordHere>'  
    FOR CRYPTOGRAPHIC PROVIDER MyEKMProvider;  
GO  
  
/* Modify the login to assign the cryptographic provider credential */  
ALTER LOGIN Login1  
ADD CREDENTIAL CredentialForEKM;  
  
/* Modify the login to assign a non cryptographic provider credential */   
ALTER LOGIN Login1  
WITH CREDENTIAL = AlterEgo;  
GO  
```  
  
### <a name="c-creating-a-credential-for-ekm-using-the-azure-key-vault"></a>C. Creazione di una credenziale per EKM con l'insieme di credenziali chiave di Azure  
 Nell'esempio seguente viene creato un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le credenziali per il [!INCLUDE[ssDE](../../includes/ssde-md.md)] da utilizzare quando si accede utilizzando insieme credenziali chiavi Azure il **SQL Server Connector per Microsoft Azure Key Vault**. Per un esempio completo dell'utilizzo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connettore, vedere [Extensible Key Management con insieme credenziali chiavi Azure &#40; SQL Server &#41; ](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
> [!IMPORTANT]  
>  L'argomento **IDENTITY** di **CREATE CREDENTIAL** richiede il nome dell'insieme di credenziali delle chiavi. Il **SECRET** argomento di **CREATE CREDENTIAL** richiede il  *\<ID Client >* (senza trattini) e  *\<segreto >*  da passare insieme senza uno spazio tra di essi.  
  
 Nell'esempio seguente l' **ID client** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) viene immesso con tutti i trattini rimossi come stringa `EF5C8E094D2A4A769998D93440D8115D` e il **Segreto** è rappresentato dalla stringa *SECRET_DBEngine*.  
  
```  
USE master;  
CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault',   
    SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
```  
  
 Nell'esempio seguente viene creata la stessa credenziale utilizzando le variabili per il **ID Client** e **Secret** stringhe, che vengono quindi concatenate insieme per formare il **SECRET** argomento. Il **sostituire** funzione viene utilizzata per rimuovere i trattini dall'ID Client.  
  
```  
DECLARE @AuthClientId uniqueidentifier = 'EF5C8E09-4D2A-4A76-9998-D93440D8115D';  
DECLARE @AuthClientSecret varchar(200) = 'SECRET_DBEngine';  
DECLARE @pwd varchar(max) = REPLACE(CONVERT(varchar(36), @AuthClientId) , '-', '') + @AuthClientSecret;  
  
EXEC ('CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault', SECRET = ''' + @PWD + '''   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;');  
```  
  
### <a name="d-creating-a-credential-using-a-sas-token"></a>D. Creazione di una credenziale utilizzando un Token di firma di accesso condiviso  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [versione](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
 Nell'esempio seguente crea una credenziale di firma di accesso condiviso usando un token di firma di accesso condiviso.  Per un'esercitazione sulla creazione di criteri di accesso archiviati e una firma di accesso condiviso in un contenitore di Azure e quindi creare una credenziale utilizzando la firma di accesso condiviso, vedere [esercitazione: utilizzo del servizio di archiviazione Blob di Microsoft Azure con SQL Server 2016 database](Tutorial:%20Using%20the%20Microsoft%20Azure%20Blob%20storage%20service%20with%20SQL%20Server%202016%20databases.md).  
  
> [!IMPORTANT]  
>  IL **nome delle CREDENZIALI** argomento richiede che il nome corrisponde al percorso del contenitore, iniziare con https e non contengono una barra finale. Il **identità** argomento richiede il nome, *firma di accesso condiviso*. Il **SECRET** argomento richiede che il token di firma di accesso condiviso.  
  
```  
USE master  
CREATE CREDENTIAL [https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>] -- this name must match the container path, start with https and must not contain a trailing forward slash.  
   WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
   , SECRET = 'sharedaccesssignature' –- this is the shared access signature token   
GO    
```  
  
## <a name="see-also"></a>Vedere anche  
 [Credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Istruzione ALTER CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-credential-transact-sql.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Lezione 2: Creare una credenziale di SQL Server utilizzando una firma di accesso condiviso](../../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)   
 [Firme di accesso condiviso](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
  
  
