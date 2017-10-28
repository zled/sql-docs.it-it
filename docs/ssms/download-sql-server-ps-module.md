---
title: Scaricare il modulo PowerShell di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- installare sql server powershell, scaricare sql server powershell
ms.assetid: 
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 7449932a07aa0284fe2248828270b7f391713175
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="download-sql-server-powershell-module"></a>Scaricare il modulo PowerShell di SQL Server
Come parte della versione 17.0 di SQL Server Management Studio, il modulo PowerShell di SQL Server ora è disponibile in PowerShell Gallery.  Il modulo non è più incluso nel pacchetto di installazione di SQL Server Management Studio. Per usare PowerShell con SSMS 17.0 e versioni successive, il modulo di SQL Server deve essere installato nel computer come passaggio aggiuntivo.

La documentazione completa sull'installazione della versione più recente di Windows Management Framework e su come installare i moduli PowerShell in generale è disponibile sul sito [PowerShell Gallery](https://www.powershellgallery.com/).

Il comando di PowerShell per installare il modulo di SQL Server è:

> Install-Module -Name SqlServer

Questo comando installa il modulo per tutti gli utenti del computer. È necessario eseguire il processo di PowerShell come amministratore.

> Install-Module -Name SqlServer -Scope CurrentUser

Questo comando installa il modulo per l'utente che esegue il processo corrente di PowerShell. Non è necessario eseguire il processo PowerShell con i diritti di amministratore.

Se esistono versioni precedenti dei moduli PowerShell di SQL Server nel computer, può essere necessario specificare il parametro "-AllowClobber".  

Se in esecuzione come amministratore e per installare il modulo per tutti gli utenti del computer

> Install-Module -Name SqlServer -AllowClobber

Se non è possibile l'esecuzione come amministratore o per installare solo per l'utente corrente

> Install-Module -Name SqlServer -Scope CurrentUser -AllowClobber

Quando sono disponibili versioni aggiornate del modulo SqlServer, è possibile aggiornare la versione usando il comando Update-Module

> Update-Module -Name SqlServer

Per visualizzare le versioni del modulo installate nel computer che è possibile usare

> Get-Module SqlServer -ListAvailable

Per usare una versione specifica del modulo negli script è possibile importarlo con

> Import-Module SqlServer -Version 21.0.17178

Le versioni del modulo PowerShell per SQL Server disponibili in PowerShell Gallery supportano il controllo delle versioni e richiedono PowerShell versione 5.0 o successiva. Il modulo SqlServer è disponibile in [PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver/) 

