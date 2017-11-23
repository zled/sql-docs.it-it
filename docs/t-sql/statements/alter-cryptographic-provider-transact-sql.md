---
title: Istruzione ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/20/2017
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
- ALTER_CRYPTOGRAPHIC_PROVIDER_TSQL
- ALTER CRYPTOGRAPHIC PROVIDER
- ALTER_CRYPTOGRAPHIC_TSQL
- ALTER CRYPTOGRAPHIC
dev_langs: TSQL
helpviewer_keywords: ALTER CRYPTOGRAPHIC PROVIDER
ms.assetid: 876b6348-fb29-49e1-befc-4217979f6416
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fe377a27978cdae372a7bfc8545d7cad1f514820
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-cryptographic-provider-transact-sql"></a>ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica un provider di crittografia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un provider EKM (Extensible Key Management).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER CRYPTOGRAPHIC PROVIDER provider_name   
    [ FROM FILE = path_of_DLL ]  
    ENABLE | DISABLE  
```  
  
## <a name="arguments"></a>Argomenti  
 *provider_name*  
 Nome del provider EKM.  
  
 *Path_of_DLL*  
 Percorso del file DLL che implementa l'interfaccia EKM di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ENABLE | DISABLE  
 Abilita o disabilita un provider.  
  
## <a name="remarks"></a>Osservazioni  
 Se il provider modifica il file DLL utilizzato per l'implementazione di EKM (Extensible Key Management) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario utilizzare l'istruzione ALTER CRYPTOGRAPHIC PROVIDER.  
  
 Quando il percorso del file DLL viene aggiornato utilizzando l'istruzione ALTER CRYPTOGRAPHIC PROVIDER, tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono effettuate le azioni seguenti:  
-   Disabilitazione del provider.  
-   Verifica della firma DLL e del fatto che il GUID del file DLL sia uguale a quello registrato nel catalogo.  
-   Aggiornamento della versione DLL nel catalogo.  
  

Quando un provider EKM viene impostato su DISABLE, qualsiasi tentativo effettuato su nuove connessioni di utilizzare il provider con istruzioni di crittografia avrà esito negativo.  
  
Per disabilitare un provider, è necessario terminare tutte le sessioni che lo utilizzano.  
  
Quando la dll di un provider EKM non implementa tutti i metodi necessari, ALTER CRYPTOGRAPHIC PROVIDER può restituire l'errore 33085:  
  
 `One or more methods cannot be found in cryptographic provider library '%.*ls'.`  
  
Quando il file di intestazione utilizzato per creare la dll del provider EKM non è aggiornato, ALTER CRYPTOGRAPHIC PROVIDER può restituire l'errore 33032:  
  
 `SQL Crypto API version '%02d.%02d' implemented by provider is not supported. Supported version is '%02d.%02d'.`  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per il provider di crittografia.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente modifica un provider di crittografia, denominato `SecurityProvider` in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a una versione più recente di un file DLL. Questa nuova versione è denominata `c:\SecurityProvider\SecurityProvider_v2.dll` e viene installato nel server. Il certificato del provider deve essere installato nel server.  
  
1. Disabilitare il provider per eseguire l'aggiornamento. Questo comporta la terminazione tutte le sessioni di crittografia.  
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
DISABLE;  
GO  
```  

2. Aggiornare il file con estensione DLL del provider. Il GUID deve essere identico alla versione precedente, ma la versione può essere diversa.  
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider  
FROM FILE = 'c:\SecurityProvider\SecurityProvider_v2.dll';  
GO  
```  

3. Abilitare il provider aggiornato.   
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
ENABLE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Extensible Key Management con l'insieme di credenziali delle chiavi di Azure &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  
