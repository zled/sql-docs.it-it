---
title: Integrazione di Reporting Services tramite i controlli ReportViewer | Microsoft Docs
ms.custom: ''
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: application-integration
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: bf99e8bbb0286c66ca0b16cea0ccb8ff8a1817cd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="integrating-reporting-services-using-reportviewer-controls"></a>Integrazione di Reporting Services tramite i controlli ReportViewer
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2015 sono disponibili due controlli ReportViewer per l'integrazione delle funzionalità di visualizzazione dei report nelle applicazioni. È disponibile una versione per le applicazioni basate su Windows Form e una per le applicazioni Web Form. Ogni controllo offre funzionalità simili, ma ognuno è progettato per un ambiente specifico. Entrambi i controlli consentono di elaborare i report distribuiti in un server di report (modalità di elaborazione remota) o copiati in un computer in cui [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è stato installato (modalità di elaborazione locale).  
  
 Il controllo ReportViewer non include il supporto integrato per l'adattamento dinamico ai diversi dispositivi con risoluzioni dello schermo diverse.  
  
## <a name="remote-processing-mode"></a>Modalità di elaborazione remota  
 La modalità di elaborazione remota è il metodo migliore per la visualizzazione dei report distribuiti in un server di report. La modalità di elaborazione remota offre i vantaggi seguenti:  
  
-   L'elaborazione remota fornisce una soluzione ottimizzata per l'esecuzione di report, in quanto il rendering e l'elaborazione dei report vengono eseguiti dal server di report.  
  
-   Poiché l'elaborazione viene gestita dal server di report, una richiesta del report può essere elaborata da più server di report in una distribuzione con scalabilità orizzontale o da un server con più processori in uno scenario con scalabilità verticale.  
  
 Per i report eseguiti in modalità remota possono inoltre venire usate le funzionalità complete del server di report, incluse tutte le estensioni dati e per il rendering.  
  
> [!NOTE]  
>  L'elenco di estensioni disponibili per il controllo ReportViewer quando l'esecuzione avviene in modalità di elaborazione remota dipende dall'edizione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installata nel server di report.  
  
## <a name="local-processing-mode"></a>Modalità di elaborazione locale  
 La modalità di elaborazione locale offre un metodo alternativo per la visualizzazione e il rendering dei report quando [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è installato. A differenza dell'elaborazione remota, nel controllo è disponibile solo un subset delle funzionalità fornite dal server di report. Nella modalità locale l'elaborazione dei dati non viene gestita dal controllo ma implementata dall'applicazione host. L'elaborazione dei report viene tuttavia gestita dal controllo. Nella modalità di elaborazione locale sono disponibili solo le estensioni per il rendering PDF, Excel, Word e Image.  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione di Reporting Services nelle applicazioni](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Uso del controllo Web Form ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)   
 [Uso del controllo Windows Form ReportViewer](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md)  

  
  
