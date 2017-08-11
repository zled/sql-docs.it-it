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
ms.translationtype: HT
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: f55266b6ec28e2552047cc36a5060945006b2caa
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="download-sql-server-powershell-module"></a>Scaricare il modulo PowerShell di SQL Server
Come parte della versione 17.0 di SQL Server Management Studio, il modulo PowerShell di SQL Server ora è disponibile in PowerShell Gallery.  Il modulo non è più incluso nel pacchetto di installazione di SQL Server Management Studio. Per usare PowerShell con SSMS 17.0 e versioni successive, il modulo di SQL Server deve essere installato nel computer come passaggio aggiuntivo.

La documentazione completa sull'installazione della versione più recente di Windows Management Framework e su come installare i moduli PowerShell in generale è disponibile sul sito [PowerShell Gallery](https://www.powershellgallery.com/).

Il comando di PowerShell per installare il modulo di SQL Server è:

> Install-module -Name SqlServer -Scope CurrentUser

Se esistono versioni precedenti dei moduli PowerShell di SQL Server nel computer, può essere necessario specificare il parametro "-AllowClobber".  

Le versioni del modulo PowerShell di per SQL Server disponibili in PowerShell Gallery supportano il controllo delle versioni e richiedono PowerShell versione 5.0 o successiva.

