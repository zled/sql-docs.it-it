---
title: Scaricare il modulo PowerShell di SQL Server | Documenti Microsoft
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
ms.translationtype: Human Translation
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: f55266b6ec28e2552047cc36a5060945006b2caa
ms.contentlocale: it-it
ms.lasthandoff: 06/23/2017

---
# <a name="download-sql-server-powershell-module"></a>Scaricare il modulo PowerShell di SQL Server
Come parte della versione 17,0 di SQL Server Management Studio, è ora incluso il modulo di PowerShell per SQL Server tramite PowerShell Gallery.  Il modulo non è più incluso nel pacchetto di installazione di SQL Server Management Studio. Per utilizzare PowerShell con SSMS 17,0 e successive, il modulo di SQL Server deve essere installato nel computer come un passaggio aggiuntivo.

Documentazione sull'installazione della versione più recente di Windows Management Framework completo e come installare i moduli di PowerShell in generale è reperibile nel [PowerShell Gallery](https://www.powershellgallery.com/) sito.

Il comando di PowerShell per installare il modulo di SQL Server è:

> Install-module-Name SqlServer-ambito CurrentUser

Se sono presenti versioni precedenti dei moduli di PowerShell per SQL Server nel computer, potrebbe essere necessario fornire il "-AllowClobber" parametro.  

Le versioni del modulo PowerShell per SQL Server disponibile in PowerShell Gallery supportano il controllo delle versioni e richiedono PowerShell versione 5.0 o versione successiva.

