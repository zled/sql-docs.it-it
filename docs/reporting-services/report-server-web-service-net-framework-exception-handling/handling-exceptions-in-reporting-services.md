---
title: La gestione delle eccezioni in Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
caps.latest.revision: 31
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 7e1472c11575ba8bed99992ec9630e408c347291
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="handling-exceptions-in-reporting-services"></a>Gestione delle eccezioni in Reporting Services
  Quando una richiesta del client dell'API SOAP di Reporting Services non può essere completata, il server di report restituisce un errore al posto dei risultati previsti della chiamata. Impossibile completare una chiamata, viene restituito un errore per il servizio Web ReportServer come SOAP **errore** elemento XML. L'elemento descrittivo principale dell'errore è il **dettaglio** elemento che include tutte le informazioni di errore fornite dal server di report, nonché le informazioni di errore di servizio Web. Informazioni sulla chiave nel **dettaglio** elemento è il codice di errore di server di report. In base al messaggio e al codice di errore, è possibile determinare l'azione appropriata da eseguire nelle applicazioni. Per ulteriori informazioni sugli errori SOAP, vedere il sito Web World Wide Web Consortium (W3C) all'indirizzo http://www.w3.org/TR/SOAP (informazioni in lingua inglese).  
  
## <a name="soap-faults-and-the-net-framework"></a>Errori SOAP e .NET Framework  
 Nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], se si verifica un errore in una richiesta client al servizio Web, il server di report comunica l'errore al codice client che chiama il servizio Web generando una **SoapException** oggetto. Il **SoapException** include le informazioni contenute in un errore SOAP. Il **dettaglio** proprietà del **SoapException** esegue il mapping al **dettaglio** elemento nell'errore SOAP. Le applicazioni devono intercettare la **SoapException** con un blocco try/catch e utilizzare il **dettaglio** proprietà del **SoapException** per eseguire l'azione appropriata. Per ulteriori informazioni sul **SoapException** classe e **dettaglio** proprietà in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vedere [Reporting Services SoapException classe](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md). Per ulteriori informazioni sul **SoapException** classe, vedere il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentazione SDK.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Detail](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Introduzione a gestione delle eccezioni in Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException di Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
