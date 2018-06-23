---
title: Finestra di dialogo Accesso a Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
caps.latest.revision: 29
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: e4a3feeca737e1d4db6627af5ece9fa9d36c6b7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156196"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Finestra di dialogo Accesso a Reporting Services (SSRS)
  Utilizzare la finestra di dialogo **Accesso a Reporting Services** per specificare le credenziali per la pubblicazione di report nel server di report.  
  
-   **Nota** se questa è la prima volta che si pubblica un report in un server di report dal set di impostare la proprietà di distribuzione **TargetServerURL** per un progetto, verificare che il nome del server specificato sia simile a `http://localhost/reportserver`e non `http://localhost/reports`. Se si specifica la directory `reports` nel server locale anziché la directory `reportserver` , verrà visualizzata questa finestra di dialogo. Per altre informazioni sull'impostazione **TargetServerURL**, vedere [Impostare le proprietà di distribuzione &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Opzioni  
 **Server**  
 Indica il nome del server di report. Ad esempio, `http://localhost/reportserver`. Per i server di report che utilizzano una porta diversa da quella predefinita, ovvero 80, includere il numero di porta. Ad esempio, `http://localhost:81/reportserver`.  
  
 **Nome utente**  
 Consente di digitare il nome utente da utilizzare per l'accesso al servizio Web.  
  
 **Password**  
 Consente di digitare la password da utilizzare per l'accesso al servizio Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Connessioni dati, origini dati e stringhe di connessione in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Specificare le credenziali e informazioni di connessione per origini dati del Report](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [della Guida F1 della finestra di progettazione del Report](report-designer-f1-help.md)  
  
  