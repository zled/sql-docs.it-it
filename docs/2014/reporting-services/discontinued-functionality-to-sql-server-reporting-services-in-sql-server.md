---
title: Funzionalità di SQL Server Reporting Services in SQL Server 2014 non più disponibili | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- discontinued functionality [Reporting Services]
- Reporting Services, backward compatibility
- Rsactivate.exe
- unsupported features [Reporting Services]
ms.assetid: d529cc96-3483-480b-9bfc-bd28b1d0ef52
caps.latest.revision: 47
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 971662bbb0b1c8b08507574d569418d065f6204a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201031"
---
# <a name="discontinued-functionality-to-sql-server-reporting-services-in-sql-server-2014"></a>Funzionalità non più disponibili in SQL Server Reporting Services in SQL Server 2014
  In questo argomento vengono descritte le funzionalità di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non più disponibili in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Non sono inclusi avvisi relativi al supporto non più disponibile per versioni specifiche del sistema operativo o per [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Services (IIS). Per altre informazioni sui prerequisiti di sistema, vedere [Hardware and Software Requirements for Installing SQL Server 2014](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
 Contenuto dell'argomento:  
  
-   [Funzionalità deprecate in SQL Server 2014 Reporting Services](#bkmk_sql14)  
  
-   [Funzionalità deprecate in SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Funzionalità deprecate in SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services non più disponibile la funzionalità  
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non sono presenti funzionalità di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] non più disponibili.  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services non più disponibile la funzionalità  
 In questa sezione vengono descritte le funzionalità di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non più disponibili in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non sono presenti funzionalità di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] non più disponibili.  
  
##  <a name="bkmk_kj"></a> Funzionalità deprecate in SQL Server 2008 R2 Reporting Services  
 Questa sezione viene descritto non più disponibile in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Poiché SQL Server 2008 R2 è un aggiornamento secondario della versione di SQL Server 2008, è consigliabile rivedere anche il contenuto nella sezione relativa a SQL Server 2008.  
  
### <a name="64-bit-platform-support"></a>Supporto della piattaforma a 64 bit  
 A partire da [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] componente non supporta più server basati su Itanium che eseguono Windows Server 2003 o Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] continua a supportare altri sistemi operativi a 64 bit, ad esempio Windows Server°2008 per sistemi basati su Itanium e Windows Server 2008 R2 per sistemi basati su Itanium. Per eseguire l'aggiornamento a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] da un'installazione di [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] con [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in un'edizione del sistema basata su Itanium di Windows Server 2003 o Windows Server 2003 R2, è necessario prima aggiornare il sistema operativo.  
  
### <a name="data-source-credentials-in-url-access"></a>Credenziali dell'origine dati nell'accesso a URL  
 Le stringhe di parametri URL accesso *dsu:datasourcename = value* e *dsp:datasourcename = valore* ora sono obsolete. Nelle versioni precedenti queste stringhe di parametri sono archiviate in testo normale nella cache del browser e non viene pertanto garantita la sicurezza.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Modifiche del comportamento di SQL Server Reporting Services in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Funzionalità deprecate di SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)  
  
  
