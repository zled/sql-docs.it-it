---
title: MODIFICARE l'origine dati esterna (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/09/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL DATA SOURCE
- ALTER_EXTERNAL_DATA_SOURCE
dev_langs: TSQL
helpviewer_keywords:
- polybase, alter external data source statement
- ALTER EXTERNAL DATA SOURCE statement
ms.assetid: a34b9e90-199d-46d0-817a-a7e69387bf5f
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 16ea77011039c1b48ab83bfd335028c83c6f3c3e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="alter-external-data-source-transact-sql"></a>ALTER EXTERNAL DATA SOURCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Modifica di un'origine dati esterna utilizzata per creare una tabella esterna. L'origine dati esterna può essere Hadoop o blob nell'archivio Azure (WASB).
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Modify an external data source
-- Applies to: SQL Server (2016 or later)
ALTER EXTERNAL DATA SOURCE data_source_name SET
    {   
        LOCATION = 'server_name_or_IP' [,] |
        RESOURCE_MANAGER_LOCATION = <'IP address;Port'> [,] |
        CREDENTIAL = credential_name
    }  
    [;]  

-- Modify an external data source pointing to Azure Blob storage
-- Applies to: SQL Server (starting with 2017)
ALTER EXTERNAL DATA SOURCE data_source_name
    WITH (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://storage_account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>Argomenti  
 data_source_name specifica il nome definito dall'utente per l'origine dati. Il nome deve essere univoco.
  
 PERCORSO = 'server_name_or_IP' specifica il nome del server o un indirizzo IP.
  
 RESOURCE_MANAGER_LOCATION = '\<indirizzo IP. Porta >' specifica il percorso di gestione risorse di Hadoop. Quando specificato, query optimizer potrebbe scegliere di pre-elaborare i dati di una query di PolyBase con funzionalità di calcolo di Hadoop. Questa è una decisione basata sui costi. La distribuzione del predicato di chiamata, questo può ridurre notevolmente il volume di dati trasferiti tra Hadoop e SQL e pertanto migliorare le prestazioni delle query.
  
 CREDENZIALE = Credential_Name specifica la credenziale denominata. Vedere [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

TIPO = BLOB_STORAGE   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
Per le operazioni bulk, solo `LOCATION` deve essere valido l'URL di archiviazione Blob di Azure. Non inserire  **/** , nome del file o condiviso i parametri di firma di accesso alla fine del `LOCATION` URL.
La credenziale utilizzata, deve essere creata usando `SHARED ACCESS SIGNATURE` come identità. Per altre informazioni sulle firme di accesso condiviso, vedere [Uso delle firme di accesso condiviso](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).

  
  
## <a name="remarks"></a>Osservazioni
 Solo singola origine può essere modificata alla volta. Richieste simultanee per modificare la stessa origine causano un'istruzione di attesa. Tuttavia, è possono modificare origini diverse nello stesso momento. Questa istruzione è possibile eseguire contemporaneamente altre istruzioni.
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER ANY EXTERNAL DATA SOURCE.
 > [!IMPORTANT]  
 >  L'autorizzazione ALTER ANY EXTERNAL DATA SOURCE concede a qualsiasi entità la possibilità di creare e modificare qualsiasi oggetto di origine dati esterna e di conseguenza, concede inoltre la possibilità di accedere a tutte le credenziali con ambito database nel database. Questa autorizzazione deve essere considerata privilegi elevati e pertanto devono essere concesse solo a entità attendibili nel sistema.

  
## <a name="examples"></a>Esempi  
 L'esempio seguente modifica il percorso e il percorso di gestione risorse di un'origine dati esistente.
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET
     LOCATION = 'hdfs://10.10.10.10:8020',
     RESOURCE_MANAGER_LOCATION = '10.10.10.10:8032'
    ;
  
```  

 L'esempio seguente modifica le credenziali per connettersi a un'origine dati esistente.
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET
   CREDENTIAL = new_hadoop_user
    ;
```