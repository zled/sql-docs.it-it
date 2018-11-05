---
title: Installare SQL Server con PowerShell Desired State Configuration (DSC) | Microsoft Docs
description: Informazioni su come installare SQL Server con PowerShell Desired State Configuration (DSC).
ms.custom: ''
ms.date: 10/26/2018
ms.devlang: PowerShell
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
author: randomnote1
ms.author: dareist
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 16d425d8eb66a950f432fa3ef9c68a8e68a78d22
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148479"
---
# <a name="install-sql-server-with-powershell-desired-state-configuration"></a>Installare SQL Server con PowerShell Desired State Configuration (DSC)

Quante volte è successo di spostarsi all'interno dell'interfaccia di installazione di SQL Server usando i soliti vecchi pulsanti, immettendo le solite informazioni senza soffermarsi un attimo a pensare? Poi, quando l'installazione è terminata, ci si rende conto di aver dimenticato di specificare il gruppo di amministratori di database nel ruolo sysadmin. A questo punto, bisogna dedicare tempo prezioso accedendo in modalità utente singolo per aggiungere gli utenti o i gruppi appropriati, riattivare la modalità multiutente di SQL e testare l'installazione. Ora, però, il livello di confidenza dell'intera installazione è compromesso. Ci si chiede se non si sarà dimenticato qualcos'altro... Io stesso ho vissuto questa situazione più di una volta.

Basta scegliere [PowerShell Desired State Configuration (DSC)](https://docs.microsoft.com/powershell/dsc/overview). Con DSC è possibile creare un modello di configurazione che può essere riutilizzato in centinaia o migliaia di server. A seconda della build, potrebbe essere necessario modificare alcuni dei parametri di installazione, ma non è un grosso problema perché è comunque possibile mantenere tutte le impostazioni standard. L'aspetto positivo è che elimina l'eventualità di dimenticarsi di specificare un parametro importante a causa di una notte insonne.

In questo articolo verrà descritta l'installazione iniziale di un'istanza autonoma di SQL Server 2017 in Windows Server 2016 usando la risorsa DSC SqlServerDsc. È utile avere una conoscenza pregressa di DSC perché in questo articolo non viene spiegato il funzionamento di DSC.

Per questa procedura dettagliata sono necessari gli elementi seguenti:

- Una macchina virtuale che esegue Windows Server 2016
- Supporto di installazione di SQL Server 2017
- La risorsa DSC SqlServerDsc (la versione 10.0.0.0 è la versione corrente al momento della stesura di questo articolo)

## <a name="prerequisites"></a>Prerequisites

Nella maggior parte dei casi, DSC verrà utilizzato per gestire i prerequisiti. Tuttavia, ai fini di questa dimostrazione, i prerequisiti verranno gestiti manualmente.

## <a name="install-the-sqlserverdsc-dsc-resource"></a>Installare la risorsa DSC SqlServerDsc

La risorsa DSC [SqlServerDsc](https://www.powershellgallery.com/packages/SqlServerDsc) può essere scaricata dalla [PowerShell Gallery](https://www.powershellgallery.com/) utilizzando il cmdlet [Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module?view=powershell-5.1). _Nota: verificare che PowerShell sia in esecuzione "Come amministratore" per installare il modulo._

```PowerShell
Install-Module -Name SqlServerDsc
```

Ottenere il supporto di installazione di SQL Server 2017 Scaricare nel server il supporto di installazione di SQL Server 2017. Per questa demo è stato scaricato SQL Server 2017 Enterprise dalla sottoscrizione di Visual Studio e il file ISO è stato copiato in "C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso".

A questo punto, è necessario estrarre il file ISO in una directory.

```PowerShell
New-Item -Path C:\SQL2017 -ItemType Directory
$mountResult = Mount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso' -PassThru
$volumeInfo = $mountResult | Get-Volume
$driveInfo = Get-PSDrive -Name $volumeInfo.DriveLetter
Copy-Item -Path ( Join-Path -Path $driveInfo.Root -ChildPath '*' ) -Destination C:\SQL2017\ -Recurse
Dismount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso'
```

## <a name="create-the-configuration"></a>Creare configurazione

### <a name="configuration"></a>Configurazione

Creare la funzione di configurazione che verrà chiamata per generare i documenti [MOF (Managed Object Format)](https://docs.microsoft.com/windows/desktop/WmiSdk/managed-object-format--mof-).

```PowerShell
Configuration SQLInstall
{...}
```

### <a name="modules"></a>Moduli

Importare i moduli nella sessione corrente. Questi moduli indicano al documento di configurazione come creare il o i documenti MOF e comunica al motore DSC come applicare i documenti MOF al server.

```PowerShell
Import-DscResource -ModuleName SqlServerDsc
```

### <a name="resources"></a>Risorse

#### <a name="net-framework"></a>.NET Framework

SQL Server si basa su .NET framework, pertanto è necessario assicurarsi che sia installato prima di installare SQL Server. La risorsa WindowsFeature è usata per installare la funzionalità di Windows Net-Framework-45-Core.

```PowerShell
WindowsFeature 'NetFramework45'
{
     Name = 'Net-Framework-45-Core'
     Ensure = 'Present'
}
```

#### <a name="sqlsetup"></a>SqlSetup

La risorsa SqlSetup viene utilizzata per indicare a DSC come installare SQL Server. I parametri necessari per un'installazione di base sono:

- **InstanceName**: il nome dell'istanza. Utilizzare MSSQLSERVER per un'istanza predefinita.
- **Feature**: le funzionalità da installare. In questo esempio, verrà installata solo la funzionalità SQLEngine.
- **SourcePath**: il percorso del supporto di installazione di SQL. In questo esempio, il supporto di installazione di SQL è archiviato in "C:\SQL2017". Per limitare lo spazio utilizzato nel server, si può utilizzare una condivisione di rete.
- **SQLSysAdminAccounts**: gli utenti o i gruppi che devono essere un membro del ruolo sysadmin. In questo esempio, viene concesso l'accesso sysadmin al gruppo Administrators locale. _Nota: questa configurazione non è consigliata per un ambiente con sicurezza elevata._

È disponibile un elenco completo dei parametri SqlSetup esistenti, con relativa descrizione, nel [repository GitHub di SqlServerDsc](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlsetup).

La risorsa SqlSetup ha un comportamento insolito perché installa solo SQL SENZA MANTENERE le impostazioni applicate. Ad esempio, se al momento dell'installazione vengono specificati gli SQLSysAdminAccount, un amministratore potrebbe aggiungere o rimuovere gli account di accesso al o dal ruolo sysadmin senza entrare in conflitto con SqlSetup. Se si desidera che DSC applichi l'appartenenza del ruolo sysadmin, utilizzare la risorsa [SqlServerRole](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlserverrole).

#### <a name="complete-configuration"></a>Completare la configurazione

```PowerShell
Configuration SQLInstall
{
     Import-DscResource -ModuleName SqlServerDsc

     node localhost
     {
          WindowsFeature 'NetFramework45'
          {
               Name   = 'NET-Framework-45-Core'
               Ensure = 'Present'
          }

          SqlSetup 'InstallDefaultInstance'
          {
               InstanceName        = 'MSSQLSERVER'
               Features            = 'SQLENGINE'
               SourcePath          = 'C:\SQL2017'
               SQLSysAdminAccounts = @('Administrators')
               DependsOn           = '[WindowsFeature]NetFramework45'
          }
     }
}
```

## <a name="build-and-deploy"></a>Compilare e distribuire

### <a name="compile-the-configuration"></a>Compilare la configurazione

Eseguire lo script di configurazione:

```PowerShell
. .\SQLInstallConfiguration.ps1
```

Eseguire la funzione di configurazione:

```PowerShell
SQLInstall
```

Nella directory di lavoro verrà creata la directory "SQLInstall" che conterrà una chiamata al file "localhost.mof". Esaminare il contenuto del file MOF per vedere la configurazione DSC compilata.

### <a name="deploy-the-configuration"></a>Distribuire la configurazione

Per iniziare la distribuzione DSC di SQL Server, chiamare il cmdlet Start-DscConfiguration. I parametri forniti al cmdlet sono:

- **Path**: il percorso della cartella contenente i documenti MOF da distribuire, ad esempio "C:\SQLInstall".
- **Wait**: attendere il completamento del processo di configurazione.
- **Force**: eseguire l'override di tutte le configurazioni DSC esistenti.
- **Verbose**: mostrare l'output dettagliato. Utile quando si effettua il push di una configurazione per la prima volta per agevolare la risoluzione dei problemi.

```PowerShell
Start-DscConfiguration -Path C:\SQLInstall -Wait -Force -Verbose
```

Man mano che la configurazione viene applicata, l'output dettagliato illustra ciò che accade, rassicurando sul fatto che sta effettivamente accadendo qualcosa. A meno che non si verifichino errori, indicati da testo rosso, quando "Operation 'Invoke CimMethod' complete." viene visualizzato sullo schermo, l'installazione di SQL è terminata.

## <a name="validate-installation"></a>Convalidare l'installazione

### <a name="dsc"></a>DSC

I cmdlet [Test-DscConfiguration](https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration) possono essere utilizzati per determinare se lo stato corrente del server, in questo caso l'installazione di SQL, soddisfa lo stato desiderato. Il risultato di Test-DscConfiguration deve essere "True".

```PowerShell
PS C:\> Test-DscConfiguration
True
```

### <a name="services"></a>Servizi

L'elenco dei servizi ora riporta i servizi di SQL Server

```PowerShell
PS C:\> Get-Service -Name *SQL*
Status  Name           DisplayName
------  ----           -----------
Running MSSQLSERVER    SQL Server (MSSQLSERVER)
Stopped SQLBrowser     SQL Server Browser
Running SQLSERVERAGENT SQL Server Agent (MSSQLSERVER)
Running SQLTELEMETRY   SQL Server CEIP service (MSSQLSERVER)
Running SQLWriter      SQL Server VSS Writer
```

### <a name="sql-server"></a>SQL Server

```PowerShell
PS C:\> & sqlcmd -S $env:COMPUTERNAME
1> SELECT @@SERVERNAME
2> GO
1> quit
```

## <a name="see-also"></a>Vedere anche

[Panoramica di PowerShell DSC](https://docs.microsoft.com/powershell/dsc/overview)

[Installare SQL Server dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)

[Installare SQL Server tramite un file di configurazione](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)
