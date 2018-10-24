---
title: Scaricare il modulo PowerShell di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 10/08/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
keywords:
- installare sql server powershell, scaricare sql server powershell
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40873fe63b897da52fc9a7d440a8568872431d72
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851756"
---
# <a name="install-sql-server-powershell-module"></a>Installare il modulo PowerShell SqlServer
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Questo articolo include indicazioni per l'installazione del modulo PowerShell **SqlServer**.
> [!NOTE]
> Esistono due moduli SQL Server PowerShell: 
> * **SQLPS**: questo modulo è incluso nell'installazione di SQL Server (per la compatibilità con le versioni precedenti), ma non viene più aggiornato. Il modulo PowerShell più aggiornato è il modulo **SqlServer**.
> * **SqlServer**: questo modulo include nuovi cmdlet per il supporto delle funzionalità più recenti di SQL. Il modulo contiene anche le versioni aggiornate dei cmdlet in **SQLPS**. 

Le versioni precedenti del modulo **SqlServer** *erano* incluse con SQL Server Management Studio (SSMS), ma solo con le versioni 16.x di SQL Server Management Studio. Per usare PowerShell con SSMS 17.0 e versioni successive, è necessario installare il modulo **SqlServer** da [PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver).
La versione corrente del modulo **SqlServer** è la 21.0.17279. È basata sulla versione v140 di Microsoft.SQLServer.SMO.  
Per una versione del modulo che supporta la versione successiva di SQL Server (basata sulla versione v150 di Microsoft.SQLServer.SMO), vedere nella sezione alla fine di questa pagina le istruzioni per ottenere versioni non definitive del modulo. La versione non definitiva più recente del modulo è 21.1.18040-preview.

Per installare il modulo **SqlServer** da PowerShell Gallery, avviare una sessione di [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting) e usare i comandi seguenti. Se si verificano problemi durante l'installazione, vedere la [documentazione per l'installazione del modulo](https://docs.microsoft.com/powershell/gallery/psget/module/psget_install-module) e la [guida di riferimento per l'installazione del modulo](https://docs.microsoft.com/powershell/module/powershellget/Install-Module).

Per installare il modulo **SqlServer**:

```Install-Module -Name SqlServer```

Se nel computer sono presenti versioni precedenti del modulo **SqlServer** può essere possibile usare `Update-Module` (descritto più avanti in questo articolo) o specificare il parametro `-AllowClobber`:  

```Install-Module -Name SqlServer -AllowClobber```

Se non è possibile eseguire la sessione di PowerShell come amministratore, è possibile eseguire l'installazione per l'utente corrente:

```Install-Module -Name SqlServer -Scope CurrentUser```

Quando sono disponibili versioni aggiornate del modulo **SqlServer**, è possibile aggiornare la versione usando `Update-Module`:

```Update-Module -Name SqlServer```

Per visualizzare le versioni del modulo installate:

```Get-Module SqlServer -ListAvailable```

Per usare una versione specifica del modulo è possibile importarlo con un numero di versione specifico, come indicato di seguito:

```Import-Module SqlServer -Version 21.0.17178```

> [!NOTE]
> Versioni non definitive (o di "anteprima") del modulo possono essere disponibili in PowerShell Gallery. Possono essere rilevate e installate mediante i cmdlet aggiornati *Find-Module* e *Install-Module* incluse nel modulo [PowerShellGet](https://www.powershellgallery.com/packages/PowerShellGet) passando l'opzione *-AllowPrerelease*.
>
> Per individuare la versione non definitiva/di anteprima del modulo, è possibile eseguire il comando seguente:
>
> ```Find-Module SqlServer -AllowPrerelease```
>
> Per installare una versione non definitiva/di anteprima specifica del modulo è possibile installarla con un numero di versione specifico, come indicato di seguito:
>
> ```Install-Module SqlServer -RequiredVersion 21.1.18040-preview -AllowPrerelease```
> 

Le versioni del modulo **SqlServer** disponibili in PowerShell Gallery supportano il controllo delle versioni e richiedono PowerShell versione 5.0 o successiva. 

* [Modulo SqlServer in PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver) 
* [Cmdlet di SQL Server](https://docs.microsoft.com/powershell/module/sqlserver)
* [Cmdlet di SQLPS](https://docs.microsoft.com/powershell/module/sqlps)
