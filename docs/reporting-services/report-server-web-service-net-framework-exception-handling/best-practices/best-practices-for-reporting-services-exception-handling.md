---
title: Procedure consigliate per la gestione delle eccezioni in Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: ''
ms.component: report-server-web-service-net-framework-exception-handling
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e6ae230c7d3e21ad4b5ac19ab791f63db8d51c50
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Procedure consigliate per la gestione delle eccezioni di Reporting Services
  Quando si sviluppano applicazioni [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], è possibile ricorrere a diversi metodi per eliminare o ridurre le eccezioni. Quando si verificano le eccezioni, fornire messaggi di errore chiari e concisi all'utente e aggiungere funzionalità adeguate di gestione delle eccezioni per impedire che le applicazioni vengano chiuse in modo imprevisto.  
  
 Un'applicazione che invia richieste al servizio Web ReportServer deve essere in grado di effettuare le operazioni seguenti:  
  
-   Evitare che vengano generate eccezioni impedendo il maggior numero possibile di richieste non valide.  
  
-   Rilevare le eccezioni e fornire codice specifico di gestione degli errori quando possibile.  
  
-   Gestire i casi di errore che non generano eccezioni.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Metodi per evitare le richieste non valide](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/preventing-invalid-requests.md)|Vengono descritte le tecniche per impedire l'invio delle richieste non valide al server di report.|  
|[Uso di blocchi try/catch](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md)|Viene descritto come migliorare l'affidabilità dell'applicazione con i blocchi try/catch.|  
|[Gestione di avvisi e casi che non causano eccezioni](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Viene illustrato come gestire gli errori che non comportano la generazione di un'eccezione in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Uso della proprietà Detail per la gestione di errori specifici](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)|Spiega come gestire errori specifici a livello di codice tramite la proprietà **Detail** dell'oggetto **SoapException**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Introduzione alla gestione delle eccezioni in Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException di Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
