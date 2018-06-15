---
title: PowerShell - Ruotare la protezione TDE - Azure SQL | Microsoft Docs
description: Informazioni su come eseguire la rotazione della protezione Transparent Data Encryption (TDE) per un server SQL di Azure.
keywords: ''
services: sql-database
documentationcenter: ''
author: becczhang
manager: jhubbard
editor: ''
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.custom: ''
ms.component: security
ms.tgt_pltfrm: ''
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: ryzhang26
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: cee667b6f92c19c03cd670537d09dc5ccc7b03f3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32619272"
---
# <a name="rotate-the-transparent-data-encryption-tde-protector-using-powershell"></a>Ruotare la protezione Transparent Data Encryption (TDE) con PowerShell 
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

Questa guida alle procedure descrive la rotazione della chiave per un server SQL di Azure usando una protezione TDE di Azure Key Vault. Ruotare la protezione TDE di un server SQL di Azure significa passare a una nuova chiave asimmetrica che protegge i database presenti nel server. La rotazione delle chiavi è un'operazione online e richiede solo alcuni secondi, poiché si limita a decrittografare e crittografare nuovamente la chiave di crittografia dei dati del database, non dell'intero database.

In questa guida vengono illustrate due opzioni di rotazione della protezione TDE nel server.

> [!NOTE]
> Se un data warehouse SQL è in pausa, è necessario riprenderne l'esecuzione prima di ruotare le chiavi.
>

> [!IMPORTANT]
> **Non eliminare** le versioni precedenti della chiave dopo un rollover.  Con il rollover delle chiavi, alcuni dati vengono comunque crittografati usando le chiavi precedenti, ad esempio i backup più datati del database. 
>

## <a name="prerequisites"></a>Prerequisites

- In questa guida si presuppone che sia già in uso una chiave di Azure Key Vault come protezione TDE per un database o data warehouse SQL di Azure. Vedere l'articolo sull'uso di [Transparent Data Encryption con il supporto BYOK](transparent-data-encryption-byok-azure-sql.md).
- Azure PowerShell versione 3.7.0 o versioni successive deve essere installato e in esecuzione. 
- [Scelta consigliata ma facoltativa] Creare prima il materiale della chiave per la protezione TDE in un modulo di protezione hardware (HSM) o un archivio chiavi locale e importare il materiale della chiave in Azure Key Vault. Seguire le [istruzioni per l'uso di un modulo di protezione hardware e di Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started) per altre informazioni.

## <a name="option-1-auto-rotation"></a>Opzione 1: rotazione automatica

Generare una nuova versione della chiave di protezione TDE esistente in Key Vault usando lo stesso nome di chiave e lo stesso insieme di credenziali delle chiavi. Il servizio SQL Azure si avvia usando questa nuova versione entro 24 ore. 

Per creare una nuova versione della protezione TDE usando il cmdlet [Add-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/add-azurekeyvaultkey):

   ```powershell
   Add-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -Destination <HardwareOrSoftware>
   ```

## <a name="option-2-manual-rotation"></a>Opzione 2: rotazione manuale

L'opzione usa i cmdlet [Add-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/add-azurekeyvaultkey), [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) e [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) per aggiungere una chiave completamente nuova, che può essere indicata con un nuovo nome di chiave o persino un altro insieme di credenziali delle chiavi. 

>[!NOTE]
>La lunghezza combinata per il nome dell'insieme di credenziali delle chiavi e il nome della chiave non può superare 94 caratteri.
>

   ```powershell
   # Add a new key to Key Vault
   Add-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -Destination <HardwareOrSoftware>

   # Add the new key from Key Vault to the server
   Add-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>   
  
   <# Set the key as the TDE protector for all resources 
   under the server #>
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```
  
## <a name="other-useful-powershell-cmdlets"></a>Altri cmdlet utili di PowerShell

- Per passare la protezione TDE dalla modalità gestita da Microsoft alla modalità BYOK, usare il cmdlet [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector).

   ```powershell
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```

- Per passare la protezione TDE dalla modalità BYOK alla modalità gestita da Microsoft, usare il cmdlet [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector).

   ```powershell
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type ServiceManaged `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName> 
   ``` 

## <a name="next-steps"></a>Passaggi successivi

- In caso di rischi per la sicurezza, vedere le indicazioni su come [rimuovere una protezione TDE potenzialmente compromessa](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md) 

- Per un'introduzione al supporto Bring Your Own Key (BYOK) per TDE, vedere [PowerShell: abilitare TDE usando la propria chiave di Azure Key Vault](transparent-data-encryption-byok-azure-sql-configure.md)
