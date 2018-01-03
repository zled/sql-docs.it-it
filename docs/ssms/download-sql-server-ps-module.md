---
title: Scaricare il modulo PowerShell di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords: installare sql server powershell, scaricare sql server powershell
ms.assetid: 
caps.latest.revision: "113"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 208bf291819a3e847e784e76611acdec0bf2f2d0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="download-sql-server-powershell-module"></a>Scaricare il modulo PowerShell di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Come parte della versione 17.0 di SQL Server Management Studio, il modulo SQL Server PowerShell ora è disponibile in PowerShell Gallery.  Il modulo non è più incluso nel pacchetto di installazione di SQL Server Management Studio. Per usare PowerShell con SSMS 17.0 e versioni successive, il modulo di SQL Server deve essere installato nel computer come passaggio aggiuntivo.

La documentazione completa sull'installazione della versione più recente di Windows Management Framework e su come installare i moduli PowerShell in generale è disponibile sul sito [PowerShell Gallery](https://www.powershellgallery.com/).

Il comando di PowerShell per installare il modulo di SQL Server è:

> Install-Module -Name SqlServer

Questo comando installa il modulo per tutti gli utenti del computer. È necessario eseguire il processo di PowerShell come amministratore.

> Install-Module -Name SqlServer -Scope CurrentUser

Questo comando installa il modulo per l'utente che esegue il processo corrente di PowerShell. Non è necessario eseguire il processo PowerShell con i diritti di amministratore.

Se esistono versioni precedenti dei moduli PowerShell di SQL Server nel computer, può essere necessario specificare il parametro "-AllowClobber".  

Se in esecuzione come amministratore e per installare il modulo per tutti gli utenti del computer

> Install-Module -Name SqlServer -AllowClobber

Se non è possibile l'esecuzione come amministratore o per eseguire l'installazione solo per l'utente corrente

> Install-Module -Name SqlServer -Scope CurrentUser -AllowClobber

Quando sono disponibili versioni aggiornate del modulo SqlServer, è possibile aggiornare la versione usando il comando Update-Module

> Update-Module -Name SqlServer

Per visualizzare le versioni del modulo installate nel computer che è possibile usare

> Get-Module SqlServer -ListAvailable

Per usare una versione specifica del modulo negli script è possibile importarlo con

> Import-Module SqlServer -Version 21.0.17178

Le versioni del modulo PowerShell per SQL Server disponibili in PowerShell Gallery supportano il controllo delle versioni e richiedono PowerShell versione 5.0 o successiva. Il modulo SqlServer è disponibile in [PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver/) 
