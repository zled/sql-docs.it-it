---
title: La gestione di SQL Server in Linux con PowerShell | Documenti Microsoft
description: In questo articolo viene fornita una panoramica dell'utilizzo di PowerShell in Windows con SQL Server in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 54892a66cea7643d708bcd7ba5cf1b6b07d4523f
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Utilizzo di PowerShell in Windows per la gestione di SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo descrive [SQL Server PowerShell](https://msdn.microsoft.com/en-us/library/mt740629.aspx) e illustra alcuni esempi su come utilizzarlo con 2017 di SQL Server in Linux. Supporto di PowerShell per SQL Server è attualmente disponibile in Windows, pertanto è possibile utilizzare quando si dispone di un computer Windows in grado di connettersi a un'istanza remota di SQL Server in Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Installare la versione più recente di SQL PowerShell in Windows

[SQL PowerShell](https://msdn.microsoft.com/en-us/library/mt740629.aspx) in Windows è incluso con [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md). Quando si utilizza SQL Server, è necessario utilizzare sempre la versione più recente di SQL Server Management Studio e SQL PowerShell. La versione più recente di SQL Server Management Studio viene aggiornata continuamente, ottimizzazione e attualmente funziona con SQL Server Linux su 2017. Per scaricare e installare la versione più recente, vedere [scaricare SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Per rimanere aggiornati, la versione più recente di SSMS chiede di quando è disponibile una nuova versione disponibile per il download.

## <a name="before-you-begin"></a>Operazioni preliminari

Lettura di [problemi noti](sql-server-linux-release-notes.md) per SQL Server, 2017 in Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Avviare PowerShell e importare il *sqlserver* modulo

Per iniziare, l'avvio di PowerShell in Windows. Aprire un *prompt dei comandi* nel computer Windows e digitare **PowerShell** per avviare una nuova sessione di Windows PowerShell.

```
PowerShell
```

SQL Server fornisce un modulo di Windows PowerShell denominato **SqlServer** che è possibile utilizzare per importare i componenti di SQL Server (provider di SQL Server e i cmdlet) in un ambiente di PowerShell o script.

Copiare e incollare il comando seguente al prompt di PowerShell per importare il **SqlServer** modulo nella sessione corrente di PowerShell:

```powershell
Import-Module SqlServer
```

Digitare il comando seguente al prompt di PowerShell per verificare che il **SqlServer** modulo è stato importato correttamente:

```powershell
Get-Module -Name SqlServer
```

PowerShell deve visualizzare informazioni simili all'output seguente:

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     0.0        SqlServer
Manifest   20.0       SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Connettersi a SQL Server e ottenere informazioni sul server

Utilizziamo PowerShell in Windows per connettersi all'istanza di SQL Server 2017 su Linux e visualizzare un paio di proprietà del server.

Copiare e incollare i comandi seguenti al prompt di PowerShell. Quando si eseguono questi comandi, verrà PowerShell:
- Visualizzazione di *richiesta delle credenziali di Windows PowerShell* finestra di dialogo in cui vengono richieste le credenziali (*nome utente SQL* e *password SQL*) a cui connettersi il 2017 di SQL Server istanza in Linux
- Caricare l'assembly di SQL Server Management Objects (SMO)
- Creare un'istanza di [Server](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.smo.server.aspx) oggetto
- Connettere il **Server** e visualizzare alcune proprietà

Ricordarsi di sostituire **\<your_server_instance\>** con l'indirizzo IP o il nome host dell'istanza di SQL Server 2017 in Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Load the SMO assembly and create a Server object
[System.Reflection.Assembly]::LoadWithPartialName('Microsoft.SqlServer.SMO') | out-null
$server = New-Object ('Microsoft.SqlServer.Management.Smo.Server') $serverInstance

# Set credentials
$server.ConnectionContext.LoginSecure=$false
$server.ConnectionContext.set_Login($credential.UserName)
$server.ConnectionContext.set_SecurePassword($credential.Password)

# Connect to the Server and get a few properties
$server.Information | Select-Object Edition, HostPlatform, HostDistribution | Format-List
# done
```

PowerShell deve visualizzare informazioni simili all'output seguente:

```
Edition          : Developer Edition (64-bit)
HostPlatform     : Linux
HostDistribution : Ubuntu
```
> [!NOTE]
> Se viene visualizzato nulla per questi valori, molto probabilmente la connessione all'istanza di SQL Server di destinazione non riuscita. Assicurarsi che è possibile utilizzare le stesse informazioni di connessione per la connessione da SQL Server Management Studio. Rivedere poi i [consigli per la risoluzione dei problemi di connessione](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="examine-sql-server-error-logs"></a>Esaminare i log degli errori di SQL Server

Si usa PowerShell in Windows per esaminare i log degli errori connect nell'istanza SQL Server 2017 in Linux. Si utilizzerà inoltre la **Out-GridView** registra cmdlet per visualizzare le informazioni dell'errore in una visualizzazione griglia.

Copiare e incollare i comandi seguenti al prompt di PowerShell. Si potrebbero richiedere alcuni minuti per l'esecuzione. Questi comandi, eseguire le operazioni seguenti:
- Visualizzazione di *richiesta delle credenziali di Windows PowerShell* finestra di dialogo in cui vengono richieste le credenziali (*nome utente SQL* e *password SQL*) a cui connettersi il 2017 di SQL Server istanza in Linux
- Utilizzare il **Get SqlErrorLog** per connettersi all'istanza di SQL Server 2017 su Linux e recuperare l'errore registra dal **ieri**
- Reindirizzare l'output di **Out-GridView** cmdlet

Ricordarsi di sostituire **\<your_server_instance\>** con l'indirizzo IP o il nome host dell'istanza di SQL Server 2017 in Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>Vedere anche
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
