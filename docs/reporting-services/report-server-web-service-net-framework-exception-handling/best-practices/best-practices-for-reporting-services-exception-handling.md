---
title: Procedure consigliate per la gestione delle eccezioni di servizi di report | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d7a1557097e118bfc47cb395dc58331ccf3e0817
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Procedure consigliate per la gestione delle eccezioni di Reporting Services
  Quando si sviluppano applicazioni [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], è possibile ricorrere a diversi metodi per eliminare o ridurre le eccezioni. Quando si verificano le eccezioni, fornire messaggi di errore chiari e concisi all'utente e aggiungere funzionalità adeguate di gestione delle eccezioni per impedire che le applicazioni vengano chiuse in modo imprevisto.  
  
 Un'applicazione che invia richieste al servizio Web ReportServer deve essere in grado di effettuare le operazioni seguenti:  
  
-   Evitare che vengano generate eccezioni impedendo il maggior numero possibile di richieste non valide.  
  
-   Rilevare le eccezioni e fornire codice specifico di gestione degli errori quando possibile.  
  
-   Gestire i casi di errore che non generano eccezioni.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Impedire richieste non valide](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/preventing-invalid-requests.md)|Vengono descritte le tecniche per impedire l'invio delle richieste non valide al server di report.|  
|[Utilizzo di Try e blocchi Catch](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md)|Viene descritto come migliorare l'affidabilità dell'applicazione con i blocchi try/catch.|  
|[Gestione degli avvisi e casi che non generano eccezioni](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Viene illustrato come gestire gli errori che non comportano la generazione di un'eccezione in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Utilizzo della proprietà Detail per gestire errori specifici](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)|Viene illustrato come gestire a livello di programmazione errori specifici tramite il **dettaglio** proprietà del **SoapException** oggetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Introduzione a gestione delle eccezioni in Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException di Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  