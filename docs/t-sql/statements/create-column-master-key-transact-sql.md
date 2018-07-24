---
title: CREATE COLUMN MASTER KEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SQL13.SWB.NEWCOLUMNMASTERKEYDEF.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEYDEF.GENERAL.F1
- CREATE COLUMN MASTER KEY
- COLUMN MASTER KEY
- CREATE_COLUMN_MASTER_KEY_TSQL
- COLUMN_MASTER_KEY_TSQL
- SQL13.SWB.NEWCOLUMNMASTERKEY.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEY.GENERAL.F1
dev_langs:
- TSQL
helpviewer_keywords:
- column master key definition
- column master key, create
- CREATE COLUMN MASTER KEY statement
- Always Encrypted, create column master key
ms.assetid: f8926b95-e146-4e3f-b56b-add0c0d0a30e
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a4f7c950785268f1b462c8363e4fb9e5f426055b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993133"
---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Crea un oggetto metadati chiave master della colonna nel database. Una voce di metadati chiave master della colonna che rappresenta una chiave, archiviata in un archivio chiavi esterno, usato per proteggere (crittografare) le chiavi di crittografia della colonna quando si usa la funzionalità [Always Encrypted &#40;motore di database&#41; ](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Più chiavi master della colonna consentono la rotazione delle chiavi, modificando periodicamente la chiave per migliorare la sicurezza. È possibile creare una chiave master della colonna in un archivio chiavi e l'oggetto metadati corrispondente nel database tramite Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o PowerShell. Per i dettagli, vedere [Panoramica della gestione delle chiavi per Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE COLUMN MASTER KEY key_name   
    WITH (  
        KEY_STORE_PROVIDER_NAME = 'key_store_provider_name',  
        KEY_PATH = 'key_path'   
         )   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *key_name*  
 Nome con il quale sarà nota la chiave master della colonna all'interno del database.  
  
 *key_store_provider_name*  
 Specifica il nome di un provider dell'archivio chiavi, un componente software lato client che incapsula un archivio chiavi contenente la chiave master della colonna. Un driver client abilitato per Always Encrypted usa il nome di un provider dell'archivio chiavi per cercare un provider dell'archivio chiavi nel registro del driver dei provider dell'archivio chiavi. Il driver usa il provider per decrittografare le chiavi di crittografia della colonna, protette da una chiave master della colonna, archiviata nell'archivio chiavi sottostante. Un valore di testo non crittografato della chiave di crittografia della colonna viene quindi usato per crittografare i parametri di query, corrispondenti alle colonne del database crittografate, o per decrittografare i risultati delle query provenienti dalle colonne crittografate.  
  
 Le librerie dei driver client abilitati per Always Encrypted includono provider dell'archivio chiavi per gli archivi chiavi più diffusi.   
  
Il set di provider disponibili dipende dal tipo e dalla versione del driver client. Per driver particolari, fare riferimento alla documentazione di Always Encrypted:

[Sviluppare applicazioni usando Always Encrypted con il provider di dati .NET Framework per SQL Server](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)


La tabella seguente contiene i nomi dei provider di sistema:  
  
|Nome provider archivio chiavi|Archivio chiavi sottostante|  
    |-----------------------------|--------------------------|
    |'MSSQL_CERTIFICATE_STORE'|Archivio certificati Windows| 
    |'MSSQL_CSP_PROVIDER'|Archivio, ad esempio un modulo di protezione hardware, che supporta la CryptoAPI Microsoft.|
    |'MSSQL_CNG_STORE'|Archivio, ad esempio un modulo di protezione hardware, che supporta l'API Cryptography Next Generation di Microsoft.|  
    |'Azure_Key_Vault'|[Introduzione a Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)|  
  

 È possibile implementare un provider dell'archivio chiavi personalizzato allo scopo di archiviare chiavi master della colonna in un archivio per il quale non esiste un provider dell'archivio chiavi predefinito nel driver client abilitato per Always Encrypted.  Si noti che i nomi dei provider dell'archivio chiavi personalizzati non possono iniziare con 'MSSQL_', che è un prefisso riservato per i provider dell'archivio chiavi [!INCLUDE[msCoName](../../includes/msconame-md.md)]. 

  
 key_path  
 Percorso della chiave nell'archivio chiavi master della colonna. Il percorso della chiave deve essere valido nel contesto di ogni applicazione client che si prevede che effettui la crittografia o la decrittografia dei dati archiviati in una colonna (indirettamente) protetta dalla chiave master della colonna di riferimento e l'applicazione client deve essere autorizzata ad accedere alla chiave. Il formato del percorso della chiave è specifico del provider dell'archivio chiavi. L'elenco seguente descrive il formato dei percorsi delle chiavi per provider dell'archivio chiavi di sistema Microsoft specifici.  
  
-   **Nome provider:** MSSQL_CERTIFICATE_STORE  
  
     **Formato del percorso della chiave:** *CertificateStoreName*/*CertificateStoreLocation*/*CertificateThumbprint*  
  
     Dove:  
  
     *CertificateStoreLocation*  
     Posizione dell'archivio certificati, che deve essere Utente corrente o Computer locale. Per altre informazioni, vedere [Local Machine and Current User Certificate Stores](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx) (Archivi certificati Computer locale e Utente corrente).  
  
     *CertificateStore*  
     Nome dell'archivio certificati, ad esempio 'My'.  
  
     *CertificateThumbprint*  
     Identificazione personale del certificato.  
  
     **Esempi:**  
  
    ```  
    N'CurrentUser/My/BBF037EC4A133ADCA89FFAEC16CA5BFA8878FB94'  
  
    N'LocalMachine/My/CA5BFA8878FB94BBF037EC4A133ADCA89FFAEC16'  
    ```  
  
-   **Nome del provider:** MSSQL_CSP_PROVIDER  
  
     **Formato del percorso della chiave:** *ProviderName*/*KeyIdentifier*  
  
     Dove:  
  
     *ProviderName*  
     Nome di un provider del servizio di crittografia (CSP, Cryptography Service Provider), che implementa CAPI, per l'archivio chiavi master della colonna. Se si usa un modulo di protezione hardware come archivio chiavi, deve essere il nome del CSP fornito dal fornitore del modulo di protezione hardware. Il provider deve essere installato in un computer client.  
  
     *KeyIdentifier*  
     Identificatore della chiave, usato come chiave master della colonna, nell'archivio chiavi.  
  
     **Esempi:**  
  
    ```  
    N'My HSM CSP Provider/AlwaysEncryptedKey1'  
    ```  
  
-   **Nome del provider:** MSSQL_CNG_STORE  
  
     **Formato del percorso della chiave:** *ProviderName*/*KeyIdentifier*  
  
     Dove:  
  
     *ProviderName*  
     Nome del provider di archiviazione chiavi, che implementa l'API Cryptography Next Generation (CNG), per l'archivio chiavi master della colonna. Se si usa un modulo di protezione hardware come archivio chiavi, deve essere il nome del provider di archiviazione chiavi fornito dal fornitore del modulo di protezione hardware. Il provider deve essere installato in un computer client.  
  
     *KeyIdentifier*  
     Identificatore della chiave, usato come chiave master della colonna, nell'archivio chiavi.  
  
     **Esempi:**  
  
    ```  
    N'My HSM CNG Provider/AlwaysEncryptedKey1'  
    ```  

-   **Nome del provider:** AZURE_KEY_STORE  
  
     **Formato del percorso della chiave:** *KeyUrl*  
  
     Dove:  
  
     *KeyUrl*  
     URL della chiave in Azure Key Vault


Esempio:
 
`N'https://myvault.vault.azure.net:443/keys/MyCMK/4c05f1a41b12488f9cba2ea964b6a700'`  
  
## <a name="remarks"></a>Remarks  

È necessario creare una voce di metadati della chiave master della colonna prima di poter creare nel database una voce di metadati della chiave di crittografia della colonna e prima di poter crittografare qualsiasi colonna nel database con Always Encrypted. Si noti che una voce di chiave master della colonna nei metadati non contiene la chiave master della colonna effettiva, che deve essere archiviata in un archivio chiavi della colonna esterno (all'esterno di SQL Server). Il nome del provider dell'archivio chiavi e il percorso della chiave master della colonna nei metadati devono essere validi perché un'applicazione client sia in grado di usare la chiave master della colonna per decrittografare una chiave di crittografia della colonna crittografata con la chiave master della colonna e perché sia in grado di effettuare query sulle colonne crittografate.


  
## <a name="permissions"></a>Permissions  
 È necessaria l'autorizzazione **ALTER ANY COLUMN MASTER KEY**.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-column-master-key"></a>A. Creazione di una chiave master della colonna  
 Creazione di una voce di metadati della chiave master della colonna per una chiave master della colonna archiviata nell'archivio certificati, per applicazioni client che usano il provider MSSQL_CERTIFICATE_STORE per accedere alla chiave master della colonna:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
 Creazione di una voce di metadati della chiave master della colonna per una chiave master della colonna a cui accedono applicazioni client che usano il provider MSSQL_CNG_STORE:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CNG_STORE',    
    KEY_PATH = N'My HSM CNG Provider/AlwaysEncryptedKey'  
);  
```  
  
 Creazione di una chiave master della colonna archiviata in Azure Key Vault, per applicazioni client che usano il provider AZURE_KEY_VAULT, per accedere alla chiave master della colonna.  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/  
        MyCMK/4c05f1a41b12488f9cba2ea964b6a700');  
```  
  
 Creazione di una chiave master della colonna archiviata in un archivio chiavi master della colonna:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = 'CUSTOM_KEY_STORE',    
    KEY_PATH = 'https://contoso.vault/sales_db_tce_key'  
);  
```  
  
## <a name="see-also"></a>Vedere anche
 
* [DROP COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
* [Panoramica della gestione delle chiavi per Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
  
