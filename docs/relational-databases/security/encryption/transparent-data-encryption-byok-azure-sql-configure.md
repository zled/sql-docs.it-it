---
title: 'PowerShell e CLI: abilitare TDE di SQL usando la propria chiave di Azure Key Vault | Microsoft Docs'
description: Informazioni sulla configurazione di un database SQL di Azure e di Data Warehouse per iniziare a usare Transparent Data Encryption (TDE) per crittografare i dati inattivi con PowerShell o CLI.
keywords: ''
documentationcenter: ''
author: aliceku
manager: craigg
editor: ''
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.tgt_pltfrm: ''
ms.devlang: azurecli, powershell
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: aliceku
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 5b6a5d6eafc76b80a169332f8c71309440c4ef0f
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37093315"
---
# <a name="powershell-and-cli-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vault"></a>PowerShell e CLI: abilitare Transparent Data Encryption usando la propria chiave di Azure Key Vault

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

Questa guida alle procedure spiega come usare una chiave di Azure Key Vault per Transparent Data Encryption (TDE) in un database o data warehouse SQL. Per altre informazioni su TDE con supporto BYOK (Bring Your Own Key), consultare l'articolo relativo all'[uso di TDE con supporto BYOK per Azure SQL](transparent-data-encryption-byok-azure-sql.md). 

## <a name="prerequisites-for-powershell"></a>Prerequisiti per PowerShell

- È necessario avere una sottoscrizione di Azure ed essere un amministratore per tale sottoscrizione.
- [Scelta consigliata ma facoltativa] Usare un modulo di protezione hardware (HSM) o un archivio chiavi locale per creare una copia locale del materiale della chiave di protezione TDE.
- Azure PowerShell versione 4.2.0 o versioni successive deve essere installato e in esecuzione. 
- Creare un insieme di credenziali delle chiavi e una chiave da usare per TDE in Azure Key Vault.
   - [Istruzioni per l'uso di Key Vault con PowerShell](https://docs.microsoft.com/azure/key-vault/key-vault-get-started)
   - [Istruzioni per l'uso di un modulo di protezione hardware e Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
 - L'insieme di credenziali delle chiavi deve avere la proprietà seguente per essere usato per TDE:
   - [Eliminazione temporanea](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-ovw-soft-delete)
   - [Come usare l'eliminazione temporanea di Key Vault con PowerShell](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-soft-delete-powershell) 
- La chiave deve avere i seguenti attributi per essere usata per TDE:
   - Nessuna data di scadenza
   - Non disabilitata
   - In grado di eseguire operazioni *get*, *wrap key*, *unwrap key*

## <a name="step-1-assign-an-azure-ad-identity-to-your-server"></a>Passaggio 1. Assegnare un'identità Azure AD al server 

Se si usa un server esistente, aggiungere un'identità Azure AD al server nel modo seguente:

   ```powershell
   $server = Set-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -AssignIdentity
   ```

Se si sta creando un server, usare il cmdlet [New-AzureRmSqlServer](/powershell/module/azurerm.sql/new-azurermsqlserver) con il tag -Identity per aggiungere un'identità Azure AD durante la creazione del server:

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

Usare il cmdlet [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) per concedere l'accesso al server all'insieme di credenziali delle chiavi prima di usare una chiave dell'insieme per TDE.

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
>KeyId di esempio da Key Vault: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h
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

## <a name="step-5-check-the-encryption-state-and-encryption-activity"></a>Passaggio 5. Controllare lo stato e l'attività di crittografia

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

## <a name="prerequisites-for-cli"></a>Prerequisiti per CLI

- È necessario avere una sottoscrizione di Azure ed essere un amministratore per tale sottoscrizione.
- [Scelta consigliata ma facoltativa] Usare un modulo di protezione hardware (HSM) o un archivio chiavi locale per creare una copia locale del materiale della chiave di protezione TDE.
- Interfaccia della riga di comando 2.0 o versione successiva. Per installare la versione più recente e connettersi alla sottoscrizione di Azure, vedere [Installare l'interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest). 
- Creare un insieme di credenziali delle chiavi e una chiave da usare per TDE in Azure Key Vault.
   - [Gestire Key Vault tramite l'interfaccia della riga di comando 2.0](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-manage-with-cli2)
   - [Istruzioni per l'uso di un modulo di protezione hardware e Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
 - L'insieme di credenziali delle chiavi deve avere la proprietà seguente per essere usato per TDE:
   - [Eliminazione temporanea](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-ovw-soft-delete)
   - [Come usare l'eliminazione temporanea di Key Vault con l'interfaccia della riga di comando](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-soft-delete-cli) 
- La chiave deve avere i seguenti attributi per essere usata per TDE:
   - Nessuna data di scadenza
   - Non disabilitata
   - In grado di eseguire operazioni *get*, *wrap key*, *unwrap key*
   
## <a name="step-1-create-a-server-and-assign-an-azure-ad-identity-to-your-server"></a>Passaggio 1. Creare un server e assegnare a tale server un'identità Azure AD
      cli
      # create server (with identity) and database
      az sql server create -n "ServerName" -g "ResourceGroupName" -l "westus" -u "cloudsa" -p "YourFavoritePassWord99@34" -I 
      az sql db create -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 
      

 
## <a name="step-2-grant-key-vault-permissions-to-your-server"></a>Passaggio 2. Concedere al server le autorizzazioni per l'insieme di credenziali delle chiavi
      cli
      # create key vault, key and grant permission
      az keyvault create -n "VaultName" -g "ResourceGroupName" 
      az keyvault key create -n myKey -p software --vault-name "VaultName" 
      az keyvault set-policy -n "VaultName" --object-id "ServerIdentityObjectId" -g "ResourceGroupName" --key-permissions wrapKey unwrapKey get list 
      

 
## <a name="step-3-add-the-key-vault-key-to-the-server-and-set-the-tde-protector"></a>Passaggio 3. Aggiungere la chiave di Key Vault al server e impostare la protezione TDE
  
     cli
     # add server key and update encryption protector
      az sql server key create -g "ResourceGroupName" -s "ServerName" -t "AzureKeyVault" -u "FullVersionedKeyUri 
      az sql server tde-key update -g "ResourceGroupName" -s "ServerName" -t AzureKeyVault -u "FullVersionedKeyUri" 
      
  
  > [!Note]
> La lunghezza combinata per il nome dell'insieme di credenziali delle chiavi e il nome della chiave non può superare 94 caratteri.
> 

>[!Tip]
>KeyId di esempio da Key Vault: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h
>
  
## <a name="step-4-turn-on-tde"></a>Passaggio 4. Attivare TDE 
      cli
      # enable encryption
      az sql db tde create -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" --status Enabled 
      

Ora TDE è abilitato per il database o data warehouse con una chiave di crittografia in Key Vault.

## <a name="step-5-check-the-encryption-state-and-encryption-activity"></a>Passaggio 5. Controllare lo stato e l'attività di crittografia

     cli
      # get encryption scan progress
      az sql db tde show-activity -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 

      # get whether encryption is on or off
      az sql db tde show-configuration -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 

## <a name="sql-cli-references"></a>Informazioni di riferimento sull'interfaccia della riga di comando di SQL

https://docs.microsoft.com/en-us/cli/azure/sql?view=azure-cli-latest 

https://docs.microsoft.com/en-us/cli/azure/sql/server/key?view=azure-cli-latest 

https://docs.microsoft.com/en-us/cli/azure/sql/server/tde-key?view=azure-cli-latest 

https://docs.microsoft.com/en-us/cli/azure/sql/db/tde?view=azure-cli-latest 

