---
title: Registro applicazioni di Windows | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
caps.latest.revision: "32"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2f34c31f34b79a5e2f40cc88cbf57c35ce582558
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="windows-application-log"></a>Registro applicazioni di Windows
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] i messaggi di evento vengono inseriti nel registro applicazioni di Windows. in modo da consentire l'individuazione degli eventi generati dalle applicazioni del server di report in esecuzione nel sistema locale.  
  
## <a name="viewing-report-server-events"></a>Visualizzazione degli eventi del server di report  
 Per visualizzare il registro e filtrare i messaggi in esso contenuti, è possibile utilizzare il Visualizzatore eventi. Per altre informazioni sui messaggi di evento, vedere [Guida di riferimento a errori ed eventi &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md). Per ulteriori informazioni sul registro applicazioni di Windows e sul Visualizzatore eventi, vedere la documentazione di Windows.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dispone di tre origini dell'evento:  
  
-   Server di report (servizio Windows ReportServer)  
  
-   Gestione report  
  
-   Elaborazione pianificazione e recapito  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è possibile disabilitare la registrazione eventi delle applicazioni del server di report né decidere quali eventi devono essere registrati. Lo schema che descrive la registrazione degli eventi del server di report è fisso e non è possibile estenderlo per supportare eventi personalizzati.  
  
 Nella tabella riportata di seguito vengono descritti i tipi di evento che vengono registrati dal server di report nel registro eventi applicazioni.  
  
|Tipo di evento|Description|  
|----------------|-----------------|  
|Informazioni|Evento che descrive un'operazione riuscita, ad esempio quando viene avviato il servizio del server di report.|  
|Avviso|Evento che indica un potenziale problema, ad esempio insufficienza di spazio su disco.|  
|Errore|Evento che descrive un problema importante, ad esempio il mancato avvio del servizio.|  
|Controllo con esito positivo|Evento di sicurezza che descrive un accesso riuscito.|  
|Controllo con esito negativo|Evento che viene registrato in caso di tentativo di accesso non riuscito.|  
  
## <a name="see-also"></a>Vedere anche  
 [File di log e origini di Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Guida di riferimento a errori ed eventi &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
