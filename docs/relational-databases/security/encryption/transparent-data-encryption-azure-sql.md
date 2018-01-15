---
title: TDE per il database SQL di Azure e Azure SQL Data Warehouse | Microsoft Docs
description: "Panoramica di Transparent Data Encryption per il database SQL e SQL Data Warehouse. Il documento ne illustra i vantaggi e le opzioni per la configurazione, incluse le funzionalità TDE gestita dal servizio e Bring Your Own Key."
keywords: 
author: becczhang
manager: craigg
editor: 
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.component: security
ms.custom: 
ms.workload: On Demand
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: rebeccaz
ms.openlocfilehash: 39e1807178f536a1bac2148deae406b1e3bb44b5
ms.sourcegitcommit: 34d3497039141d043429eed15d82973b18ad90f2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="transparent-data-encryption-for-azure-sql-database-and-data-warehouse"></a>Transparent Data Encryption per il database SQL di Azure e Azure SQL Data Warehouse
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

Transparent Data Encryption (TDE) contribuisce alla protezione del database SQL di Azure e di Azure SQL Data Warehouse dalle minacce di attività dannose eseguendo la crittografia e la decrittografia in tempo reale del database, dei backup associati e dei file di log delle transazioni inattivi senza la necessità di apportare modifiche all'applicazione.

TDE crittografa l'archivio di un intero database usando una chiave simmetrica denominata chiave di crittografia del database (DEK, Database Encryption Key). Questa chiave di crittografia del database è protetta dalla protezione TDE, ovvero un certificato gestito dal servizio ("TDE gestita dal servizio") o una chiave asimmetrica archiviata in Azure Key Vault ("Bring Your Own Key"). La protezione TDE viene impostata a livello di server. 

All'avvio del database, la chiave DEK crittografata viene decrittografata e quindi usata per decrittografare e ricrittografare i file di database nel processo del motore SQL. TDE esegue in tempo reale la crittografia e decrittografia dell'I/O dei dati a livello di pagina. Ogni pagina viene decrittografata quando viene letta nella memoria e crittografata prima di essere scritta su disco. Per una descrizione generale di TDE, vedere [Transparent Data Encryption (TDE)](transparent-data-encryption.md).

Per SQL Server in esecuzione in una macchina virtuale di Azure è anche possibile usare una chiave asimmetrica di Key Vault. I passaggi di configurazione sono diversi rispetto all'uso di una chiave asimmetrica nel database SQL di Azure. Per altre informazioni, vedere [Extensible Key Management tramite Azure Key Vault (SQL Server)](extensible-key-management-using-azure-key-vault-sql-server.md).

## <a name="service-managed-tde"></a>TDE gestita dal servizio

In Azure l'impostazione predefinita di TDE prevede che la chiave di crittografia del database sia protetta da un certificato predefinito del server. Il certificato predefinito del server è univoco per ogni server. Se un database è in una relazione di replica geografica, il database primario e il database di replica geografica secondaria saranno protetti dalla chiave del server padre del database primario. Se due database sono connessi allo stesso server, condividono lo stesso certificato predefinito. Microsoft ruota automaticamente questi certificati almeno ogni 90 giorni.

Microsoft sposta e gestisce inoltre le chiavi in base alle esigenze per la replica geografica e i ripristini. 

> [!IMPORTANT]
> Per impostazione predefinita, tutti i nuovi database SQL vengono crittografati usando la funzionalità TDE gestita dal servizio. I database esistenti prima di maggio 2017 e quelli creati tramite ripristino, replica geografica e copia di database non vengono crittografati per impostazione predefinita.
>

## <a name="bring-your-own-key-preview"></a>Bring Your Own Key (anteprima)

Il supporto Bring Your Own Key (BYOK) (in anteprima) consente all'utente di avere il controllo delle proprie chiavi di crittografia TDE e di controllare chi può accedervi e quando. Azure Key Vault (AKV), ovvero il sistema di gestione delle chiavi esterne basato sul cloud di Azure, è il primo servizio di gestione delle chiavi con cui è stato integrato TDE per il supporto BYOK. Con BYOK, la chiave di crittografia del database è protetta da una chiave asimmetrica archiviata in AKV. La chiave asimmetrica rimane in Key Vault. Dopo che il server ha ottenuto l'autorizzazione per un insieme di credenziali delle chiavi, invierà a questo insieme le richieste di operazioni di base relative alle chiavi tramite il servizio Key Vault. La chiave asimmetrica viene impostata a livello di server ed ereditata da tutti i database presenti nel server. Con il supporto BYOK, gli utenti possono ora controllare le attività di gestione delle chiavi, tra cui le rotazioni delle chiavi, le autorizzazioni dell'insieme di credenziali delle chiavi e l'eliminazione delle chiavi, nonché abilitare il controllo e la creazione di report relativi a tutte le chiavi di crittografia. Key Vault consente di gestire le chiavi in modo centralizzato, usa moduli di protezione hardware accuratamente monitorati e promuove la separazione della gestione delle chiavi e dei dati per contribuire a soddisfare la conformità alle normative. Per altre informazioni su Key Vault, visitare la [pagina della documentazione di Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault).

Per altre informazioni su TDE con il supporto BYOK per il database SQL di Azure e Azure SQL Data Warehouse, vedere [Transparent Data Encryption with Bring Your Own Key support](transparent-data-encryption-byok-azure-sql.md) (Transparent Data Encryption con il supporto Bring Your Own Key).

Per iniziare a usare TDE con il supporto BYOK, vedere la guida alle procedure [Turn on Transparent Data Encryption using your own key from Key Vault Using PowerShell](transparent-data-encryption-byok-azure-sql-configure.md) (Attivare Transparent Data Encryption con una chiave personalizzata di Key Vault usando PowerShell).

## <a name="moving-a-tde-protected-database"></a>Spostamento di un database protetto da TDE

Non è necessario decrittografare i database per eseguire operazioni all'interno di Azure. Le impostazioni di Transparent Data Encryption nel database di origine o nel database primario vengono ereditate in modo trasparente nel database di destinazione. Sono incluse le operazioni che prevedono le attività seguenti:
- Ripristino geografico
- Ripristino temporizzato self-service
- Ripristino di un database eliminato
- Replica geografica attiva
- Creazione di una copia del database

Quando si esporta un database protetto da TDE, il contenuto esportato del database non è crittografato. Questo contenuto esportato viene archiviato in file BACPAC non crittografati. Assicurarsi di proteggere i file BACPAC nel modo appropriato e abilitare TDE al termine dell'importazione del nuovo database.

Ad esempio, se il file BACPAC viene esportato da un'istanza locale di SQL Server, il contenuto importato del nuovo database non viene automaticamente crittografato. Allo stesso modo, se il file BACPAC viene esportato in un'istanza locale di SQL Server, il nuovo database non verrà automaticamente crittografato.

L'unica eccezione riguarda l'esportazione da e verso il database SQL di Azure. TDE è abilitato nel nuovo database, ma il file BACPAC non è comunque crittografato.

## <a name="managing-transparent-data-encryption-in-the-azure-portal"></a>Gestione di Transparent Data Encryption nel portale di Azure

Per configurare TDE tramite il portale di Azure è necessario essere connessi come proprietario, collaboratore o Gestore Sicurezza SQL di Azure. 

Transparent Data Encryption viene impostato a livello di database. Per abilitare TDE in un database, visitare il [portale di Azure](https://portal.azure.com) e accedere con l'account di amministratore o collaboratore di Azure. Le impostazioni di TDE si trovano nel database utente. Per impostazione predefinita, viene usata la funzionalità TDE gestita dal servizio e viene automaticamente generato un certificato TDE per il server contenente il database. 

![TDE gestita dal servizio](./media/transparent-data-encryption-azure-sql/service-managed-tde.png)  

La chiave master di TDE, anche nota come *Protezione TDE*, viene impostata a livello di server. Per usare TDE con il supporto Bring Your Own Key e proteggere i database con una chiave di Azure Key Vault, passare alle impostazioni di TDE nel server. 

![TDE con il supporto BYOK](./media/transparent-data-encryption-azure-sql/tde-byok-support.png) 

## <a name="managing-transparent-data-encryption-using-powershell"></a>Gestione di Transparent Data Encryption usando PowerShell

Per configurare TDE tramite PowerShell è necessario essere connessi come proprietario, collaboratore o Gestore Sicurezza SQL di Azure. 

| Cmdlet | Description |
| --- | --- |
| [Set-AzureRmSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) |Abilita o disabilita TDE per un database.|
| [Get-Azure-Rm-Sql-Database-Transparent-Data-Encryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption) |Ottiene lo stato di TDE per un database. |
| [Get-Azure-Rm-Sql-Database-Transparent-Data-Encryption-Activity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity) |Controlla lo stato di crittografia per un database. |
| [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) |Aggiunge una chiave di Key Vault a un server SQL. |
| [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) |Ottiene le chiavi di Key Vault di un server SQL. |
| [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) |Imposta la Protezione TDE per un server SQL. |
| [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) |Ottiene la protezione Transparent Data Encryption (TDE). |
| [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) |Rimuove una chiave di Key Vault da un server SQL. |
|  | |

## <a name="managing-transparent-data-encryption-using-transact-sql"></a>Gestione di Transparent Data Encryption usando Transact-SQL

Connettersi al database con un account di accesso di amministratore o membro del ruolo **dbmanager** nel database master.

| Comando | Description |
| --- | --- |
| [ALTER DATABASE (database SQL di Azure)](/sql/t-sql/statements/alter-database-azure-sql-database) | Usare SET ENCRYPTION ON/OFF per crittografare o decrittografare un database. |
| [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) |Restituisce informazioni sullo stato di crittografia di un database e sulle chiavi di crittografia a esso associate. |
| [sys.dm_pdw_nodes_database_encryption_keys](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql) |Restituisce informazioni sullo stato di crittografia di ogni nodo del data warehouse e sulle chiavi di crittografia a esso associate. | 
|  | |

Non è possibile usare Transact-SQL per passare la Protezione TDE a una chiave di Azure Key Vault. Usare PowerShell o il portale di Azure.

## <a name="managing-transparent-data-encryption-using-rest-api"></a>Gestione di Transparent Data Encryption usando l'API REST
 
Per configurare TDE tramite l'API REST è necessario essere connessi come proprietario, collaboratore o Gestore Sicurezza SQL di Azure. 

| Comando | Description |
| --- | --- |
|[Create Or Update Server](/rest/api/sql/servers/createorupdate)|Aggiunge un'identità AAD a un server SQL (usato per concedere l'accesso a Key Vault).|
|[Create Or Update Server Key](/rest/api/sql/serverkeys/createorupdate)|Aggiunge una chiave di Key Vault a un server SQL.|
|[Delete Server Key](/rest/api/sql/serverkeys/delete)|Rimuove una chiave di Key Vault da un server SQL.|
|[Get Server Keys](/rest/api/sql/serverkeys/get)|Ottiene una chiave di Key Vault specifica da un server SQL.|
|[List Server Keys By Server](/rest/api/sql/serverkeys/listbyserver)|Ottiene le chiavi di Key Vault di un server SQL.|
|[Create Or Update Encryption Protector](/rest/api/sql/encryptionprotectors/createorupdate)|Imposta la Protezione TDE per un server SQL.|
|[Get Encryption Protector](/rest/api/sql/encryptionprotectors/get)|Ottiene la Protezione TDE per un server SQL.|
|[List Encryption Protectors By Server](/rest/api/sql/encryptionprotectors/listbyserver)|Ottiene le protezioni TDE di un server SQL.|
|[Create Or Update Transparent Data Encryption Configuration](/rest/api/sql/transparentdataencryptions/createorupdate)|Abilita o disabilita TDE per un database.|
|[Get Transparent Data Encryption Configuration](/rest/api/sql/transparentdataencryptions/get)|Ottiene la configurazione di TDE per un database.|
|[List Transparent Data Encryption Configuration Results](/rest/api/sql/transparentdataencryptionactivities/ListByConfiguration)|Ottiene il risultato della crittografia per un database.|

## <a name="next-steps"></a>Passaggi successivi

- Per una descrizione generale di TDE, vedere [Transparent Data Encryption (TDE)](transparent-data-encryption.md).

- Per altre informazioni su TDE con il supporto BYOK per il database SQL di Azure e Azure SQL Data Warehouse, vedere [Transparent Data Encryption with Bring Your Own Key support](transparent-data-encryption-byok-azure-sql.md) (Transparent Data Encryption con il supporto Bring Your Own Key).

- Per iniziare a usare TDE con il supporto BYOK, vedere la guida alle procedure [Turn on Transparent Data Encryption using your own key from Key Vault Using PowerShell](transparent-data-encryption-byok-azure-sql-configure.md) (Attivare Transparent Data Encryption con una chiave personalizzata di Key Vault usando PowerShell).

- Per altre informazioni su Key Vault, vedere la [pagina della documentazione di Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault).
