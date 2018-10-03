---
title: Attivare le funzionalità di integrazione Power View in SharePoint e il Server di Report | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1ab486390e8da36d14d5aac1e1049a5836dd2be9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081828"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Attivare le funzionalità di integrazione per Power View e server di report in SharePoint
  Le funzionalità delle raccolte siti di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sono in genere attivate per impostazione predefinita dopo l'installazione del componente aggiuntivo [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] per prodotti SharePoint. In alcune situazioni sarà necessario attivare manualmente le funzionalità.  
  
 Se si installa il componente aggiuntivo di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per Prodotti SharePoint 2010 dopo l'installazione del prodotto SharePoint, la funzionalità di integrazione del server di report e la funzionalità di integrazione di Power View saranno attivate solo per le raccolte siti radice. Per le altre raccolte siti, sarà necessario attivare manualmente le funzionalità. Ad esempio se si dispone di una raccolta siti **http://[my il nome server] /sites/ [nome raccolta siti]** sarà necessario attivare manualmente il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] caratteristiche raccolta siti.  
  
 Quando non vi è alcuna raccolta siti radice, il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aggiuntivo registrerà un messaggio simile al seguente.  
  
 "L'applicazione Web SharePoint 80 non dispone della raccolta siti radice"  
  
 Il messaggio sarà registrato nel log dell'installazione del componente aggiuntivo, denominato "RS_SP_#.log" dove # è un numero incrementale. Il file di log si trova nella cartella Temp dell'utente corrente, ad esempio C:\Utenti\\[nome utente]\AppData\Local\Temp. Per altre informazioni sulle opzioni di registrazione con il componente aggiuntivo, vedere [installare o disinstallare il componente aggiuntivo di Reporting Services per SharePoint &#40;SharePoint 2010 e SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 Contenuto dell'argomento:  
  
-   [Per attivare le funzionalità di raccolta siti di integrazione per Power View e server di report](#bkmk_features)  
  
-   [Per attivare o disattivare la funzionalità Raccolta siti di amministrazione centrale di Reporting Services:](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a> Per attivare le funzionalità di raccolta siti di integrazione per Power View e server di report  
  
1.  Aprire il browser al sito dove si desidera che le funzionalità [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] siano attive.  
  
2.  Fare clic su **Azioni sito**.  
  
3.  Fare clic su **Impostazioni sito**.  
  
4.  Fare clic su **Funzionalità raccolta siti** nel gruppo Amministrazione raccolta siti  
  
5.  Individuare **Funzionalità di integrazione Server report** o **Funzionalità di integrazione Power View** nell'elenco.  
  
6.  Fare clic su **Attiva**.  
  
 Per disattivare le funzionalità, è possibile utilizzare la stessa procedura facendo clic su **Disattiva** anziché su **Attiva**.  
  
##  <a name="bkmk_centraladmin"></a> Per attivare o disattivare la funzionalità Raccolta siti di amministrazione centrale di Reporting Services:  
  
1.  Aprire il browser alla pagina Amministrazione centrale SharePoint.  
  
2.  Fare clic su **Azioni sito**.  
  
3.  Fare clic su **Impostazioni sito**.  
  
4.  Fare clic su **Funzionalità raccolta siti** nel gruppo Amministrazione raccolta siti  
  
5.  Individuare **Funzionalità Amministrazione centrale del server di report** nell'elenco.  
  
6.  Fare clic su **Attiva**.  
  
 Per disattivare la funzionalità, è possibile utilizzare la stessa procedura facendo tuttavia clic su **Disattiva** anziché su **Attiva.**  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo aver attivato la funzionalità, è possibile continuare con l'integrazione del server.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare o disinstallare il Reporting aggiuntivo Services per SharePoint &#40;SharePoint 2010 e SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
