---
title: CREARE il PROVIDER di crittografia (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_CRYPTOGRAPHIC_TSQL
- CRYPTOGRAPHIC PROVIDER
- PROVIDER_TSQL
- CREATE CRYPTOGRAPHIC
- CREATE CRYPTOGRAPHIC PROVIDER
- CRYPTOGRAPHIC_PROVIDER_TSQL
- CREATE_CRYPTOGRAPHIC_PROVIDER_TSQL
- PROVIDER
dev_langs:
- TSQL
helpviewer_keywords:
- 33085 (Database Engine error)
- CREATE CRYPTOGRAPHIC PROVIDER statement
- 33032 (Database Engine error)
ms.assetid: 059a39a6-9d32-4d3f-965b-0a1ce75229c7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bedc5441c8119101a209de42358b38d20c288b8d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-cryptographic-provider-transact-sql"></a>CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un provider del servizio di crittografia in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un provider EKM (Extensible Key Management).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE CRYPTOGRAPHIC PROVIDER provider_name   
    FROM FILE = path_of_DLL  
```  
  
## <a name="arguments"></a>Argomenti  
 *provider_name*  
 Nome del provider EKM.  
  
 *path_of_DLL*  
 Percorso del file dll che implementa l'interfaccia EKM di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando si utilizza il **SQL Server Connector per Microsoft Azure Key Vault** il percorso predefinito è **' C:\Program Files\Microsoft SQL Server Connector per Microsoft Azure chiave Vault\Microsoft.AzureKeyVaultService.EKM.dll '**.  
  
## <a name="remarks"></a>Osservazioni  
 Tutte le chiavi create da un provider faranno riferimento al provider attraverso il GUID. Il GUID viene mantenuto per tutte le versioni della DLL.  
  
 Alla DLL che implementa l'interfaccia SQLEKM deve essere applicata una firma digitale usando qualsiasi certificato. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verificherà la firma. Ciò include la catena di certificati, che deve avere installato nella radice di **autorità di certificazione radice attendibili** percorso in un sistema di Windows. Se la firma non viene verificata correttamente, l'istruzione CREATE CRYPTOGRAPHIC PROVIDER avrà esito negativo. Per ulteriori informazioni sui certificati e le catene di certificati, vedere [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
 Quando la DLL di un provider EKM non implementa tutti i metodi necessari, CREATE CRYPTOGRAPHIC PROVIDER può restituire l'errore 33085:  
  
 `One or more methods cannot be found in cryptographic provider library '%.*ls'.`  
  
 Quando il file di intestazione utilizzato per creare la DLL del provider EKM non è aggiornato, CREATE CRYPTOGRAPHIC PROVIDER può restituire l'errore 33032:  
  
 `SQL Crypto API version '%02d.%02d' implemented by provider is not supported. Supported version is '%02d.%02d'.`  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione CONTROL SERVER o l'appartenenza di **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente crea un provider di crittografia denominato `SecurityProvider` in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un file con estensione dll. Il file dll è denominato `c:\SecurityProvider\SecurityProvider_v1.dll` ed è installato nel server. Il certificato del provider deve prima essere installato nel server.  
  
```  
-- Install the provider  
CREATE CRYPTOGRAPHIC PROVIDER SecurityProvider  
    FROM FILE = 'C:\SecurityProvider\SecurityProvider_v1.dll';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Extensible Key Management con l'insieme di credenziali delle chiavi di Azure &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  
