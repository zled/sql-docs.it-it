---
title: Finestra di dialogo Accesso a Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- sql13.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
caps.latest.revision: 31
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: db595388a1970fa37cf19dca00a58b4c4f2704ed
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Finestra di dialogo Accesso a Reporting Services (SSRS)
  Utilizzare la finestra di dialogo **Accesso a Reporting Services** per specificare le credenziali per la pubblicazione di report nel server di report.  
  
-   **Nota** La prima volta che si pubblica un report in un server di report dopo aver impostato la proprietà di distribuzione **TargetServerURL** per un progetto, verificare che il nome del server includa **server** e non **report**. Ad esempio, `http://localhost/reportserver`e non `http://localhost/reports`. Se si specifica la directory `reports` nel server locale anziché la directory `reportserver` , verrà visualizzata questa finestra di dialogo. Per altre informazioni sull'impostazione **TargetServerURL**, vedere [Impostare le proprietà di distribuzione &#40;Reporting Services&#41;](../../reporting-services/tools/set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Opzioni  
 **Server**  
 Indica il nome del server di report. Ad esempio, `http://localhost/reportserver`. Per i server di report che utilizzano una porta diversa da quella predefinita, ovvero 80, includere il numero di porta. Ad esempio, `http://localhost:81/reportserver`.  
  
 **User name**  
 Consente di digitare il nome utente da utilizzare per l'accesso al servizio Web.  
  
 **Password**  
 Consente di digitare la password da utilizzare per l'accesso al servizio Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Connessioni dati, origini dati e stringhe di connessione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Guida sensibile al contesto di Progettazione report](../../reporting-services/tools/report-designer-f1-help.md)  
  
  
