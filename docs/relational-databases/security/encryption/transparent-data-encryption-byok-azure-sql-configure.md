---
title: 'PowerShell: abilitare TDE usando la propria chiave di Azure Key Vault | Microsoft Docs'
description: Informazioni sulla configurazione di un database e un data warehouse SQL di Azure per iniziare a usare Transparent Data Encryption (TDE) per crittografare i dati inattivi con PowerShell.
keywords: 
services: sql-database
documentationcenter: 
author: becczhang
manager: jhubbard
editor: 
ms.assetid: 
ms.service: sql-database
ms.custom: security
ms.workload: Inactive
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: rebeccaz
ms.translationtype: HT
ms.sourcegitcommit: 46b16dcf147dbd863eec0330e87511b4ced6c4ce
ms.openlocfilehash: cf8f46ab01c08e68fa22f65a4f86f4ff16f16ba3
ms.contentlocale: it-it
ms.lasthandoff: 09/05/2017

---


# <a name="powershell-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vault"></a>PowerShell: abilitare Transparent Data Encryption usando la propria chiave di Azure Key Vault

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Questa guida alle procedure spiega come usare una chiave di Azure Key Vault per Transparent Data Encryption (TDE) in un database o data warehouse SQL. Per altre informazioni su TDE con supporto BYOK (Bring Your Own Key), consultare l'articolo relativo all'[uso di TDE con supporto BYOK per Azure SQL](transparent-data-encryption-byok-azure-sql.md). 

## <a name="prerequisites"></a>Prerequisiti

- È necessario avere una sottoscrizione di Azure ed essere un amministratore per tale sottoscrizione.
- [Scelta consigliata ma facoltativa] Usare un modulo di protezione hardware (HSM) o un archivio chiavi locale per creare una copia locale del materiale della chiave di protezione TDE.
- Azure PowerShell versione 4.2.0 o versioni successive deve essere installato e in esecuzione. 
- Creare un insieme di credenziali delle chiavi e una chiave da usare per TDE in Azure Key Vault.
   - [Istruzioni per l'uso di Key Vault con PowerShell](https://docs.microsoft.com/azure/key-vault/key-vault-get-started)
   - [Istruzioni per l'uso di un modulo di protezione hardware e Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
- La chiave deve avere i seguenti attributi per essere usata per TDE:
   - Nessuna data di scadenza
   - Non disabilitata
   - In grado di eseguire operazioni *get*, *wrap key*, *unwrap key*

## <a name="step-1-assign-an-aad-identity-to-your-server"></a>Passaggio 1. Assegnare un'identità AAD al server 

Se si usa un server già esistente, aggiungere un'identità AAD al server nel modo seguente:

   ```powershell
   $server = Set-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -AssignIdentity
   ```

Se si crea un server, usare il cmdlet [New-AzureRmSqlServer](/powershell/module/azurerm.sql/new-azurermsqlserver) con il tag -Identity per aggiungere un'identità AAD durante la creazione del server:

   ```powershell
   $server = New-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -Location <RegionName> `
   -ServerName <LogicalServerName> `
   -ServerVersion "12.0" `
   -SqlAdministratorCredentials <PSCredential> `
   -AssignIdentity 
   ```

## <a name="step-2-grant-key-vault-permissions-to-your-server"></a>Passaggio 2. Concedere al server le autorizzazioni per l'insieme di credenziali delle chiavi

Usare il cmdlet [Set AzureRmKeyValutAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) per concedere l'accesso al server all'insieme di credenziali delle chiavi prima di usare una chiave dell'insieme per TDE.

   ```powershell
   Set-AzureRmKeyVaultAccessPolicy  `
   -VaultName <KeyVaultName> `
   -ObjectId $server.Identity.PrincipalId `
   -PermissionsToKeys get, wrapKey, unwrapKey
   ```

## <a name="step-3-add-the-key-vault-key-to-the-server-and-set-the-tde-protector"></a>Passaggio 3. Aggiungere la chiave di Key Vault al server e impostare la protezione TDE

- Usare il cmdlet [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) per aggiungere al server la chiave di Key Vault.
- Usare il cmdlet [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) per impostare la chiave come protezione TDE per tutte le risorse del server.
- Usare il cmdlet [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) per verificare se la protezione TDE è stata configurata nel modo previsto.

> [!Note]
> La lunghezza combinata per il nome dell'insieme di credenziali delle chiavi e il nome della chiave non può superare 94 caratteri.
> 

>[!Tip]
>Un esempio di ID chiave di Key Vault: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h
>

   ```powershell
   <# Add the key from Key Vault to the server #>
   Add-AzureRmSqlServerKeyVaultKey `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -KeyId <KeyVaultKeyId>

   <# Set the key as the TDE protector for all resources under the server #>
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> 

   <# To confirm that the TDE protector was configured as intended: #>
   Get-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> 
   ```

## <a name="step-4-turn-on-tde"></a>Passaggio 4. Attivare TDE 

Usare il cmdlet [Set-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) per attivare TDE.

   ```powershell
   Set-AzureRMSqlDatabaseTransparentDataEncryption `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName> `
   -State "Enabled"
   ```

Ora TDE è abilitato per il database o data warehouse con una chiave di crittografia in Key Vault.

## <a name="step-5-check-the-encryption-state-and-encryption-activity-of-the-database-or-data-warehouse"></a>Passaggio 5. Controllare lo stato della crittografia e l'attività di crittografia del database o data warehouse

Usare [Get-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption) per ottenere la crittografia e [Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity) per verificare l'avanzamento della crittografia per un database o data warehouse.

   ```powershell
   # Get the encryption state
   Get-AzureRMSqlDatabaseTransparentDataEncryption `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName> `

   <# Check the encryption progress for a database or data warehouse #>
   Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName>  
   ```

## <a name="other-useful-powershell-cmdlets"></a>Altri cmdlet utili di PowerShell

- Usare il cmdlet [Set-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) per disattivare TDE.

   ```powershell
   Set-AzureRMSqlDatabaseTransparentDataEncryption `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -DatabaseName <DatabaseName> `
   -State "Disabled”
   ```
 
- Usare il cmdlet [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) per restituire l'elenco delle chiavi di Key Vault aggiunte al server.

   ```powershell
   <# KeyId is an optional parameter, to return a specific key version #>
   Get-AzureRmSqlServerKeyVaultKey `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>
   ```
 
- Usare il cmdlet [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) per rimuovere una chiave di Key Vault dal server.

   ```powershell
   <# The key set as the TDE Protector cannot be removed. #>
   Remove-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>   
   ```
 
## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verifica un problema, controllare quanto segue:
- Se non si trova l'insieme di credenziali delle chiavi, verificare se la sottoscrizione è quella giusta usando il cmdlet [Get AzureRmSubscription](/powershell/module/azurerm.profile/get-azurermsubscription).

   ```powershell
   Get-AzureRmSubscription `
   -SubscriptionId <SubscriptionId>
   ```

- Se non è possibile aggiungere la nuova chiave al server o la nuova chiave non può essere aggiornata come protezione TDE, verificare quanto segue:
   - La chiave non deve avere una data di scadenza
   - Per la chiave devono essere abilitate le operazioni *get*, *wrap key* e *unwrap key*.

## <a name="next-steps"></a>Passaggi successivi

- Informazioni su come eseguire la rotazione della protezione TDE di un server per soddisfare i requisiti di sicurezza: [Ruotare la protezione Transparent Data Encryption (TDE) con PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md).
- In caso di rischi per la sicurezza, vedere le indicazioni su come [rimuovere una protezione TDE potenzialmente compromessa](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md). 



