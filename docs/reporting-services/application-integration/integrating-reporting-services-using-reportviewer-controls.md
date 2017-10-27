---
title: Integrazione di Reporting Services utilizzando i controlli ReportViewer | Documenti Microsoft
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
caps.latest.revision: 26
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6247ce56394aff4f194bf9e452f36663a1112c80
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls"></a>Integrazione di Reporting Services utilizzando i controlli ReportViewer
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual Studio 2015 fornisce due controlli ReportViewer per l'integrazione di funzionalità nelle applicazioni di visualizzazione dei report. È disponibile una versione per le applicazioni basate su Windows Form e una per le applicazioni Web Form. Ogni controllo offre funzionalità simili, ma ognuno è progettato per un ambiente specifico. Entrambi i controlli possono elaborare i report distribuiti in un server di report (modalità di elaborazione remota) o sono stati copiati in un computer in cui [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è stato installato (modalità di elaborazione locale).  
  
 Il controllo ReportViewer non include il supporto integrato per l'adattamento dinamico ai diversi dispositivi con risoluzioni dello schermo diverse.  
  
## <a name="remote-processing-mode"></a>Modalità di elaborazione remota  
 La modalità di elaborazione remota è il metodo migliore per la visualizzazione dei report distribuiti in un server di report. La modalità di elaborazione remota offre i vantaggi seguenti:  
  
-   L'elaborazione remota fornisce una soluzione ottimizzata per l'esecuzione di report, in quanto il rendering e l'elaborazione dei report vengono eseguiti dal server di report.  
  
-   Poiché l'elaborazione viene gestita dal server di report, una richiesta del report può essere elaborata da più server di report in una distribuzione con scalabilità orizzontale o da un server con più processori in uno scenario con scalabilità verticale.  
  
 Per i report eseguiti in modalità remota possono inoltre venire usate le funzionalità complete del server di report, incluse tutte le estensioni dati e per il rendering.  
  
> [!NOTE]  
>  L'elenco di estensioni disponibili per il controllo ReportViewer quando l'esecuzione avviene in modalità di elaborazione remota dipende dall'edizione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installata nel server di report.  
  
## <a name="local-processing-mode"></a>Modalità di elaborazione locale  
 La modalità di elaborazione locale offre un metodo alternativo per la visualizzazione e il rendering dei report quando [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è installato. A differenza dell'elaborazione remota, nel controllo è disponibile solo un subset delle funzionalità fornite dal server di report. Nella modalità locale l'elaborazione dei dati non viene gestita dal controllo ma implementata dall'applicazione host. Tuttavia, l'elaborazione di report viene gestita dal controllo stesso. Nella modalità di elaborazione locale sono disponibili solo le estensioni per il rendering PDF, Excel, Word e Image.  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione di Reporting Services nelle applicazioni](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Utilizzo del controllo Web Form ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)   
 [Utilizzo del controllo Windows Form ReportViewer](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md)  

  
  

