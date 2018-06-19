---
title: PowerShell - Rimuovere la protezione TDE - Azure SQL | Microsoft Docs
description: Guida alle procedure da seguire per rispondere a una protezione TDE potenzialmente compromessa per un database o data warehouse SQL di Azure usando TDE con il supporto BYOK (Bring Your Own Key).
keywords: ''
services: sql-database
documentationcenter: ''
author: becczhang
manager: craigg
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.custom: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.date: 08/07/2017
ms.author: rebeccaz
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: d498331b409732ab741b59122567959c1175f249
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35699712"
---
# <a name="remove-a-transparent-data-encryption-tde-protector-using-powershell"></a>Rimuovere una protezione Transparent Data Encryption (TDE) con PowerShell
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

## <a name="prerequisites"></a>Prerequisites
- È necessario avere una sottoscrizione di Azure ed essere un amministratore per tale sottoscrizione
- Azure PowerShell versione 4.2.0 o versioni successive deve essere installato e in esecuzione. 
- In questa guida si presuppone che sia già in uso una chiave di Azure Key Vault come protezione TDE per un database o data warehouse SQL di Azure. Per altre informazioni, vedere l'articolo sull'uso di [Transparent Data Encryption con il supporto BYOK](transparent-data-encryption-byok-azure-sql.md).

## <a name="overview"></a>Panoramica
Questa guida descrive le procedure da seguire per rispondere a una protezione TDE potenzialmente compromessa per un database o data warehouse SQL di Azure che usa TDE con il supporto BYOK (Bring Your Own Key). Per altre informazioni sul supporto BYOK per TDE, vedere la [pagina Panoramica](transparent-data-encryption-byok-azure-sql.md). 

Le procedure seguenti devono essere eseguite solo in casi estremi o in ambienti di test. Leggere attentamente la guida alle procedure, poiché l'eliminazione di protezioni TDE in uso da Azure Key Vault può comportare la **perdita di dati**. 

Se si sospetta che una chiave sia compromessa e che per questo un servizio o un utente ha eseguito l'accesso non autorizzato alla chiave, è consigliabile eliminare la chiave.

Tenere presente che dal momento in cui la protezione TDE viene eliminata in Key Vault, **tutte le connessioni ai database crittografati nel server vengono bloccate e i database vengono portati offline ed eliminati entro 24 ore**. I backup meno recenti crittografati con la chiave compromessa non sono più accessibili.

Questa guida descrive due approcci, in base al risultato che si vuole ottenere dopo la risposta all'evento imprevisto:
- Mantenere i database/data warehouse SQL di Azure **accessibili**
- Mantenere i database/data warehouse SQL di Azure **inaccessibili**

## <a name="to-keep-the-encrypted-resources-accessible"></a>Per mantenere accessibili le risorse crittografate
1. Creare una [nuova chiave nell'insieme di credenziali delle chiavi](https://docs.microsoft.com/powershell/module/azurerm.keyvault/add-azurekeyvaultkey?view=azurermps-4.1.0). Verificare che la nuova chiave venga creata in un insieme di credenziali delle chiavi separato dalla protezione TDE potenzialmente compromessa, poiché il provisioning del controllo di accesso viene eseguito a livello di insieme di credenziali. 
2. Aggiungere la nuova chiave al server usando i cmdlet [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) e [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) e aggiornarla come nuova protezione TDE del server.

   ```powershell
   # Add the key from Key Vault to the server  
   Add-AzureRmSqlServerKeyVaultKey `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -KeyId <KeyVaultKeyId>
   
   # Set the key as the TDE protector for all resources under the server
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -Type AzureKeyVault -KeyId <KeyVaultKeyId> 
   ```

3. Verificare che il server ed eventuali repliche siano stati aggiornati alla nuova protezione TDE usando il cmdlet [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector). 

   >[!NOTE]
   > Possono trascorrere alcuni minuti prima che la nuova protezione TDE venga propagata a tutti i database e i database secondari nel server.
   >

   ```powershell
   Get-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>
   ```

4. Tenere una copia di [backup della nuova chiave](/powershell/module/azurerm.keyvault/backup-azurekeyvaultkey) in Key Vault.

   ```powershell
   <# -OutputFile parameter is optional; 
   if removed, a file name is automatically generated. #>
   Backup-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -OutputFile <DesiredBackupFilePath>
   ```
 
5. Eliminare la chiave compromessa da Key Vault usando il cmdlet [Remove-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/remove-azurekeyvaultkey). 

   ```powershell
   Remove-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName>
   ```
 
6. Per ripristinare in futuro una chiave in Key Vault usando il cmdlet [Restore-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/restore-azurekeyvaultkey):
   ```powershell
   Restore-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -InputFile <BackupFilePath>
   ```
 
## <a name="to-make-the-encrypted-resources-inaccessible"></a>Per rendere inaccessibili le risorse crittografate
1. Eliminare i database crittografati con la chiave potenzialmente compromessa.
Poiché viene automaticamente eseguito il backup dei file di database e di log, un ripristino temporizzato del database può essere eseguito in qualsiasi momento, purché venga specificata la chiave. I database devono essere eliminati prima di eliminare una protezione TDE attiva per evitare potenziali perdite di dati di fino a 10 minuti delle transazioni più recenti. 
2. Eseguire il backup del materiale della chiave della protezione TDE in Key Vault.
3. Rimuovere la chiave potenzialmente compromessa da Key Vault

## <a name="next-steps"></a>Passaggi successivi

- Informazioni su come eseguire la rotazione della protezione TDE di un server per soddisfare i requisiti di sicurezza: [Ruotare la protezione Transparent Data Encryption (TDE) con PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md)

- Per un'introduzione al supporto Bring Your Own Key (BYOK) per TDE, vedere [PowerShell: abilitare TDE usando la propria chiave di Azure Key Vault](transparent-data-encryption-byok-azure-sql-configure.md)
