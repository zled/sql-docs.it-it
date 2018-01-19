---
title: Scaricare il modulo PowerShell di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 01/05/2018
ms.prod: sql-non-specified
ms.prod_service: powershell
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
keywords: installare sql server powershell, scaricare sql server powershell
ms.assetid: 
caps.latest.revision: "113"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: de203080dcc9b2c296003606e9a8067fd5dc532d
ms.sourcegitcommit: 779f3398e4e3f4c626d81ae8cedad153bee69540
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2018
---
# <a name="install-sql-server-powershell-module"></a>Installare il modulo PowerShell SqlServer
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Questo articolo include indicazioni per l'installazione del modulo PowerShell **SqlServer**.

> [!NOTE]
> Esistono due moduli SQL Server PowerShell: **SqlServer** e **SQLPS**. Il modulo **SQLPS** è incluso nell'installazione di SQL Server (per la compatibilità con le versioni precedenti), ma non viene più aggiornato. Il modulo PowerShell più aggiornato è il modulo **SqlServer**. Il modulo **SqlServer** contiene versioni aggiornate dei cmdlet di **SQLPS** e include anche nuovi cmdlet per il supporto delle funzionalità SQL più recenti. Le versioni precedenti del modulo **SqlServer** *erano* incluse con SQL Server Management Studio (SSMS), ma solo con le versioni 16.x di SQL Server Management Studio. Per usare PowerShell con SSMS 17.0 e versioni successive, è necessario installare il modulo **SqlServer** da PowerShell Gallery.

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


Le versioni del modulo **SqlServer** disponibili in PowerShell Gallery supportano il controllo delle versioni e richiedono PowerShell versione 5.0 o successiva. 

* [Modulo SqlServer in PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver) 
* [Cmdlet di SQL Server](https://docs.microsoft.com/powershell/module/sqlserver)
* [Cmdlet di SQLPS](https://docs.microsoft.com/powershell/module/sqlps)
