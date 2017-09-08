---
title: CREARE la chiave MASTER della colonna (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 871acb46898a9a62b25062f69d4e51bf28658f06
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Crea un oggetto di metadati chiave master della colonna in un database. Una voce di metadati chiave master della colonna che rappresenta una chiave, archiviati in un archivio di chiavi esterno, viene utilizzato per proteggere (crittografare) le chiavi di crittografia di colonna quando si utilizza il [Always Encrypted &#40; motore di Database &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md) funzionalità. Consenti più chiavi master della colonna per la rotazione delle chiavi; modifica periodica della chiave per migliorare la sicurezza. È possibile creare una chiave master della colonna in un archivio chiavi e il relativo oggetto di metadati corrispondente nel database utilizzando Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o PowerShell. Per informazioni dettagliate, vedere [Panoramica della gestione delle chiavi per Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).  
  
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
 È il nome mediante il quale la chiave master della colonna sarà noto nel database.  
  
 *key_store_provider_name*  
 Specifica il nome di un provider dell'archivio chiavi, che è un componente software lato client che incapsula un archivio chiavi contenente la chiave master della colonna. Un driver client abilitato per crittografia sempre attiva utilizza un nome di provider di archivio chiavi per cercare un provider dell'archivio chiavi del Registro di sistema del driver di provider dell'archivio chiavi. Il driver utilizza il provider per decrittografare le chiavi di crittografia di colonna, protette dalla chiave master della colonna, archiviata nell'archivio delle chiavi sottostante. Un valore crittografato della chiave di crittografia della colonna viene quindi utilizzato per crittografare i parametri di query, corrispondenti alle colonne del database crittografato, o per decrittografare i risultati della query dalle colonne crittografate.  
  
 Le librerie di driver di Always Encrypted abilitato client includono provider dell'archivio chiavi per archivi chiavi più diffusi.   
  
Un set di provider disponibili dipendono dal tipo e la versione del driver client. Consultare la documentazione di Always Encrypted per un driver specifico:

[Sviluppare applicazioni usando Always Encrypted con il Provider .NET Framework per SQL Server](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)


Di seguito tabelle acquisisce i nomi di provider di sistema:  
  
|Nome provider archivio chiavi|Archivio chiave sottostante|  
    |-----------------------------|--------------------------|
    |'MSSQL_CERTIFICATE_STORE'|Archivio certificati di Windows| 
    |'MSSQL_CSP_PROVIDER'|Un archivio, ad esempio un modulo di protezione hardware (HSM), che supporta Microsoft CryptoAPI.|
    |'MSSQL_CNG_STORE'|Un archivio, ad esempio un modulo di protezione hardware (HSM), che supporta l'API Cryptography: generazione successiva.|  
    |'Azure_Key_Vault'|Vedere [Guida introduttiva a insieme di credenziali chiave di Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)|  
  

 È possibile implementare un provider dell'archivio chiavi personalizzato, per poter archiviare chiavi master della colonna in un archivio in cui non è presente alcuna chiave incorporata provider dell'archivio nel driver client abilitato per Always Encrypted.  Si noti che i nomi di provider di archivio chiavi personalizzato non possono iniziare con 'MSSQL _', che è un prefisso riservato [!INCLUDE[msCoName](../../includes/msconame-md.md)] provider di archiviazione chiavi. 

  
 key_path  
 Archiviare il percorso della chiave master della colonna chiave. Il percorso della chiave deve essere valido nel contesto di ogni applicazione client che si prevede di crittografare o decrittografare i dati archiviati in una colonna (indirettamente) protetta dalla chiave master della colonna di riferimento e l'applicazione client deve essere consentito di accedere alla chiave. Il formato del percorso della chiave è specifico del provider di archivio chiavi. Nell'elenco seguente descrive il formato di percorsi principali per determinati provider di archivio chiavi di sistema di Microsoft.  
  
-   **Nome del provider:** MSSQL_CERTIFICATE_STORE  
  
     **Formato del percorso di chiave:** *NomeArchivioCertificati*/*CertificateStoreLocation*/*CertificateThumbprint*  
  
     Dove:  
  
     *CertificateStoreLocation*  
     Percorso dell'archivio certificati, che deve essere l'utente corrente o al computer locale. Per ulteriori informazioni, vedere [del computer locale e archivi di certificati utente corrente](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx).  
  
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
  
     **Formato del percorso di chiave:** *ProviderName*/*KeyIdentifier*  
  
     Dove:  
  
     *ProviderName*  
     Il nome di un Cryptography Service Provider (CSP), che implementa CAPI, per l'archivio chiavi master della colonna. Se si utilizza un modulo HSM come un archivio chiavi, deve essere il nome del CSP il fornitore del modulo fornisce. Il provider deve essere installato in un computer client.  
  
     *KeyIdentifier*  
     Identificatore della chiave, utilizzato come chiave master della colonna, nell'archivio delle chiavi.  
  
     **Esempi:**  
  
    ```  
    N'My HSM CSP Provider/AlwaysEncryptedKey1'  
    ```  
  
-   **Nome del provider:** MSSQL_CNG_STORE  
  
     **Formato del percorso di chiave:** *ProviderName*/*KeyIdentifier*  
  
     Dove:  
  
     *ProviderName*  
     Nome dell'archiviazione Provider chiavi (KSP), che implementa la crittografia: Next Generation (CNG) API, per l'archivio chiavi master della colonna. Se si utilizza un modulo HSM come un archivio chiavi, deve essere il nome del KSP il fornitore del modulo fornisce. Il provider deve essere installato in un computer client.  
  
     *KeyIdentifier*  
     Identificatore della chiave, utilizzato come chiave master della colonna, nell'archivio delle chiavi.  
  
     **Esempi:**  
  
    ```  
    N'My HSM CNG Provider/AlwaysEncryptedKey1'  
    ```  

-   **Nome del provider:** AZURE_KEY_STORE  
  
     **Formato del percorso di chiave:** *KeyUrl*  
  
     Dove:  
  
     *KeyUrl*  
     L'URL della chiave nell'insieme di credenziali chiave di Azure


Esempio:
 
`N'https://myvault.vault.azure.net:443/keys/MyCMK/4c05f1a41b12488f9cba2ea964b6a700'`  
  
## <a name="remarks"></a>Osservazioni  

È necessario creare una voce di metadati chiave master della colonna prima di poter creare una voce di metadati della chiave di crittografia di colonna nel database e prima di qualsiasi colonna nel database può essere crittografata con crittografia sempre attiva. Si noti che, una voce di chiave master della colonna nei metadati non contiene la chiave master di colonna effettivi, che deve essere memorizzata in un archivio chiavi colonna esterna (all'esterno di SQL Server). Il nome del provider di archivio chiavi e il percorso della chiave master di colonna nei metadati devono essere validi per un'applicazione client in grado di utilizzare la chiave master della colonna per decrittografare una chiave di crittografia di colonna crittografata con la chiave master della colonna e di query sulle colonne crittografate.


  
## <a name="permissions"></a>Permissions  
 Richiede il **ALTER ANY COLUMN MASTER KEY** autorizzazione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-column-master-key"></a>A. Creazione di una chiave master della colonna  
 Creazione di una voce di metadati della chiave master della colonna per una chiave master della colonna archiviata nell'archivio certificati, per le applicazioni client che utilizzano il provider MSSQL_CERTIFICATE_STORE per accedere alla chiave master di colonna:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
 Creazione di una voce di metadati della chiave master della colonna per una chiave master della colonna che si accede dalle applicazioni client che utilizzano il provider MSSQL_CNG_STORE:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CNG_STORE',    
    KEY_PATH = N'My HSM CNG Provider/AlwaysEncryptedKey'  
);  
```  
  
 Creazione di una chiave master della colonna archiviata nell'insieme di credenziali chiave di Azure, per le applicazioni client che utilizzano il provider AZURE_KEY_VAULT, per accedere alla chiave master di colonna.  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/  
        MyCMK/4c05f1a41b12488f9cba2ea964b6a700');  
```  
  
 Creazione di una CMK archiviata in un archivio chiavi master della colonna personalizzata:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = 'CUSTOM_KEY_STORE',    
    KEY_PATH = 'https://contoso.vault/sales_db_tce_key'  
);  
```  
  
## <a name="see-also"></a>Vedere anche
 
* [ELIMINARE la chiave MASTER della colonna &#40; Transact-SQL &#41;](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
* [Panoramica della gestione delle chiavi per Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
  

