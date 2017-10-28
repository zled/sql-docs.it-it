---
title: rsInternalError - errore di Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
caps.latest.revision: 23
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7265597c2376d62b6d3e42c55c8d87e45f6d869e
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="rsinternalerror---reporting-services-error"></a>rsInternalError - Errore di Reporting Services
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|rsInternalError|  
|Origine evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Errore interno nel server di report. Per altre informazioni, vedere il log degli errori.|  
  
## <a name="explanation"></a>Spiegazione  
 Si tratta di un messaggio di errore generico, spesso seguito da un errore più descrittivo che include ulteriori dettagli.  
  
 Gli errori interni non sono comuni. Se viene visualizzato questo errore, nei log di traccia del server di report sono disponibili ulteriori informazioni. Se inoltre si esegue il servizio come amministratore locale nello stesso computer in cui si è verificato l'errore, è possibile visualizzare lo stack di chiamate per ottenere ulteriori informazioni.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per determinare la causa specifica di questo messaggio, esaminare i file di log dei server di report, che si trovano in \Microsoft SQL Server\MSRS12. \<instancename > \Reporting. Per altre informazioni, vedere [File di log e origini di Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
 Per visualizzare lo stack di chiamate, fare clic con il pulsante destro del mouse nella pagina in cui si è verificato l'errore e scegliere **Visualizza origine**. Per visualizzare lo stack di chiamate, è necessario disporre delle autorizzazioni di amministratore nello stesso computer in cui si verifica l'errore.  
  
 Se non sono disponibili informazioni aggiuntive, è possibile riprovare a eseguire la richiesta.  
  
## <a name="internal-only"></a>Solo interno  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare e arrestare il servizio del server di report](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  

