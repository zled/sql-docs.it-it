---
title: Transparent Data Encryption per il database SQL di Azure e Azure SQL Data Warehouse | Microsoft Docs
description: Panoramica di Transparent Data Encryption per database e data warehouse SQL. Il documento illustra i vantaggi della tecnologia e le opzioni per la configurazione, incluse le funzionalità Transparent Data Encryption gestita dal servizio e Bring Your Own Key.
keywords: ''
author: becczhang
manager: craigg
editor: ''
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.component: security
ms.custom: ''
ms.workload: On Demand
ms.tgt_pltfrm: ''
ms.topic: article
ms.date: 04/10/2018
ms.author: rebeccaz
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: fd5186e4a069b76108ad0c8cd4e91497e618a195
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="transparent-data-encryption-for-sql-database-and-data-warehouse"></a>Transparent Data Encryption per database e data warehouse SQL
[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Transparent Data Encryption contribuisce a proteggere il database SQL di Azure e Azure Data Warehouse dagli attacchi di attività dannose. Esegue la crittografia e la decrittografia in tempo reale del database, dei backup associati e dei file di log delle transazioni inattivi senza richiedere modifiche all'applicazione.

Transparent Data Encryption crittografa l'archivio di un intero database usando una chiave simmetrica denominata chiave di crittografia del database. La chiave di crittografia del database è protetta dalla protezione di Transparent Data Encryption. La protezione può essere un certificato gestito dal servizio (Transparent Data Encryption gestita dal servizio) o una chiave asimmetrica archiviata in Azure Key Vault (Bring Your Own Key). La protezione di Transparent Data Encryption si imposta a livello di server. 

All'avvio del database, la chiave di crittografia crittografata viene decrittografata e quindi usata per decrittografare e ricrittografare i file di database nel processo del motore di database di SQL Server. Transparent Data Encryption esegue la crittografia e la decrittografia I/O in tempo reale dei dati a livello di pagina. Ogni pagina viene decrittografata quando viene letta nella memoria e quindi crittografata prima di essere scritta su disco. Per una descrizione generale di Transparent Data Encryption, vedere [Transparent Data Encryption](transparent-data-encryption.md).

Per SQL Server in esecuzione in una macchina virtuale di Azure è anche possibile usare una chiave asimmetrica di Key Vault. I passaggi di configurazione sono diversi rispetto all'uso di una chiave asimmetrica nel database SQL. Per altre informazioni, vedere [Extensible Key Management tramite l'insieme di credenziali delle chiavi di Azure (SQL Server)](extensible-key-management-using-azure-key-vault-sql-server.md).

## <a name="service-managed-transparent-data-encryption"></a>Transparent Data Encryption gestita dal servizio

In Azure l'impostazione predefinita di Transparent Data Encryption prevede che la chiave di crittografia del database sia protetta da un certificato predefinito del server. Il certificato predefinito del server è univoco per ogni server. Se un database è in una relazione di replica geografica, il database primario e il database di replica geografica secondaria sono protetti dalla chiave del server padre del database primario. Se due database sono connessi allo stesso server, condividono lo stesso certificato predefinito. Microsoft ruota automaticamente questi certificati almeno ogni 90 giorni.

Microsoft inoltre sposta e gestisce le chiavi in base alle esigenze per la replica geografica e i ripristini. 

> [!IMPORTANT]
> Tutti i nuovi database SQL vengono crittografati per impostazione predefinita usando la funzionalità Transparent Data Encryption gestita dal servizio. I database esistenti prima di maggio 2017 e quelli creati con una procedura di ripristino, replica geografica e copia del database non vengono crittografati per impostazione predefinita.
>

## <a name="bring-your-own-key"></a>Bring Your Own Key

Il supporto Bring Your Own Key consente all'utente di assumere il controllo delle proprie chiavi di Transparent Data Encryption e di stabilire chi può accedervi e quando. Key Vault, ovvero il sistema di gestione delle chiavi esterne basato sul cloud di Azure, è il primo servizio di gestione delle chiavi con cui è stato integrato Transparent Data Encryption per il supporto Bring Your Own Key. Con il supporto Bring Your Own Key, la chiave di crittografia del database è protetta da una chiave asimmetrica archiviata in Key Vault. La chiave asimmetrica non viene mai rimossa da Key Vault. Quando il server ottiene le autorizzazioni per un insieme di credenziali delle chiavi, invia a tale insieme le richieste di operazioni di base relative alle chiavi attraverso Key Vault. La chiave asimmetrica viene impostata a livello di server ed ereditata da tutti i database presenti nel server.

Con il supporto Bring Your Own Key ora è possibile controllare le attività di gestione delle chiavi, ad esempio le rotazioni delle chiavi e le autorizzazioni dell'insieme di credenziali delle chiavi. È anche possibile eliminare le chiavi e abilitare il controllo o il reporting per tutte le chiavi di crittografia. Key Vault offre una gestione centrale delle chiavi e usa moduli di protezione hardware accuratamente monitorati. Key Vault alza di livello la separazione della gestione delle chiavi e dei dati per consentire il rispetto delle conformità alle normative. Per altre informazioni su Key Vault, vedere la [pagina della documentazione di Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault).

Per altre informazioni su Transparent Data Encryption con il supporto Bring Your Own Key per database e data warehouse SQL, vedere [Transparent Data Encryption con supporto Bring Your Own Key](transparent-data-encryption-byok-azure-sql.md).

Per iniziare a usare Transparent Data Encryption con il supporto Bring Your Own Key, vedere la guida alle procedure [PowerShell: abilitare Transparent Data Encryption usando la propria chiave di Azure Key Vault (anteprima)](transparent-data-encryption-byok-azure-sql-configure.md).

## <a name="move-a-transparent-data-encryption-protected-database"></a>Spostare un database protetto con Transparent Data Encryption

Non è necessario decrittografare i database per eseguire operazioni all'interno di Azure. Le impostazioni di Transparent Data Encryption nel database di origine o nel database primario vengono ereditate in modo trasparente nel database di destinazione. Queste sono alcune delle operazioni incluse:
- Ripristino geografico.
- Ripristino temporizzato self-service.
- Ripristino di un database eliminato.
- Replica geografica attiva.
- Creazione di una copia del database.

Quando si esporta un database protetto con Transparent Data Encryption, il contenuto esportato del database non viene crittografato. Questo contenuto esportato viene archiviato in file BACPAC non crittografati. Verificare che i file BACPAC siano protetti in modo appropriato e abilitare Transparent Data Encryption al termine dell'importazione del nuovo database.

Ad esempio, se il file BACPAC viene esportato da un'istanza locale di SQL Server, il contenuto importato del nuovo database non viene automaticamente crittografato. Allo stesso modo, se il file BACPAC viene esportato in un'istanza locale di SQL Server, il nuovo database non viene automaticamente crittografato.

L'unica eccezione riguarda l'esportazione da e verso un database SQL. Transparent Data Encryption è abilitata nel nuovo database, ma il file BACPAC non viene comunque crittografato.

## <a name="manage-transparent-data-encryption-in-the-azure-portal"></a>Gestire Transparent Data Encryption nel portale di Azure

Per configurare Transparent Data Encryption nel portale di Azure, è necessario essere connessi come proprietario, collaboratore o Gestore Sicurezza SQL di Azure. 

Impostare Transparent Data Encryption a livello di database. Per abilitare Transparent Data Encryption in un database, accedere al [portale di Azure](https://portal.azure.com) con l'account di amministratore o collaboratore di Azure. Individuare le impostazioni di Transparent Data Encryption nel database utente. Per impostazione predefinita viene usata la funzionalità Transparent Data Encryption gestita dal servizio. Viene automaticamente generato un certificato di Transparent Data Encryption per il server che contiene il database. 

![Transparent Data Encryption gestita dal servizio](./media/transparent-data-encryption-azure-sql/service-managed-tde.png)  

Impostare la chiave master, nota anche come protezione, di Transparent Data Encryption a livello di server. Per usare Transparent Data Encryption con il supporto Bring Your Own Key e proteggere i database con una chiave di Key Vault, vedere le impostazioni di Transparent Data Encryption del server in uso. 

![Transparent Data Encryption con supporto Bring Your Own Key](./media/transparent-data-encryption-azure-sql/tde-byok-support.png) 

## <a name="manage-transparent-data-encryption-by-using-powershell"></a>Gestire Transparent Data Encryption con PowerShell

Per configurare Transparent Data Encryption usando PowerShell, è necessario essere connessi come proprietario, collaboratore o Gestore Sicurezza SQL di Azure. 

| Cmdlet | Description |
| --- | --- |
| [Set-AzureRmSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) |Abilita o disabilita Transparent Data Encryption per un database|
| [Get-Azure-Rm-Sql-Database-Transparent-Data-Encryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption) |Ottiene lo stato di Transparent Data Encryption per un database |
| [Get-Azure-Rm-Sql-Database-Transparent-Data-Encryption-Activity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity) |Controlla l'avanzamento della crittografia per un database |
| [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) |Aggiunge una chiave di Key Vault a un'istanza di SQL Server |
| [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) |Ottiene le chiavi di Key Vault per un'istanza di SQL Server  |
| [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) |Imposta la protezione di Transparent Data Encryption per un'istanza di SQL Server |
| [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) |Ottiene la protezione di Transparent Data Encryption |
| [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) |Rimuove una chiave di Key Vault da un'istanza di SQL Server |
|  | |

## <a name="manage-transparent-data-encryption-by-using-transact-sql"></a>Gestire Transparent Data Encryption con Transact-SQL

Connettersi al database con un account di accesso di amministratore o membro del ruolo **dbmanager** nel database master.

| Comando | Description |
| --- | --- |
| [ALTER DATABASE (database SQL di Azure)](/sql/t-sql/statements/alter-database-azure-sql-database) | SET ENCRYPTION ON/OFF consente di crittografare o decrittografare un database |
| [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) |Restituisce informazioni sullo stato della crittografia di un database e sulle chiavi di crittografia del database associate |
| [sys.dm_pdw_nodes_database_encryption_keys](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql) |Restituisce informazioni sullo stato della crittografia di ogni nodo del data warehouse e sulle chiavi di crittografia del database associate | 
|  | |

Non è possibile passare dalla protezione di Transparent Data Encryption a una chiave di Key Vault usando Transact-SQL. Usare PowerShell o il portale di Azure.

## <a name="manage-transparent-data-encryption-by-using-the-rest-api"></a>Gestire Transparent Data Encryption con l'API REST
 
Per configurare Transparent Data Encryption usando l'API REST, è necessario essere connessi come proprietario, collaboratore o Gestore Sicurezza SQL di Azure. 

| Comando | Description |
| --- | --- |
|[Create Or Update Server](/rest/api/sql/servers/createorupdate)|Aggiunge un'identità di Azure Active Directory a un'istanza di SQL Server (usata per concedere accesso a Key Vault)|
|[Create Or Update Server Key](/rest/api/sql/serverkeys/createorupdate)|Aggiunge una chiave di Key Vault a un'istanza di SQL Server|
|[Delete Server Key](/rest/api/sql/serverkeys/delete)|Rimuove una chiave di Key Vault da un'istanza di SQL Server|
|[Get Server Keys](/rest/api/sql/serverkeys/get)|Ottiene una chiave di Key Vault specifica da un'istanza di SQL Server|
|[List Server Keys By Server](/rest/api/sql/serverkeys/listbyserver)|Ottiene le chiavi di Key Vault per un'istanza di SQL Server |
|[Create Or Update Encryption Protector](/rest/api/sql/encryptionprotectors/createorupdate)|Imposta la protezione di Transparent Data Encryption per un'istanza di SQL Server|
|[Get Encryption Protector](/rest/api/sql/encryptionprotectors/get)|Ottiene la protezione di Transparent Data Encryption per un'istanza di SQL Server|
|[List Encryption Protectors By Server](/rest/api/sql/encryptionprotectors/listbyserver)|Ottiene le protezioni di Transparent Data Encryption per un'istanza di SQL Server |
|[Create Or Update Transparent Data Encryption Configuration](/rest/api/sql/transparentdataencryptions/createorupdate)|Abilita o disabilita Transparent Data Encryption per un database|
|[Get Transparent Data Encryption Configuration](/rest/api/sql/transparentdataencryptions/get)|Ottiene la configurazione di Transparent Data Encryption per un database|
|[List Transparent Data Encryption Configuration Results](/rest/api/sql/transparentdataencryptionactivities/ListByConfiguration)|Ottiene il risultato della crittografia per un database|

## <a name="next-steps"></a>Passaggi successivi

- Per una descrizione generale di Transparent Data Encryption, vedere [Transparent Data Encryption](transparent-data-encryption.md).
- Per altre informazioni su Transparent Data Encryption con il supporto Bring Your Own Key per database e data warehouse SQL, vedere [Transparent Data Encryption con supporto Bring Your Own Key](transparent-data-encryption-byok-azure-sql.md).
- Per iniziare a usare Transparent Data Encryption con il supporto Bring Your Own Key, vedere la guida alle procedure [PowerShell: abilitare Transparent Data Encryption usando la propria chiave di Azure Key Vault (anteprima)](transparent-data-encryption-byok-azure-sql-configure.md).
- Per altre informazioni su Key Vault, vedere la [pagina della documentazione di Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault).
